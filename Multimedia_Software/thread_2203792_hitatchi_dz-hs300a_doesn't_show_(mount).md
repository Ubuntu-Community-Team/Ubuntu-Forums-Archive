---
title: "hitatchi dz-hs300a doesn't show (mount)"
date: 2014-02-05
forum: Multimedia Software
---

### Post by peter-olderon on 2014-02-05
Good day everyone,

Recently I received a camcorder that has its own HDD as well as the ability to record on DVDs. I connected it via USB to see if I could edit some test footage but Ubuntu doesn't seem to be mounting it as a drive at all. However, it looks like it is being recognized, please refer to information below:

**With dmesg**


[ 3494.638749] usb 2-1.1: Product: Hitachi DVDCAM USB HS Interface
[ 3494.638754] usb 2-1.1: Manufacturer: Hitachi, Ltd.
[ 3494.638759] usb 2-1.1: SerialNumber: 6659230245102414
[ 3494.639662] usb-storage 2-1.1:1.0: USB Mass Storage device detected
[ 3494.640171] scsi15 : usb-storage 2-1.1:1.0
[ 3495.642244] scsi 15:0:0:0: CD-ROM            HITACHI  DZ-USBHDD        0100 PQ: 0 ANSI: 0
[ 3495.644494] sr0: scsi3-mmc drive: 15x/15x dvd-ram tray
[ 3495.645458] sr 15:0:0:0: Attached scsi CD-ROM sr0
[ 3495.645675] sr 15:0:0:0: Attached scsi generic sg1 type 5
peter@PeroPeroPC:~$ 


**With lsusb**


Bus 002 Device 004: ID 8086:0189 Intel Corp. 
Bus 002 Device 007: ID 04a4:0043 Hitachi, Ltd 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 2232:1008  
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

What can I do to fix my situation here? Thank you for anyone who might help me.

**Update: **It seems my camcorder is detected as a CD/DVD Drive rather than a hard drive. Please refer to the picture below:

[IMG]http://i807.photobucket.com/albums/yy360/PeterLO4FP/Screenshotfrom2014-02-05083446_zps730645a6.png[/IMG]

---

