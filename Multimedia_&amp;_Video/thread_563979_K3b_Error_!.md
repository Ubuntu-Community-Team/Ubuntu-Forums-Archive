---
title: "K3b Error !"
date: 2007-09-30
forum: Multimedia &amp; Video
---

### Post by bigbrovar on 2007-09-30
When ever i try to run K3b in gnome it takes about 2 minute for the application to be up and running...when i tried lunching through terminal i got this  


[PHP]bigbrovar@bigbrovar-laptop:~$ k3b
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kdecore (KAction): WARNING: KActionCollection::KActionCollection( QObject *parent, const char *name, KInstance *instance )
(K3bDevice::HalConnection) initializing HAL >= 0.5
Mapping udi /org/freedesktop/Hal/devices/storage_model_DVD_RW_AD_7530A to device /dev/scd0
/dev/scd0 resolved to /dev/scd0
/dev/scd0 is block device (0)
/dev/scd0 seems to be cdrom
bus: 0, id: 0, lun: 0
(K3bDevice::Device) /dev/scd0: init()
(K3bDevice::Device) /dev/scd0 feature: CD Mastering
(K3bDevice::Device) /dev/scd0 feature: CD Track At Once
(K3bDevice::Device) /dev/scd0 feature: DVD Read (MMC5)
(K3bDevice::Device) /dev/scd0 feature: DVD+R
(K3bDevice::Device) /dev/scd0 feature: DVD+RW
(K3bDevice::Device) /dev/scd0 feature: DVD+R Double Layer
(K3bDevice::Device) /dev/scd0 feature: DVD-R/-RW Write
(K3bDevice::Device) /dev/scd0 feature: Rigid Restricted Overwrite
(K3bDevice::Device) /dev/scd0 feature: Layer Jump Recording
(K3bDevice::Device) /dev/scd0 unknown profile: 2
(K3bDevice::Device) /dev/scd0: dataLen: 60
(K3bDevice::Device) /dev/scd0: checking for TAO
(K3bDevice::Device) /dev/scd0: checking for SAO
(K3bDevice::Device) /dev/scd0: checking for SAO_R96P
(K3bDevice::Device) /dev/scd0: checking for SAO_R96R
(K3bDevice::Device) /dev/scd0: checking for RAW_R16
(K3bDevice::Device) /dev/scd0: checking for RAW_R96P
(K3bDevice::Device) /dev/scd0: checking for RAW_R96R
(K3bDevice::ScsiCommand) failed: 
                           command:    GET PERFORMANCE (ac)
                           errorcode:  72
                           sense key:  NO SENSE (2)
                           asc:        0
                           ascq:       3
(K3bDevice::Device) /dev/scd0: GET PERFORMANCE length det failed.
(K3bDevice::Device) /dev/scd0:  Number of supported write speeds via 2A: 4
(K3bDevice::Device) /dev/scd0 : 4234 KB/s
(K3bDevice::Device) /dev/scd0 : 3528 KB/s
(K3bDevice::Device) /dev/scd0 : 2823 KB/s
(K3bDevice::Device) /dev/scd0 : 1764 KB/s
(K3bDevice::DeviceManager) setting current write speed of device /dev/scd0 to 3324
/dev/scd0 resolved to /dev/scd0
(K3bDevice::DeviceManager) dev /dev/scd0 already found
(K3bDevice::DeviceManager) found config entry for devicetype: Optiarc DVD RW AD-7530A
Devices:
------------------------------
Blockdevice:    /dev/scd0
Generic device: 
Vendor:         Optiarc
Description:    DVD RW AD-7530A
Version:        EX32
Write speed:    4234
Profiles:       DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW
Read Cap:       DVD-ROM, DVD-R, DVD-R Sequential, DVD-R Dual Layer, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RW, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+RW Dual Layer, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW
Write Cap:      DVD-R, DVD-R Sequential, DVD-R Dual Layer, DVD-R Dual Layer Jump, DVD-RW, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-R, CD-RW
Writing modes:  SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump
Reader aliases: /dev/scd0
------------------------------
kdecore (KAction): WARNING: KActionCollection::operator+=(): function is severely deprecated.
[/PHP]


please is there anything i can do to correct this problem although i have gnome barker and basero i prefer k3b and would like it to function seamlessly on my system

my basic hardware config is
 Gateway MT6821 laptop,160gb hard drive (dual booting with vista) 2 gb ram,intel core 2 duo, dvd / cd writer DL .. 
thanks in advance

---

