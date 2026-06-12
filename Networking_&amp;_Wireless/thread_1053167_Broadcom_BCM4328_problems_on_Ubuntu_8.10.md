---
title: "Broadcom BCM4328 problems on Ubuntu 8.10"
date: 2009-01-28
forum: Networking &amp; Wireless
---

### Post by kevinmack on 2009-01-28
Hi everybody,

I'm brand-new to Ubuntu (installed 8.10 as a dual-boot after a Windows rootkit forced me to wipe and reinstall OS anyway).  I'm running a Dell Inspiron E1705 laptop with a Broadcom BCM4328 wireless adaptor, and I'm having trouble getting the network manager to recognize it.

Under System->Administration->Hardware Drivers, I have the fwcutter driver for Broadcom B43 wireless cards activated and in use.  Broadcom STA wireless driver is available, but not currently activated.

When I hit the network manager icon, wired network connection is available and working, but no wireless options are listed.  The wireless adaptor does work correctly under Windows.

I know I'm not the first to have had trouble with this card under Linux - anybody know what the currently accepted solution is?

Thanks!

Here's lshw and iwconfig info, in case it helps:

kmack@kmack-laptop:~$ sudo lshw -C network
[sudo] password for kmack: 
  *-network               
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:59:60:23
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.0.7 latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 42:a7:1c:32:ca:29
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
kmack@kmack-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

---

### Post by Ayuthia on 2009-01-28
The 4328 card can use the Broadcom STA module or NDISwrapper.  The b43 module does not support it yet.  You can try the following to see if you can get your wireless to activate:
```
sudo modprobe -r b43 b44 ssb wl
sudo modprobe wl
sudo modprobe b44
sudo /etc/init.d/networking restart
sudo iwlist scan
```

Let us know how it turns out.

---

### Post by Josh_Lapointe on 2009-01-28
Hey
Had the exact same problem as you, what I would suggest, get the latest updates and make sure you have Multiverse in your repositories active, and update, from there, if you got your Hardware Settings, it'll show up a Broadcom Driver for your card, and you can use that. Thats how I fixed my problem. (Kubuntu 8.10)

EDIT:

QUOTE:"Under System->Administration->Hardware Drivers, I have the fwcutter driver for Broadcom B43 wireless cards activated and in use. Broadcom STA wireless driver is available, but not currently activated."

Activate that Broadcom STA Wireless Driver. It should fix it.

---

### Post by Ayuthia on 2009-01-28
> **Josh_Lapointe said:**
> Hey
Had the exact same problem as you, what I would suggest, get the latest updates and make sure you have Multiverse in your repositories active, and update, from there, if you got your Hardware Settings, it'll show up a Broadcom Driver for your card, and you can use that. Thats how I fixed my problem. (Kubuntu 8.10)

EDIT:

QUOTE:"Under System->Administration->Hardware Drivers, I have the fwcutter driver for Broadcom B43 wireless cards activated and in use. Broadcom STA wireless driver is available, but not currently activated."

Activate that Broadcom STA Wireless Driver. It should fix it.

Can you post the results of:
```
lspci -nn
lshw -C network
lsmod|grep -e b43 -e wl
```
I am surprised to see that you are able to use the b43 module because it does not support the wireless-n chipsets yet.

EDIT:
The only reason why I have not suggested the Hardware Drivers route yet is because you have a b44 wired card module in use.  It generally will prevent the wl module from loading properly.

---

### Post by Josh_Lapointe on 2009-01-28
Yeah, will do when I get to my console, i'm currently at work. And yeah, note as mentioned before, N doesn't work. But the rest of the spectrum does, cause I've connected.

---

### Post by kevinmack on 2009-01-28
Turned out activating the STA driver was all it took.  Thanks!
I'm really impressed with the Ubuntu setup process, actually.  After installing WinXP on this machine, I still had to spend another 1.5 hours hunting down chipset drivers before everything worked.  Ubuntu found everything and activated the drivers right from the start - the wireless card was the only piece of hardware that didn't work immediately.  Really impressive :)

Ayuthia, you'd asked Josh for his hardware config info - I'll give you mine too, just so you have it:

Thanks again, Ayuthia and Josh!

kmack@kmack-laptop:~$ lspci -nn
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
03:01.2 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 0a)
03:01.3 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 05)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4328 802.11a/b/g/n [14e4:4328] (rev 01)
kmack@kmack-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial: 00:16:cf:a0:35:7d
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl ip=172.30.200.202 latency=0 module=wl multicast=yes wireless=IEEE 802.11
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:59:60:23
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=64 module=ssb multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 66:ac:40:94:db:de
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
kmack@kmack-laptop:~$ lsmod|grep -e b43 -e wl
wl                   1076372  0 
ieee80211_crypt        13572  2 ieee80211_crypt_tkip,wl
kmack@kmack-laptop:~$

---

### Post by anandi on 2009-02-25
I have a mac book pro with "Broadcom Corporation BCM4328 802.11a/b/g/n (rev 05)".

I am using the proprietary drivers which came with intrepid, however i am facing a very high latency issue. In the same network, i am getting latency from 2ms to as high as 200+ms. When i connect my wired connection, the same drops to less than 1ms.

I tried to use the solution mentioned in the thread

```

sudo modprobe -r b43 b44 ssb wl
sudo modprobe wl
sudo modprobe b44
sudo /etc/init.d/networking restart
sudo iwlist scan

```

The above did disconnect me from the network and got reconnected, however the high latency issue wasn't resolved.

Here is the output of lspci and other stuff.

```

lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port [8086:2a01] (rev 03)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 03)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 [8086:2843] (rev 03)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 [8086:2847] (rev 03)
00:1c.5 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 [8086:2849] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f3)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 03)
00:1f.2 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller [8086:2828] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 03)
01:00.0 VGA compatible controller [0300]: nVidia Corporation GeForce 8600M GT [10de:0407] (rev a1)
0b:00.0 Network controller [0280]: Broadcom Corporation BCM4328 802.11a/b/g/n [14e4:4328] (rev 05)
0c:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. Marvell Yukon 88E8058 PCI-E Gigabit Ethernet Controller [11ab:436a] (rev 13)
0d:03.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB82AA2 IEEE-1394b Link Layer Controller [104c:8025] (rev 02)

```

```

sudo lshw -C network
  *-network               
       description: Wireless interface
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: eth1
       version: 05
       serial: 00:1e:c2:ba:43:d7
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.27.12 ip=192.168.1.33 latency=0 module=wl multicast=yes wireless=IEEE 802.11abgn
  *-network
       description: Ethernet interface
       product: Marvell Yukon 88E8058 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth0
       version: 13
       serial: 00:1e:c2:1e:5e:27
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 6a:8c:c2:2c:90:61
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

```

lsmod|grep -e b43 -e wl
wl                   1080212  0 
ieee80211_crypt        13572  2 wl,ieee80211_crypt_tkip

```

Any ideas how this latency issue can be resolved ? Any help would be highly appreciated.

---

### Post by epimeth on 2009-05-14
hi all... I have a dell XPS M1530 with intrepid and a BCM4328

I wanted to thank Ayuthia for the solution to my lack of wireless except for a teensie problem... I have to run the commands after every restart.  Is there any way to make these changes stick?

if it matters, I have the STA driver installed.....

Thanks!

---

### Post by Ayuthia on 2009-05-16
You can try this link:
[http://ubuntuforums.org/showpost.php?p=7288170&postcount=7](http://ubuntuforums.org/showpost.php?p=7288170&postcount=7)

Just don't do the following command from that link:
sudo rm /etc/modprobe.d/wl

This was only done because I had that person create that file in a previous post.  You should not have that file in your system.

Hope that helps.

---

