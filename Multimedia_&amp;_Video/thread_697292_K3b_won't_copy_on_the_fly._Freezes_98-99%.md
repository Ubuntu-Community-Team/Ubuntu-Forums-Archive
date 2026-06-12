---
title: "K3b won't copy on the fly. Freezes 98-99%"
date: 2008-02-15
forum: Multimedia &amp; Video
---

### Post by The Avatar of Time on 2008-02-15
Well the title says it all. I am using Gutsy 64. I try to copy a disc on the fly and k3b will hit 98 or 99% and freeze. Any ideas? Brasero will copy on the fly just fine.

---

### Post by gsmanners on 2008-02-15
Are you using the 1.0.3 or the 1.0.4 (in backports)? Also, is this a CD or DVD disc?

---

### Post by The Avatar of Time on 2008-02-15
Hello, thanks for the reply. I have k3b version 1.0.4 from the repositories (is that the same as backports?). And sorry for not being more clear, I am trying to copy a dvd. I have tried copying a dvd movie, and also a dvd full of .avi's. Same result either way. However I can burn a cd just fine. And I think I can copy (cd or dvd) so long as it's not on the fly.

---

### Post by gsmanners on 2008-02-15
You might try reverting to 1.0.3, as I recall that one seemed to work okay. I haven't tried on the fly burning lately, so I can't be sure whether it isn't a hardware or software conflict on your end.

---

### Post by The Avatar of Time on 2008-02-18
Sorry to take so long. I got k3b 1.0.3 and it freezes at 99% also. However I noticed on both versions that after it freezes the second dvd (the blank one) light is still blinking. I waited about 5 minutes and it was still doing it so I killed k3b. I decided to play the disc and it works. I don't think it worked on 1.0.4, but I could be wrong. I was sure that I actually tried to play a few of them. Anyhow as I say the disc works, but why is it still freezing? And how does the disc work if k3b is at 99% when it freezes? Here is what I get from terminal if I copy on the fly. Also I just tried another disc and after killing k3b the light is still blinking and won't open.

```
william@Imladris:~$ k3b
kdecore (KAction): WARNING: KActionCollection::KActionCollection( QObject *parent, const char *name, KInstance *instance )
william@Imladris:~$ (K3bDevice::HalConnection) initializing HAL >= 0.5
(K3bDevice::HalConnection) Failed to init HAL context!
(K3bDevice::HalConnection) failed to open connection to HAL.
(K3bDevice::HalConnection) initializing HAL >= 0.5
(K3bDevice::HalConnection) Failed to init HAL context!
(K3bDevice::HalConnection) failed to open connection to HAL.
(K3bDevice::HalConnection) initializing HAL >= 0.5
(K3bDevice::HalConnection) Failed to init HAL context!
(K3bDevice::HalConnection) failed to open connection to HAL.
/dev/sr1 resolved to /dev/scd1
/dev/scd1 is block device (1)
/dev/scd1 seems to be cdrom
bus: 2, id: 0, lun: 0
(K3bDevice::Device) /dev/scd1: init()
(K3bDevice::Device) /dev/scd1 feature: CD Mastering
(K3bDevice::Device) /dev/scd1 feature: CD Track At Once
(K3bDevice::Device) /dev/scd1 feature: DVD Read (MMC5)
(K3bDevice::Device) /dev/scd1 feature: DVD+R
(K3bDevice::Device) /dev/scd1 feature: DVD+RW
(K3bDevice::Device) /dev/scd1 feature: DVD+R Double Layer
(K3bDevice::Device) /dev/scd1 feature: DVD-R/-RW Write
(K3bDevice::Device) /dev/scd1 feature: Rigid Restricted Overwrite
(K3bDevice::Device) /dev/scd1 feature: Layer Jump Recording
(K3bDevice::Device) /dev/scd1 unknown profile: 2
(K3bDevice::Device) /dev/scd1: dataLen: 60
(K3bDevice::Device) /dev/scd1: checking for TAO
(K3bDevice::Device) /dev/scd1: checking for SAO
(K3bDevice::Device) /dev/scd1: checking for SAO_R96P
(K3bDevice::Device) /dev/scd1: checking for SAO_R96R
(K3bDevice::Device) /dev/scd1: checking for RAW_R16
(K3bDevice::Device) /dev/scd1: checking for RAW_R96P
(K3bDevice::Device) /dev/scd1: checking for RAW_R96R
(K3bDevice::Device) /dev/scd1: GET PERFORMANCE dataLen = 40
(K3bDevice::Device) /dev/scd1: GET PERFORMANCE successful with reported length: 36
(K3bDevice::Device) /dev/scd1:  Number of supported write speeds via GET PERFORMANCE: 2
(K3bDevice::Device) /dev/scd1 : 11080 KB/s
(K3bDevice::Device) /dev/scd1 : 5540 KB/s
(K3bDevice::DeviceManager) setting current write speed of device /dev/scd1 to 11080
/dev/scd1 resolved to /dev/scd1
(K3bDevice::DeviceManager) dev /dev/scd1 already found
/dev/sr0 resolved to /dev/scd0
/dev/scd0 is block device (0)
/dev/scd0 seems to be cdrom
bus: 1, id: 0, lun: 0
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
(K3bDevice::Device) /dev/scd0: GET PERFORMANCE dataLen = 40
(K3bDevice::Device) /dev/scd0: GET PERFORMANCE successful with reported length: 36
(K3bDevice::Device) /dev/scd0:  Number of supported write speeds via GET PERFORMANCE: 2
(K3bDevice::Device) /dev/scd0 : 11080 KB/s
(K3bDevice::Device) /dev/scd0 : 5540 KB/s
(K3bDevice::DeviceManager) setting current write speed of device /dev/scd0 to 11080
/dev/scd0 resolved to /dev/scd0
(K3bDevice::DeviceManager) dev /dev/scd0 already found
(K3bDevice::DeviceManager) SCANNING FOR GENERIC DEVICES.
(K3bDevice::Device) could not open device /dev/sg0 for reading
                    (Permission denied)
bus: 1, id: 0, lun: 0
bus: 2, id: 0, lun: 0
(K3bDevice::Device) could not open device /dev/sg3 for reading
                    (Permission denied)
(K3bDevice::Device) could not open device /dev/sg4 for reading
                    (Permission denied)
(K3bDevice::Device) could not open device /dev/sg5 for reading
                    (Permission denied)
(K3bDevice::Device) could not open device /dev/sg6 for reading
                    (Permission denied)
(K3bDevice::Device) could not open device /dev/sg7 for reading
                    (Permission denied)
(K3bDevice::Device) could not open device /dev/sg8 for reading
                    (Permission denied)
(K3bDevice::Device) could not open device /dev/sg9 for reading
                    (Permission denied)
(K3bDevice::Device) could not open device /dev/sg10 for reading
                    (Permission denied)
Could not resolve /dev/sg11
(K3bDevice::Device) could not open device /dev/sg11 for reading
                    (No such file or directory)
Could not resolve /dev/sg12
(K3bDevice::Device) could not open device /dev/sg12 for reading
                    (No such file or directory)
Could not resolve /dev/sg13
(K3bDevice::Device) could not open device /dev/sg13 for reading
                    (No such file or directory)
Could not resolve /dev/sg14
(K3bDevice::Device) could not open device /dev/sg14 for reading
                    (No such file or directory)
Could not resolve /dev/sg15
(K3bDevice::Device) could not open device /dev/sg15 for reading
                    (No such file or directory)
First sec data area: 43:41:33 (LBA 196608) (402653184
Last sec data area: 551:39:38 (LBA 2482463) (5084084224 Bytes)
Last sec layer 1: 00:00:00 (LBA 0) (0 Bytes)
Layer 1 length: 00:00:01 (LBA 1) (2048 Bytes)
Layer 2 length: 551:39:38 (LBA 2482463) (5084084224 Bytes)
First sec data area: 43:41:33 (LBA 196608) (402653184
Last sec data area: 00:00:00 (LBA 0) (0 Bytes)
Last sec layer 1: 00:00:00 (LBA 0) (0 Bytes)
Layer 1 length: 00:00:01 (LBA 1) (2048 Bytes)
Layer 2 length: 00:00:00 (LBA 0) (0 Bytes)
(K3bDevice::ScsiCommand) failed: 
                           command:    READ TRACK INFORMATION (52)
                           errorcode:  70
                           sense key:  ILLEGAL REQUEST (5)
                           asc:        24
                           ascq:       0
(K3bDevice::Device) /dev/scd0: READ TRACK INFORMATION length det failed.
DiskInfo:
Mediatype:       DVD-R Sequential
Current Profile: DVD-R Sequential
Disk state:      empty
Empty:           1
Rewritable:      0
Appendable:      0
Sessions:        0
Tracks:          0
Layers:          1
Capacity:        510:46:46 (LBA 2298496) (4707319808 Bytes)
Remaining size:  510:46:46 (LBA 2298496) (4707319808 Bytes)
Used Size:       00:00:00 (LBA 0) (0 Bytes)
(K3bDevice::ScsiCommand) failed: 
                           command:    READ TRACK INFORMATION (52)
                           errorcode:  70
                           sense key:  ILLEGAL REQUEST (5)
                           asc:        24
                           ascq:       0
(K3bDevice::Device) /dev/scd0: READ TRACK INFORMATION with real length 36 failed.
DiskInfo:
Mediatype:       DVD-R Sequential
Current Profile: DVD-R Sequential
Disk state:      complete
Empty:           0
Rewritable:      0
Appendable:      0
Sessions:        1
Tracks:          1
Layers:          1
Capacity:        507:58:06 (LBA 2285856) (4681433088 Bytes)
Remaining size:  00:00:00 (LBA 0) (0 Bytes)
Used Size:       507:58:06 (LBA 2285856) (4681433088 Bytes)
(K3bDevice::Device) /dev/scd1: GET PERFORMANCE dataLen = 40
(K3bDevice::Device) /dev/scd1: GET PERFORMANCE successful with reported length: 36
(K3bDevice::Device) /dev/scd1:  Number of supported write speeds via GET PERFORMANCE: 2
(K3bDevice::Device) /dev/scd1 : 11080 KB/s
(K3bDevice::Device) /dev/scd1 : 5540 KB/s
Devices:
------------------------------
Blockdevice:    /dev/scd1
Generic device: /dev/sg2
Vendor:         ASUS
Description:    DRW-1814BLT
Version:        1.13
Write speed:    11080
Profiles:       DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW
Read Cap:       DVD-ROM, DVD-R, DVD-R Sequential, DVD-R Dual Layer, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RW, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+RW Dual Layer, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW
Write Cap:      DVD-R, DVD-R Sequential, DVD-R Dual Layer, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RW, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-R, CD-RW
Writing modes:  SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump
Reader aliases: /dev/scd1
------------------------------
Blockdevice:    /dev/scd0
Generic device: /dev/sg1
Vendor:         ASUS
Description:    DRW-1814BLT
Version:        1.13
Write speed:    11080
Profiles:       DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW
Read Cap:       DVD-ROM, DVD-R, DVD-R Sequential, DVD-R Dual Layer, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RW, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+RW Dual Layer, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW
Write Cap:      DVD-R, DVD-R Sequential, DVD-R Dual Layer, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RW, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-R, CD-RW
Writing modes:  SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump
Reader aliases: /dev/scd0
------------------------------
kdecore (KAction): WARNING: KActionCollection::operator+=(): function is severely deprecated.
(K3bDevice::Device) /dev/scd0: GET PERFORMANCE dataLen = 40
(K3bDevice::Device) /dev/scd0: GET PERFORMANCE successful with reported length: 36
(K3bDevice::Device) /dev/scd0:  Number of supported write speeds via GET PERFORMANCE: 2
(K3bDevice::Device) /dev/scd0 : 11080 KB/s
(K3bDevice::Device) /dev/scd0 : 5540 KB/s
(K3bDevice::DeviceManager) request for empty device!
(K3bDevice::DeviceManager) request for empty device!
(K3bDevice::Device) /dev/scd0: GET CONFIGURATION length det failed.
(K3bDevice::Device) /dev/scd0: GET CONFIGURATION length det failed.
(K3bDevice::Device) /dev/scd0: GET CONFIGURATION length det failed.
(K3bDevice::Device) /dev/scd1: GET CONFIGURATION length det failed.
(K3bDevice::Device) /dev/scd1: GET CONFIGURATION length det failed.
First sec data area: 43:41:33 (LBA 196608) (402653184
Last sec data area: 551:39:38 (LBA 2482463) (5084084224 Bytes)
Last sec layer 1: 00:00:00 (LBA 0) (0 Bytes)
Layer 1 length: 00:00:01 (LBA 1) (2048 Bytes)
Layer 2 length: 551:39:38 (LBA 2482463) (5084084224 Bytes)
(K3bDevice::ScsiCommand) failed: 
                           command:    READ TRACK INFORMATION (52)
                           errorcode:  70
                           sense key:  ILLEGAL REQUEST (5)
                           asc:        24
                           ascq:       0
(K3bDevice::Device) /dev/scd0: READ TRACK INFORMATION length det failed.
(K3bDevice::ScsiCommand) failed: 
                           command:    READ TRACK INFORMATION (52)
                           errorcode:  70
                           sense key:  ILLEGAL REQUEST (5)
                           asc:        24
                           ascq:       0
(K3bDevice::Device) /dev/scd0: READ TRACK INFORMATION with real length 36 failed.
(K3bDevice::Device) /dev/scd1: GET PERFORMANCE dataLen = 40
(K3bDevice::Device) /dev/scd1: GET PERFORMANCE successful with reported length: 36
(K3bDevice::Device) /dev/scd1:  Number of supported write speeds via GET PERFORMANCE: 2
(K3bDevice::Device) /dev/scd1 : 11080 KB/s
(K3bDevice::Device) /dev/scd1 : 5540 KB/s
(K3bDevice::HalConnection) initializing HAL >= 0.5
(K3bDevice::HalConnection) Failed to init HAL context!
(K3bDevice::HalConnection) failed to open connection to HAL.
(K3bDevice::HalConnection) initializing HAL >= 0.5
(K3bDevice::HalConnection) Failed to init HAL context!
(K3bDevice::HalConnection) failed to open connection to HAL.
(K3bDevice::ScsiCommand) failed: 
                           command:    MODE SELECT (55)
                           errorcode:  70
                           sense key:  ILLEGAL REQUEST (5)
                           asc:        26
                           ascq:       0
(K3bDevice::ScsiCommand) failed: 
                           command:    READ (10) (28)
                           errorcode:  0
                           sense key:  NO SENSE (2)
                           asc:        0
                           ascq:       0
(K3bDevice::Device) /dev/scd0: READ 10 failed!
(K3bDevice::ScsiCommand) failed: 
                           command:    READ (10) (28)
                           errorcode:  0
                           sense key:  NO SENSE (2)
                           asc:        0
                           ascq:       0
(K3bDevice::Device) /dev/scd0: READ 10 failed!
(K3bDevice::ScsiCommand) failed: 
                           command:    READ (10) (28)
                           errorcode:  0
                           sense key:  NO SENSE (2)
                           asc:        0
                           ascq:       0
(K3bDevice::Device) /dev/scd0: READ 10 failed!
(K3bDevice::ScsiCommand) failed: 
                           command:    READ (10) (28)
                           errorcode:  0
                           sense key:  NO SENSE (2)
                           asc:        0
                           ascq:       0
(K3bDevice::Device) /dev/scd0: READ 10 failed!
(K3bDevice::ScsiCommand) failed: 
                           command:    READ (10) (28)
                           errorcode:  0
                           sense key:  NO SENSE (2)
                           asc:        0
                           ascq:       0
(K3bDevice::Device) /dev/scd0: READ 10 failed!
(K3bDevice::ScsiCommand) failed: 
                           command:    READ (10) (28)
                           errorcode:  0
                           sense key:  NO SENSE (2)
                           asc:        0
                           ascq:       0
(K3bDevice::Device) /dev/scd0: READ 10 failed!
(K3bDevice::ScsiCommand) failed: 
                           command:    READ (10) (28)
                           errorcode:  0
                           sense key:  NO SENSE (2)
                           asc:        0
                           ascq:       0
(K3bDevice::Device) /dev/scd0: READ 10 failed!
(K3bDevice::ScsiCommand) failed: 
                           command:    READ (10) (28)
                           errorcode:  0
                           sense key:  NO SENSE (2)
                           asc:        0
                           ascq:       0
(K3bDevice::Device) /dev/scd0: READ 10 failed!
(K3bDevice::ScsiCommand) failed: 
                           command:    READ (10) (28)
                           errorcode:  0
                           sense key:  NO SENSE (2)
                           asc:        0
                           ascq:       0
(K3bDevice::Device) /dev/scd0: READ 10 failed!
(K3bDevice::ScsiCommand) failed: 
                           command:    READ (10) (28)
                           errorcode:  0
                           sense key:  NO SENSE (2)
                           asc:        0
                           ascq:       0
(K3bDevice::Device) /dev/scd0: READ 10 failed!
(K3bDevice::ScsiCommand) failed: 
                           command:    READ (10) (28)
                           errorcode:  0
                           sense key:  NO SENSE (2)
                           asc:        0
                           ascq:       0
(K3bDevice::Device) /dev/scd0: READ 10 failed!
(K3bDevice::ScsiCommand) failed: 
                           command:    READ (10) (28)
                           errorcode:  0
                           sense key:  NO SENSE (2)
                           asc:        0
                           ascq:       0
(K3bDevice::Device) /dev/scd0: READ 10 failed!
(K3bDevice::ScsiCommand) failed: 
                           command:    READ (10) (28)
                           errorcode:  0
                           sense key:  NO SENSE (2)
                           asc:        0
                           ascq:       0
(K3bDevice::Device) /dev/scd0: READ 10 failed!
(K3bDevice::ScsiCommand) failed: 
                           command:    READ (10) (28)
                           errorcode:  0
                           sense key:  NO SENSE (2)
                           asc:        0
                           ascq:       0
(K3bDevice::Device) /dev/scd0: READ 10 failed!
(K3bDevice::ScsiCommand) failed: 
                           command:    READ (10) (28)
                           errorcode:  0
                           sense key:  NO SENSE (2)
                           asc:        0
                           ascq:       0
(K3bDevice::Device) /dev/scd0: READ 10 failed!
(K3bDevice::ScsiCommand) failed: 
                           command:    READ (10) (28)
                           errorcode:  0
                           sense key:  NO SENSE (2)
                           asc:        0
                           ascq:       0
(K3bDevice::Device) /dev/scd0: READ 10 failed!
(K3bDevice::ScsiCommand) failed: 
                           command:    READ (10) (28)
                           errorcode:  0
                           sense key:  NO SENSE (2)
                           asc:        0
                           ascq:       0
(K3bDevice::Device) /dev/scd0: READ 10 failed!
(K3bDevice::ScsiCommand) failed: 
                           command:    READ (10) (28)
                           errorcode:  0
                           sense key:  NO SENSE (2)
                           asc:        0
                           ascq:       0
(K3bDevice::Device) /dev/scd0: READ 10 failed!
(K3bDevice::ScsiCommand) failed: 
                           command:    READ (10) (28)
                           errorcode:  0
                           sense key:  NO SENSE (2)
                           asc:        0
                           ascq:       0
(K3bDevice::Device) /dev/scd0: READ 10 failed!
(K3bDevice::ScsiCommand) failed: 
                           command:    READ (10) (28)
                           errorcode:  0
                           sense key:  NO SENSE (2)
                           asc:        0
                           ascq:       0
(K3bDevice::Device) /dev/scd0: READ 10 failed!
(K3bDevice::ScsiCommand) failed: 
                           command:    READ (10) (28)
                           errorcode:  0
                           sense key:  NO SENSE (2)
                           asc:        0
                           ascq:       0
(K3bDevice::Device) /dev/scd0: READ 10 failed!
(K3bDevice::ScsiCommand) failed: 
                           command:    READ (10) (28)
                           errorcode:  0
                           sense key:  NO SENSE (2)
                           asc:        0
                           ascq:       0
(K3bDevice::Device) /dev/scd0: READ 10 failed!
(K3bDevice::ScsiCommand) failed: 
                           command:    READ (10) (28)
                           errorcode:  0
                           sense key:  NO SENSE (2)
                           asc:        0
                           ascq:       0
(K3bDevice::Device) /dev/scd0: READ 10 failed!
(K3bDevice::ScsiCommand) failed: 
                           command:    READ (10) (28)
                           errorcode:  0
                           sense key:  NO SENSE (2)
                           asc:        0
                           ascq:       0
(K3bDevice::Device) /dev/scd0: READ 10 failed!
(K3bDevice::ScsiCommand) failed: 
                           command:    READ (10) (28)
                           errorcode:  0
                           sense key:  NO SENSE (2)
                           asc:        0
                           ascq:       0
(K3bDevice::Device) /dev/scd0: READ 10 failed!
(K3bDevice::ScsiCommand) failed: 
                           command:    READ (10) (28)
                           errorcode:  0
                           sense key:  NO SENSE (2)
                           asc:        0
                           ascq:       0
(K3bDevice::Device) /dev/scd0: READ 10 failed!
(K3bDevice::ScsiCommand) failed: 
                           command:    READ (10) (28)
                           errorcode:  0
                           sense key:  NO SENSE (2)
                           asc:        0
                           ascq:       0
(K3bDevice::Device) /dev/scd0: READ 10 failed!
(K3bDevice::ScsiCommand) failed: 
                           command:    READ (10) (28)
                           errorcode:  0
                           sense key:  NO SENSE (2)
                           asc:        0
                           ascq:       0
(K3bDevice::Device) /dev/scd0: READ 10 failed!
(K3bDevice::ScsiCommand) failed: 
                           command:    READ (10) (28)
                           errorcode:  0
                           sense key:  NO SENSE (2)
                           asc:        0
                           ascq:       0
(K3bDevice::Device) /dev/scd0: READ 10 failed!
(K3bDevice::ScsiCommand) failed: 
                           command:    READ (10) (28)
                           errorcode:  0
                           sense key:  NO SENSE (2)
                           asc:        0
                           ascq:       0
(K3bDevice::Device) /dev/scd0: READ 10 failed!
(K3bDevice::ScsiCommand) failed: 
                           command:    READ (10) (28)
                           errorcode:  0
                           sense key:  NO SENSE (2)
                           asc:        0
                           ascq:       0
(K3bDevice::Device) /dev/scd0: READ 10 failed!
(K3bDevice::ScsiCommand) failed: 
                           command:    READ (10) (28)
                           errorcode:  0
                           sense key:  NO SENSE (2)
                           asc:        0
                           ascq:       0
(K3bDevice::Device) /dev/scd0: READ 10 failed!
(K3bDevice::ScsiCommand) failed: 
                           command:    READ (10) (28)
                           errorcode:  0
                           sense key:  NO SENSE (2)
                           asc:        0
                           ascq:       0
(K3bDevice::Device) /dev/scd0: READ 10 failed!
(K3bDevice::ScsiCommand) failed: 
                           command:    READ (10) (28)
                           errorcode:  0
                           sense key:  NO SENSE (2)
                           asc:        0
                           ascq:       0
(K3bDevice::Device) /dev/scd0: READ 10 failed!
(K3bDevice::ScsiCommand) failed: 
                           command:    READ (10) (28)
                           errorcode:  0
                           sense key:  NO SENSE (2)
                           asc:        0
                           ascq:       0
(K3bDevice::Device) /dev/scd0: READ 10 failed!
(K3bDevice::ScsiCommand) failed: 
                           command:    READ (10) (28)
                           errorcode:  0
                           sense key:  NO SENSE (2)
                           asc:        0
                           ascq:       0
(K3bDevice::Device) /dev/scd0: READ 10 failed!
(K3bDevice::ScsiCommand) failed: 
                           command:    READ (10) (28)
                           errorcode:  0
                           sense key:  NO SENSE (2)
                           asc:        0
                           ascq:       0
(K3bDevice::Device) /dev/scd0: READ 10 failed!
(K3bDevice::ScsiCommand) failed: 
                           command:    READ (10) (28)
                           errorcode:  0
                           sense key:  NO SENSE (2)
                           asc:        0
                           ascq:       0
(K3bDevice::Device) /dev/scd0: READ 10 failed!
(K3bDevice::ScsiCommand) failed: 
                           command:    READ (10) (28)
                           errorcode:  0
                           sense key:  NO SENSE (2)
                           asc:        0
                           ascq:       0
(K3bDevice::Device) /dev/scd0: READ 10 failed!
(K3bDevice::ScsiCommand) failed: 
                           command:    READ (10) (28)
                           errorcode:  0
                           sense key:  NO SENSE (2)
                           asc:        0
                           ascq:       0
(K3bDevice::Device) /dev/scd0: READ 10 failed!
(K3bDevice::ScsiCommand) failed: 
                           command:    READ (10) (28)
                           errorcode:  0
                           sense key:  NO SENSE (2)
                           asc:        0
                           ascq:       0
(K3bDevice::Device) /dev/scd0: READ 10 failed!
(K3bDevice::ScsiCommand) failed: 
                           command:    READ (10) (28)
                           errorcode:  0
                           sense key:  NO SENSE (2)
                           asc:        0
                           ascq:       0
(K3bDevice::Device) /dev/scd0: READ 10 failed!
(K3bDevice::ScsiCommand) failed: 
                           command:    READ (10) (28)
                           errorcode:  0
                           sense key:  NO SENSE (2)
                           asc:        0
                           ascq:       0
(K3bDevice::Device) /dev/scd0: READ 10 failed!
(K3bDevice::ScsiCommand) failed: 
                           command:    READ (10) (28)
                           errorcode:  0
                           sense key:  NO SENSE (2)
                           asc:        0
                           ascq:       0
(K3bDevice::Device) /dev/scd0: READ 10 failed!
(K3bDevice::ScsiCommand) failed: 
                           command:    READ (10) (28)
                           errorcode:  0
                           sense key:  NO SENSE (2)
                           asc:        0
                           ascq:       0
(K3bDevice::Device) /dev/scd0: READ 10 failed!
(K3bDevice::ScsiCommand) failed: 
                           command:    READ (10) (28)
                           errorcode:  0
                           sense key:  NO SENSE (2)
                           asc:        0
                           ascq:       0
(K3bDevice::Device) /dev/scd0: READ 10 failed!
(K3bDevice::ScsiCommand) failed: 
                           command:    READ (10) (28)
                           errorcode:  0
                           sense key:  NO SENSE (2)
                           asc:        0
                           ascq:       0
(K3bDevice::Device) /dev/scd0: READ 10 failed!
(K3bDevice::ScsiCommand) failed: 
                           command:    READ (10) (28)
                           errorcode:  0
                           sense key:  NO SENSE (2)
                           asc:        0
                           ascq:       0
(K3bDevice::Device) /dev/scd0: READ 10 failed!
(K3bDevice::ScsiCommand) failed: 
                           command:    READ (10) (28)
                           errorcode:  0
                           sense key:  NO SENSE (2)
                           asc:        0
                           ascq:       0
(K3bDevice::Device) /dev/scd0: READ 10 failed!
(K3bDevice::ScsiCommand) failed: 
                           command:    READ (10) (28)
                           errorcode:  0
                           sense key:  NO SENSE (2)
                           asc:        0
                           ascq:       0
(K3bDevice::Device) /dev/scd0: READ 10 failed!
(K3bDevice::ScsiCommand) failed: 
                           command:    READ (10) (28)
                           errorcode:  0
                           sense key:  NO SENSE (2)
                           asc:        0
                           ascq:       0
(K3bDevice::Device) /dev/scd0: READ 10 failed!
(K3bDevice::ScsiCommand) failed: 
                           command:    READ (10) (28)
                           errorcode:  0
                           sense key:  NO SENSE (2)
                           asc:        0
                           ascq:       0
(K3bDevice::Device) /dev/scd0: READ 10 failed!
(K3bDevice::ScsiCommand) failed: 
                           command:    READ (10) (28)
                           errorcode:  0
                           sense key:  NO SENSE (2)
                           asc:        0
                           ascq:       0
(K3bDevice::Device) /dev/scd0: READ 10 failed!
(K3bDevice::ScsiCommand) failed: 
                           command:    READ (10) (28)
                           errorcode:  0
                           sense key:  NO SENSE (2)
                           asc:        0
                           ascq:       0
(K3bDevice::Device) /dev/scd0: READ 10 failed!
(K3bDevice::ScsiCommand) failed: 
                           command:    READ (10) (28)
                           errorcode:  0
                           sense key:  NO SENSE (2)
                           asc:        0
                           ascq:       0
(K3bDevice::Device) /dev/scd0: READ 10 failed!
(K3bDevice::ScsiCommand) failed: 
                           command:    READ (10) (28)
                           errorcode:  0
                           sense key:  NO SENSE (2)
                           asc:        0
                           ascq:       0
(K3bDevice::Device) /dev/scd0: READ 10 failed!
(K3bDevice::ScsiCommand) failed: 
                           command:    READ (10) (28)
                           errorcode:  0
                           sense key:  NO SENSE (2)
                           asc:        0
                           ascq:       0
(K3bDevice::Device) /dev/scd0: READ 10 failed!
(K3bDevice::ScsiCommand) failed: 
                           command:    READ (10) (28)
                           errorcode:  0
                           sense key:  NO SENSE (2)
                           asc:        0
                           ascq:       0
(K3bDevice::Device) /dev/scd0: READ 10 failed!
(K3bDevice::ScsiCommand) failed: 
                           command:    READ (10) (28)
                           errorcode:  0
                           sense key:  NO SENSE (2)
                           asc:        0
                           ascq:       0
(K3bDevice::Device) /dev/scd0: READ 10 failed!
(K3bDevice::ScsiCommand) failed: 
                           command:    READ (10) (28)
                           errorcode:  0
                           sense key:  NO SENSE (2)
                           asc:        0
                           ascq:       0
(K3bDevice::Device) /dev/scd0: READ 10 failed!
(K3bDevice::ScsiCommand) failed: 
                           command:    READ (10) (28)
                           errorcode:  0
                           sense key:  NO SENSE (2)
                           asc:        0
                           ascq:       0
(K3bDevice::Device) /dev/scd0: READ 10 failed!
(K3bDevice::ScsiCommand) failed: 
                           command:    READ (10) (28)
                           errorcode:  0
                           sense key:  NO SENSE (2)
                           asc:        0
                           ascq:       0
(K3bDevice::Device) /dev/scd0: READ 10 failed!
(K3bDevice::ScsiCommand) failed: 
                           command:    READ (10) (28)
                           errorcode:  0
                           sense key:  NO SENSE (2)
                           asc:        0
                           ascq:       0
(K3bDevice::Device) /dev/scd0: READ 10 failed!
(K3bDevice::ScsiCommand) failed: 
                           command:    READ (10) (28)
                           errorcode:  0
                           sense key:  NO SENSE (2)
                           asc:        0
                           ascq:       0
(K3bDevice::Device) /dev/scd0: READ 10 failed!

```

---

### Post by The Avatar of Time on 2008-02-18
Okay also the disc I just tried to copy did not work. But the first one did, so I am lost.

---

