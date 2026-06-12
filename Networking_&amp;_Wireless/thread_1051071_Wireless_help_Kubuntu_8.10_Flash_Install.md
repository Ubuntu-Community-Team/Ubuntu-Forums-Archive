---
title: "Wireless help? Kubuntu 8.10 Flash Install"
date: 2009-01-26
forum: Networking &amp; Wireless
---

### Post by jrm19852007 on 2009-01-26
I recently installed Kubuntu 8.10 via 2g flash drive, but I have no idea how to get my sound and wireless drivers working. I was able to get these drivers working with Ubuntu 8.04 but I want to be able to keep my OS on the flash drive and everything working right.  If this can be done I would appreciate help with this issue. I dont have a working connection in Kubuntu so I would like to get it working manualy. In Ubuntu 8.04 installed on my primary hard drive I used the below tutorial to get my wireless working....

For those without a working internet connection

If you have a Hardy install CD,
Insert your CD and do the following:
Code:

sudo apt-cdrom add
sudo aptitude update
sudo aptitude install b43-fwcutter

Make sure that you say no or cancel when the installer asks you to find/download the firmware for you. It will get stuck because it is thinking that there is an internet connection.
Now skip down to the Downloading Firmware section.

If you don't have a Hardy install CD
You will have to find a place with a working internet connection. Go to this link:
[http://packages.ubuntu.com/hardy/utils/b43-fwcutter](http://packages.ubuntu.com/hardy/utils/b43-fwcutter)
Download the version that you need--amd64 for 64-bit and i386 for 32-bit. Copy the file to your home directory and do the following:
64-bit:
Code:

cd
sudo dpkg -i b43-fwcutter_011-1_amd64.deb

It is possible that the _011-1_ portion is another number.
Make sure that you say no or cancel when the installer asks you to find/download the firmware for you. It will get stuck because it is thinking that there is an internet connection.

32-bit:
Code:

cd
sudo dpkg -i b43-fwcutter_011-1_i386.deb

It is possible that the _011-1_ portion is another number.
Make sure that you say no or cancel when the installer asks you to find/download the firmware for you. It will get stuck because it is thinking that there is an internet connection.

Downloading Firmware
Both 32-bit and 64-bit:
You will still need to find someplace with a working internet connection and download the following files:
Code:

[http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o)
[http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2](http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2)

nautilus /home/yourusername Copy those files to your home directory. In the Terminal/Konsole/xterm window do the following:
Code:

cd
sudo b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o
tar xfvj broadcom-wl-4.80.53.0.tar.bz2
sudo b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.80.53.0/kmod/wl_apsta_mimo.o
sudo chmod o+rx /lib/firmware/b43 /lib/firmware/b43legacy
sudo ifconfig wlan0 up

For those of you who are configuring your /etc/network/interfaces, you might need to do:
Code:

sudo /etc/init.d/networking restart

That will restarting your network and will read through the /etc/networking/interfaces to connect.

HERE ARE MY PC SPECS.

Dell E1705
1 GB Ram
Intel Core Duo
Genuine Intel(R) CPU T2250 @1.73GHz
Genuine Intel(R) CPU T2250 @1.73GHz
Hitachi ATA Device 80GB
ATI Mobility Radeon X1400
Broadcom 440x10/100 Intergrated Controller
Broadcom 802.11g Network Adapter

00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port [8086:27a1] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 01)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 01)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 [8086:27d2] (rev 01)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 [8086:27d6] (rev 01)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 [8086:27c8] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 [8086:27c9] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 [8086:27ca] (rev 01)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 [8086:27cb] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e1)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 01)
00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller [8086:27c4] (rev 01)
00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 01)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon Mobility X1400 [1002:7145]
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
03:01.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832]
03:01.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 19)
03:01.2 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 0a)
03:01.3 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 05)
03:01.4 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev ff)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM94311MCG wlan mini-PCI [14e4:4311] (rev 01)

windows isnt a virus,
viruses are small and efficent.

---

### Post by Ayuthia on 2009-01-26
You should be able to use the Broadcom STA module without having to download anything.  The only trick is that you have a Broadcom wired ethernet card so you will have to remove the module for that card before loading the Broadcom STA card:
```
sudo modprobe -r b43 b44 ssb wl
sudo modprobe wl
sudo modprobe b44
sudo /etc/init.d/networking restart
```

---

### Post by jrm19852007 on 2009-01-26
Thanks for the help it worked. so easy.

---

