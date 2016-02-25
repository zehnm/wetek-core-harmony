# wetek-core-harmony
Wetek Core configuration files for Logitech Harmony 880 remote (and likely newer models)

## Short How-To
### Logitech Harmony Setup
* Select existing Logitech remote profile for device: **Wetek Play**
* Learn Power On IR code from Core Remote
* Map physical buttons and rename screen labels at your liking
(see [remote.conf](https://github.com/zehnm/wetek-core-harmony/blob/master/remote.conf) for possible options)

### Core Setup
1. Copy the .conf and .kl files to the Core's Download folder (/storage/sdcard0/Download)
  * remote.conf contains all the magic
  * Vendor_0001_Product_0001.kl fixes the Page Up / Down key mappings and adds the Star/Camera button
2. Telnet to Core and make system partition writeable:

        telnet WetekCore.local
        mount -o remount,rw /system

3. Backup original configuration

        cp /system/etc/remote.conf /system/etc/remote.conf.org
        cp /system/usr/keylayout/Vendor_0001_Product_0001.kl /system/usr/keylayout/Vendor_0001_Product_0001.kl.org

4. Set new configuration:

        cp /storage/sdcard0/Download/remote.conf /system/etc/remote.conf
        cp /storage/sdcard0/Download/Vendor_0001_Product_0001.kl /system/usr/keylayout/Vendor_0001_Product_0001.kl
	
5. Revert system partition to read only:

        mount -o remount,ro /system
	
6. Reboot Core

## Notes
* This procedure does not survive OTA updates and must be reapplied after the OS update 
* Not yet tested with Wetek OS > 1.0.1
* Back and Select keys don't seem to work with Wetek OS 1.1.1