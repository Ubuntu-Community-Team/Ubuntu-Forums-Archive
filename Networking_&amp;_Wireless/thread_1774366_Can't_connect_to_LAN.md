---
title: "Can't connect to LAN"
date: 2011-06-03
forum: Networking &amp; Wireless
---

### Post by Lloydb39 on 2011-06-03
Finally got Xubuntu 10.10 up and running on my ancient Dell Inspiron 1150 from the hard drive. Only problem is getting onto my LAN. Working fine in little old Puppy Linux but the larger version can't get on. It recognizes the LAN and will connect with Ethernet but not wireless. I've tried various connection programs from the software center but none seem to work. AT&T tech support no help as usual. Anyone know a good connection program or a tip about something I'm not doing? Thanks.

---

### Post by Toz on 2011-06-03
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

Let's start with the following. Open a terminal window (Accessories->Terminal Emulator), type in the following commands and post back the results.

```
nm-tool
sudo lshw -C network
lspci
lsmod
rfkill list
iwconfig
```

---

### Post by kaine007 on 2011-08-12
kofi@kofi-MM061:~$ sudo apt-get install ndisgtk
[sudo] password for kofi: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ndisgtk is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
kofi@kofi-MM061:~$ sudo dpkg -i ndiswrapper-common_*.deb
dpkg: error processing ndiswrapper-common_*.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ndiswrapper-common_*.deb
kofi@kofi-MM061:~$ sudo dpkg -i ndiswrapper-utils-*.deb
dpkg: error processing ndiswrapper-utils-*.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ndiswrapper-utils-*.deb
kofi@kofi-MM061:~$ sudo dpkg -i ndisgtk_*.deb
dpkg: error processing ndisgtk_*.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ndisgtk_*.deb
kofi@kofi-MM061:~$ clear

kofi@kofi-MM061:~$ echo -e "blacklist bcm43xx\nblacklist b43\nblacklist b43legacy\nblacklist ssb" | sudo tee -a /etc/modprobe.d/blacklist
blacklist bcm43xx
blacklist b43
blacklist b43legacy
blacklist ssb
kofi@kofi-MM061:~$ sudo lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X1400
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
0b:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
kofi@kofi-MM061:~$  ndiswrapper -l
kofi@kofi-MM061:~$ installed ndis drivers
installed: command not found
kofi@kofi-MM061:~$ clear

kofi@kofi-MM061:~$ sudo depmod -a
sudo modprobe ndiskofi@kofi-MM061:~$ sudo modprobe ndiswrapper
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
kofi@kofi-MM061:~$ tail /var/log/messages
tail: cannot open `/var/log/messages' for reading: No such file or directory
kofi@kofi-MM061:~$ ip addr
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 1000
    link/ether 00:19:b9:56:18:f9 brd ff:ff:ff:ff:ff:ff
    inet 192.168.254.12/24 brd 192.168.254.255 scope global eth0
    inet6 fe80::219:b9ff:fe56:18f9/64 scope link 
       valid_lft forever preferred_lft forever
kofi@kofi-MM061:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

kofi@kofi-MM061:~$ sudo lshw -C network
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:16 memory:efcfc000-efcfffff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:19:b9:56:18:f9
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.254.12 latency=64 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:17 memory:ef9fe000-ef9fffff
kofi@kofi-MM061:~$ sudo /usr/share/b43-fwcutter/install_bcm43xx_firmware.sh
sudo: /usr/share/b43-fwcutter/install_bcm43xx_firmware.sh: command not found
kofi@kofi-MM061:~$ sudo apt-get install b43-fwcutter
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  b43-fwcutter
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 14.6 kB of archives.
After this operation, 81.9 kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty/main b43-fwcutter i386 1:013-3 [14.6 kB]
Fetched 14.6 kB in 0s (17.8 kB/s)     
Selecting previously deselected package b43-fwcutter.
(Reading database ... 157906 files and directories currently installed.)
Unpacking b43-fwcutter (from .../b43-fwcutter_1%3a013-3_i386.deb) ...
Processing triggers for man-db ...
Setting up b43-fwcutter (1:013-3) ...
kofi@kofi-MM061:~$ emerge b43-fwcutter
No command 'emerge' found, did you mean:
 Command 'merge' from package 'rcs' (universe)
 Command 'fmerge' from package 'fhist' (universe)
 Command 'vemerge' from package 'util-vserver' (universe)
 Command 'esmerge' from package 'tstools' (universe)
emerge: command not found
kofi@kofi-MM061:~$ merge b43-fwcutter
The program 'merge' is currently not installed.  You can install it by typing:
sudo apt-get install rcs
kofi@kofi-MM061:~$ sudo apt-get install rcs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  rcs
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 365 kB of archives.
After this operation, 770 kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty/universe rcs i386 5.7-25 [365 kB]
Fetched 365 kB in 1s (191 kB/s)
Selecting previously deselected package rcs.
(Reading database ... 157913 files and directories currently installed.)
Unpacking rcs (from .../archives/rcs_5.7-25_i386.deb) ...
Processing triggers for man-db ...
Setting up rcs (5.7-25) ...
kofi@kofi-MM061:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

kofi@kofi-MM061:~$ clear

kofi@kofi-MM061:~$ nm -tool
nm: 'a.out': No such file
kofi@kofi-MM061:~$ nm
nm: 'a.out': No such file
kofi@kofi-MM061:~$ sudo lshw -C network
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:16 memory:efcfc000-efcfffff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:19:b9:56:18:f9
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.254.12 latency=64 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:17 memory:ef9fe000-ef9fffff
kofi@kofi-MM061:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X1400
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
0b:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
kofi@kofi-MM061:~$ rfkill list
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
kofi@kofi-MM061:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

---

