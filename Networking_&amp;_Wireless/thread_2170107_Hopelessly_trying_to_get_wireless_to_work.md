---
title: "Hopelessly trying to get wireless to work"
date: 2013-08-24
forum: Networking &amp; Wireless
---

### Post by adventuretime15 on 2013-08-24
Okay here's what's going down. I am currently at my dad's house with my freshly installed as of last week 13.04 ubuntu. My problem is that I do not know how to get the wifi working and I have to get it fixed tonight or else I will only be able to use linux every other weekend seeing as the only time I can get a wired connection is at my dad's house. (At home router is upstairs and too far away for a cable.) I do have ndiswrapper installed and wine and some other things but I don't think those are needed at the moment. Here's some info:
```

joe@joe-MS-7641:~$ lspci -nn
00:00.0 Host bridge [0600]: Advanced Micro Devices [AMD] RS780 Host Bridge [1022:9600]
00:02.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0) [1022:9603]
00:05.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 1) [1022:9605]
00:11.0 SATA controller [0106]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode] [1002:4390]
00:12.0 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
00:12.1 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0 USB OHCI1 Controller [1002:4398]
00:12.2 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
00:13.0 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
00:13.1 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0 USB OHCI1 Controller [1002:4398]
00:13.2 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
00:14.0 SMBus [0c05]: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller [1002:4385] (rev 3c)
00:14.1 IDE interface [0101]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 IDE Controller [1002:439c]
00:14.2 Audio device [0403]: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA) [1002:4383]
00:14.3 ISA bridge [0601]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller [1002:439d]
00:14.4 PCI bridge [0604]: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge [1002:4384]
00:14.5 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI2 Controller [1002:4399]
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] Family 15h Processor Function 0 [1022:1600]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] Family 15h Processor Function 1 [1022:1601]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] Family 15h Processor Function 2 [1022:1602]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] Family 15h Processor Function 3 [1022:1603]
00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] Family 15h Processor Function 4 [1022:1604]
00:18.5 Host bridge [0600]: Advanced Micro Devices [AMD] Family 15h Processor Function 5 [1022:1605]
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI Cape Verde XT [Radeon HD 7770 GHz Edition] [1002:683d]
01:00.1 Audio device [0403]: Advanced Micro Devices [AMD] nee ATI Cape Verde/Pitcairn HDMI Audio [Radeon HD 7700/7800 Series] [1002:aab0]
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
03:02.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8190 802.11n Wireless LAN [10ec:8190]

```

```

joe@joe-MS-7641:~$ sudo su
[sudo] password for joe: 
root@joe-MS-7641:/home/joe# lshw -c Network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168 PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 06
       serial: d4:3d:7e:55:2c:d4
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168e-3_0.0.4 03/27/12 ip=192.168.1.139 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:42 ioport:d800(size=256) memory:fdfff000-fdffffff memory:fdff8000-fdffbfff
  *-network UNCLAIMED
       description: Network controller
       product: RTL8190 802.11n Wireless LAN
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:03:02.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64 maxlatency=64 mingnt=32
       resources: ioport:e800(size=256) memory:febff000-febfffff

```

If you need any other information please don't hesitate to reply. I am hoping I don't have to straight up buy a different PCI card seeing as it works completely fine in my Windows 7 (I'm dual-booting.)

---

### Post by adventuretime15 on 2013-08-24
I'm going to move over to my Windows 7 for awhile, if I get any replies on what to do I will restart into Ubuntu. I'll be checking this thread regularly throughout the night.

---

### Post by chili555 on 2013-08-25
As far as I know, ndiswrapper is the only way to get this device working. Please see: [http://askubuntu.com/questions/53136/realtek-8190-wireless-doesnt-work](http://askubuntu.com/questions/53136/realtek-8190-wireless-doesnt-work) and also post #5 here: [http://ubuntuforums.org/showthread.php?t=1433401&p=9941361#post9941361](http://ubuntuforums.org/showthread.php?t=1433401&p=9941361#post9941361)

You will need the Windows ***XP*** inf and sys files matching your architecture; either 32- or 64-bit; find out with a terminal command:```
arch
```Do you have the files on your Windows partition? 

Frankly, there are easier devices to get going. Do you still have the receipt??

---

### Post by adventuretime15 on 2013-08-25
I have 64bit
```

joe@joe-MS-7641:~$ arch
x86_64

```

I don't have the files on my Windows partition but I'm back on linux so I'll go look for them. And I set up this build like last year, only recently started using Ubuntu. Do you want me to download the x86 XP drivers or the x64 since I'm on 64 bit?

---

### Post by adventuretime15 on 2013-08-25
I went ahead and downloaded the WinXP64 drivers "rtl819XP.inf" & "net819XP.sys" and followed the instructions, this is what I got:

```

joe@joe-MS-7641:~$ echo -e 'blacklist rtl8190\nblacklist wl' | sudo tee -a /etc/modprobe.d/blacklist
[sudo] password for joe: 
blacklist rtl8190
blacklist wl
joe@joe-MS-7641:~$ sudo apt-get install ndiswrapper-utils-1.9
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ndiswrapper-utils-1.9 is already the newest version.
ndiswrapper-utils-1.9 set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
joe@joe-MS-7641:~$ mkdir ~/rtl8190; cd ~/rtl8190
joe@joe-MS-7641:~/rtl8190$ sudo ndiswrapper -i net819xp.inf
installing net819xp ...
joe@joe-MS-7641:~/rtl8190$ ndiswrapper -l
net819xp : driver installed
    device (10EC:8190) present
joe@joe-MS-7641:~/rtl8190$ sudo depmod -a
joe@joe-MS-7641:~/rtl8190$ sudo modprobe ndiswrapper
FATAL: Module ndiswrapper not found.
joe@joe-MS-7641:~/rtl8190$ sudo cp /etc/network/interfaces /etc/network/interfaces.orig
joe@joe-MS-7641:~/rtl8190$ echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces
auto lo
iface lo inet loopback


joe@joe-MS-7641:~/rtl8190$ sudo ndiswrapper -m
module configuration already contains alias directive


joe@joe-MS-7641:~/rtl8190$ echo 'ndiswrapper' | sudo tee -a /etc/modules
ndiswrapper
joe@joe-MS-7641:~/rtl8190$ echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant
ENABLED=0

```

Still coming up as network *UNCLAIMED
```

joe@joe-MS-7641:~$ sudo su
root@joe-MS-7641:/home/joe# lshw -c Network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168 PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 06
       serial: d4:3d:7e:55:2c:d4
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168e-3_0.0.4 03/27/12 ip=192.168.1.139 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:42 ioport:d800(size=256) memory:fdfff000-fdffffff memory:fdff8000-fdffbfff
  *-network UNCLAIMED
       description: Network controller
       product: RTL8190 802.11n Wireless LAN
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:03:02.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64 maxlatency=64 mingnt=32
       resources: ioport:e800(size=256) memory:febff000-febfffff

```

---

### Post by chili555 on 2013-08-25
> joe@joe-MS-7641:~/rtl8190$ sudo modprobe ndiswrapper
FATAL: Module ndiswrapper not found.Do you have ndiswrapper-common installed?```
sudo dpkg -s ndiswrapper-common
```If not, please install it:```
sudo apt--get install ndiswrapper-common
```> I went ahead and downloaded the WinXP64 drivers "rtl819XP.inf" & "net819XP.sys"That is correct.

What does this tell us?```
sudo modprobe ndiswrapper [COLOR="#FF0000"]<---I realize this will error out.[/COLOR]
dmesg | grep ndis
```We hope there is an informative message in the logs.

---

### Post by adventuretime15 on 2013-08-25
Another fatal

```

joe@joe-MS-7641:~$ sudo dpkg -s ndiswrapper-common
[sudo] password for joe: 
Package: ndiswrapper-common
Status: install ok installed
Priority: optional
Section: misc
Installed-Size: 72
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: all
Source: ndiswrapper
Version: 1.58-0ubuntu1
Replaces: ndiswrapper-utils
Suggests: ndiswrapper-source
Description: Common scripts required to use the utilities for ndiswrapper
 Some vendors do not release specifications of the hardware or provide a
 Linux driver for their wireless network cards. This project implements
 Windows kernel API and NDIS (Network Driver Interface Specification) API
 within Linux kernel. A Windows driver for wireless network card is then
 linked to this implementation so that the driver runs natively, as though
 it is in Windows, without binary emulation.
 .
 This package contains wrapper scripts to call out to the proper
 versions of whatever -utils-X.X package is installed.
Homepage: http://ndiswrapper.sourceforge.net/
Original-Maintainer: Julian Andres Klode <jak@debian.org>
joe@joe-MS-7641:~$ sudo modprobe ndiswrapper
FATAL: Module ndiswrapper not found.

```

---

### Post by chili555 on 2013-08-25
As I said, we expected that. What did the second command say? We are interested in any *further* information from the dmesg log.

---

### Post by adventuretime15 on 2013-08-25
```

joe@joe-MS-7641:~$ sudo modprobe ndiswrapper
FATAL: Module ndiswrapper not found.
joe@joe-MS-7641:~$ dmesg | grep ndis
joe@joe-MS-7641:~$ 

```

---

### Post by chili555 on 2013-08-25
With a working ethernet connection:```
sudo apt-get install ndiswrapper-dkms
sudo modprobe ndiswrapper
```Any improvement?

---

### Post by adventuretime15 on 2013-08-25
You are a god! It was all because of the dkms issue of me not having dkms.. go figure hahah

```

joe@joe-MS-7641:~$ cd ~/rtl8190/
joe@joe-MS-7641:~/rtl8190$ sudo ndiswraper -i net819xp.inf
sudo: ndiswraper: command not found
joe@joe-MS-7641:~/rtl8190$ sudo ndiswrapper -i net819xp.inf
driver net819xp is already installed
joe@joe-MS-7641:~/rtl8190$ ndiswrapper -l
net819xp : driver installed
	device (10EC:8190) present
joe@joe-MS-7641:~/rtl8190$ sudo depmod -a
joe@joe-MS-7641:~/rtl8190$ sudo modprobe ndiswrapper
joe@joe-MS-7641:~/rtl8190$ sudo cp /etc/network/interfaces /etc/network/interfaces.orig
joe@joe-MS-7641:~/rtl8190$ echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces
auto lo
iface lo inet loopback


joe@joe-MS-7641:~/rtl8190$ sudo ndiswrapper -m
module configuration already contains alias directive


joe@joe-MS-7641:~/rtl8190$ echo 'ndiswrapper' | sudo tee -a /etc/modules
ndiswrapper
joe@joe-MS-7641:~/rtl8190$ echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant
ENABLED=0

```

I can actually see wifi networks in the taskbar now! Thanks a lot! I'll update you if it messes up by the time I move it home in a few minutes. Thanks again!

---

### Post by chili555 on 2013-08-26
Awesome! Glad it's working. Please mark the thread Solved: [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by adventuretime15 on 2013-08-26
Actually, I brought my computer home and tried to connect to one of the available wireless networks and this happens:

---

### Post by chili555 on 2013-08-26
Does it do so on every boot or was that an anomaly? Are there further clues here?```
cat /var/log/syslog | grep ndis

```This is likely to be lengthy, so please copy and paste it here and give us the link: [http://paste.ubuntu.com/](http://paste.ubuntu.com/)

If it is not lengthy or no results are returned, then try:```
cat /var/log/syslog.1 | grep ndis
```

---

