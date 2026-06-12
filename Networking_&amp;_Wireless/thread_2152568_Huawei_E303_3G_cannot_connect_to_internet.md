---
title: "Huawei E303 3G cannot connect to internet"
date: 2013-06-08
forum: Networking &amp; Wireless
---

### Post by open-nandra on 2013-06-08
Hi,

before posting this thread I read whole internet of manuals how to make it working but none works for me. I'm new to 3G things so want to ask here directly ;).
I'm owner of Huawei E303 3G modem (using Ubuntu 13.04 with latest updates):
lsusb gives:
```
Bus 002 Device 014: ID 12d1:1506 Huawei Technologies Co., Ltd. E398 LTE/UMTS/GSM Modem/Networkcard
```

seems usb_modeswitch happens because I can see in log:
```
[ 4086.176062] usb 2-3: new high-speed USB device number 13 using ehci-pci
[ 4086.308979] usb 2-3: New USB device found, idVendor=12d1, idProduct=14fe
[ 4086.308987] usb 2-3: New USB device strings: Mfr=2, Product=1, SerialNumber=0
[ 4086.308992] usb 2-3: Product: HUAWEI Mobile
[ 4086.308997] usb 2-3: Manufacturer: HUAWEI
[ 4086.310815] scsi22 : usb-storage 2-3:1.0
[ 4086.311116] scsi23 : usb-storage 2-3:1.1
[ 4087.309266] scsi 22:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
[ 4087.309274] scsi 23:0:0:0: Direct-Access     HUAWEI   SD Storage       2.31 PQ: 0 ANSI: 2
[ 4087.314633] sr1: scsi-1 drive
[ 4087.314860] sr 22:0:0:0: Attached scsi CD-ROM sr1
[ 4087.315009] sr 22:0:0:0: Attached scsi generic sg2 type 5
[ 4087.315380] sd 23:0:0:0: Attached scsi generic sg3 type 0
[ 4087.318774] sd 23:0:0:0: [sdb] Attached SCSI removable disk
[ 4087.636125] ISO 9660 Extensions: Microsoft Joliet Level 1
[ 4087.636883] ISOFS: changing to secondary root
[ 4087.755565] usb 2-3: USB disconnect, device number 13
[ 4093.256061] usb 2-3: new high-speed USB device number 14 using ehci-pci
[ 4093.389484] usb 2-3: New USB device found, idVendor=12d1, idProduct=1506
[ 4093.389492] usb 2-3: New USB device strings: Mfr=3, Product=2, SerialNumber=0
[ 4093.389497] usb 2-3: Product: HUAWEI Mobile
[ 4093.389502] usb 2-3: Manufacturer: HUAWEI
[ 4093.391182] option 2-3:1.0: GSM modem (1-port) converter detected
[ 4093.391350] usb 2-3: GSM modem (1-port) converter now attached to ttyUSB0
[ 4093.393478] usb 2-3: MAC-Address: 58:2c:80:13:92:63
[ 4093.393823] cdc_ncm 2-3:1.1 wwan0: register 'cdc_ncm' at usb-0000:00:1d.7-3, Mobile Broadband Network Device, 58:2c:80:13:92:63
[ 4093.393914] option 2-3:1.2: GSM modem (1-port) converter detected
[ 4093.394645] usb 2-3: GSM modem (1-port) converter now attached to ttyUSB1
[ 4093.394777] option 2-3:1.3: GSM modem (1-port) converter detected
[ 4093.395008] usb 2-3: GSM modem (1-port) converter now attached to ttyUSB2
[ 4093.395354] scsi24 : usb-storage 2-3:1.4
[ 4093.395682] scsi25 : usb-storage 2-3:1.5
[ 4094.392915] scsi 24:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
[ 4094.392919] scsi 25:0:0:0: Direct-Access     HUAWEI   SD Storage       2.31 PQ: 0 ANSI: 2
[ 4094.398638] sr1: scsi-1 drive
[ 4094.398871] sr 24:0:0:0: Attached scsi CD-ROM sr1
[ 4094.399021] sr 24:0:0:0: Attached scsi generic sg2 type 5
[ 4094.399375] sd 25:0:0:0: Attached scsi generic sg3 type 0
[ 4094.402429] sd 25:0:0:0: [sdb] Attached SCSI removable disk
[ 4094.601406] ISO 9660 Extensions: Microsoft Joliet Level 1
[ 4094.602137] ISOFS: changing to secondary root



```

I can see correct connection name when issue nm-connection-editor:
[ATTACH=CONFIG]243648[/ATTACH]

but any Mobile Broadband appear in NetworkSettings. I try to use gnome-ppp but it gives me error about unknown commands.
Any ideas what to check or how to proceed?

Thanks,

marek

---

