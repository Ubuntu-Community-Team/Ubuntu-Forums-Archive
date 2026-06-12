---
title: "Huawei E180/E220 Ubuntu 10.04 Server"
date: 2011-11-22
forum: Networking &amp; Wireless
---

### Post by virtuoosi on 2011-11-22
Hello,

After hours and hours of failed attempts I am asking for help regarding the Huawei E180 (or E220) 3g modem with Ubuntu Server 10.04. 

I will use this modem just to send SMS with the server with gammu or similar software. The only problem is: I can't get the server machine to recognize the Huawei stick correctly. When the modem is plugged into the USB port, it is recognized as a USB mass storage. That's a common problem which is SUPPOSED to be fixable. I tried and I tried fixing it with directions I found from Google, with no success. The modem is still shown as mass storage in dmesg.

Any help is appreciated! :confused:

Here is some info: 

dmesg
```

[11113295.845274] usb-storage: device found at 43
[11113295.845280] usb-storage: waiting for device to settle before scanning
[11113300.841003] usb-storage: device scan complete
[11113300.841979] scsi 103:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
[11113300.850257] usb-storage: device scan complete
[11113300.851610] scsi 104:0:0:0: Direct-Access     HUAWEI   SD Storage       2.31 PQ: 0 ANSI: 2
[11113300.852366] sr0: scsi-1 drive
[11113300.852612] sr 103:0:0:0: Attached scsi CD-ROM sr0
[11113300.852738] sr 103:0:0:0: Attached scsi generic sg2 type 5
[11113300.859698] sd 104:0:0:0: Attached scsi generic sg3 type 0
[11113300.900460] sd 104:0:0:0: [sdc] Attached SCSI removable disk

```lsusb
```
Bus 001 Device 043: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E230/E270/E870 HSDPA/HSUPA Modem
``````
2.6.32-32-generic-pae #62-Ubuntu SMP Wed Apr 20 22:10:33 UTC 2011 i686 GNU/Linux
```There is no /dev/ttyUSB* other than the ttyUSB0 which I created using mknod at some point when trying to make things work. If I rm the /dev/ttyUSB0 and re-plug the modem, no ttyUSB* entry is created. Is this a problem?

The modem works just fine on my Ubuntu 11.10 Desktop installation on my netbook.

I tried usb_modeswitch with no success. 

This is my usb-modeswitch.conf:
```
########################################################
# Huawei E220, E230, E270, E870

DefaultVendor= 0x12d1
DefaultProduct=0x1003

TargetClass=0xff

CheckSuccess=20

HuaweiMode=1
```Which yields the following output:
```
Looking for target devices ...
 Found devices in target mode or class (1)
Looking for default devices ...
 Found default devices (1)
 All devices in target class mode. Nothing to do. Bye.
```

---

### Post by virtuoosi on 2011-11-22
Solved!

I disabled the usb_storage kernel module by adding
```

blacklist usb_storage
```

to /etc/modprobe.d/blacklist.conf

and rebooted.

It is working, I can now send SMS from command line. :)

Sometimes writing the problem down gives the best answer. :KS

---

