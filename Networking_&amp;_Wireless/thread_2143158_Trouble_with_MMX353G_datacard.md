---
title: "Trouble with MMX353G datacard"
date: 2013-05-08
forum: Networking &amp; Wireless
---

### Post by gagansinghjarry on 2013-05-08
Hey guys, i'm having some trouble trying to get my Micromax 353G data card to work with ubuntu 13.04. It doesn't show up in the network manager, it is however detected as it's clearly listed in the output of lsub as 

```
sony@Sony-Vaio:~$ lsusb
Bus 001 Device 002: ID 05ca:18b5 Ricoh Co., Ltd Sony Vaio Integrated Webcam
[COLOR="#FF8C00"]Bus 002 Device 008: ID 1c9e:9605 OMEGA TECHNOLOGY [/COLOR]
Bus 008 Device 002: ID 044e:3017 Alps Electric Co., Ltd BCM2046 Bluetooth Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

Also I get an error from usb_modeswitch when I run dmesg, it says the highlighted line in the snippet below:

```
sony@Sony-Vaio:~$ dmesg
[15159.892105] usb 2-3: new high-speed USB device number 11 using ehci-pci
[15160.026968] usb 2-3: New USB device found, idVendor=1c9e, idProduct=f000
[15160.026976] usb 2-3: New USB device strings: Mfr=3, Product=2, SerialNumber=4
[15160.026981] usb 2-3: Product: USB Modem
[15160.026985] usb 2-3: Manufacturer: USB Modem
[15160.026989] usb 2-3: SerialNumber: 1234567890ABCDEF
[15160.029042] scsi12 : usb-storage 2-3:1.0
[15161.029514] scsi 12:0:0:0: CD-ROM            USBModem Disk             2.31 PQ: 0 ANSI: 2
[15161.033976] sr1: scsi-1 drive
[15161.034616] sr 12:0:0:0: Attached scsi CD-ROM sr1
[15161.035257] sr 12:0:0:0: Attached scsi generic sg2 type 5
[15163.383880] usb 2-3: USB disconnect, device number 11
[15163.752075] usb 2-3: new high-speed USB device number 12 using ehci-pci
[15163.887094] usb 2-3: New USB device found, idVendor=1c9e, idProduct=9605
[15163.887102] usb 2-3: New USB device strings: Mfr=3, Product=2, SerialNumber=4
[15163.887106] usb 2-3: Product: USB Modem
[15163.887111] usb 2-3: Manufacturer: USB Modem
[15163.887115] usb 2-3: SerialNumber: 1234567890ABCDEF
[15164.549703] scsi13 : usb-storage 2-3:1.4
[15165.549258] scsi 13:0:0:0: Direct-Access     USBModem Disk             2.31 PQ: 0 ANSI: 2
[15165.550202] sd 13:0:0:0: Attached scsi generic sg2 type 0
[15165.552218] sd 13:0:0:0: [sdb] Attached SCSI removable disk
[COLOR="#FF8C00"][15167.816227] usb_modeswitch_[22970]: segfault at 8 ip 00007feb9c324c51 sp 00007fff4c697a78 error 4 in libc-2.17.so[7feb9c29b000+1be000][/COLOR]

```

Can anyone help me fix this?
PS: I don't know if this matters but it used to work fine in 12.04.

Update: Nevermind i solved it, figured since the card worked in 12.04 I'll just downgrade the packages to their 12.04 counterparts. All I had to do was to go to packages.ubuntu.com and search for the package name in the 12.04 release and then I locked the version to stop it from upgrading.

---

