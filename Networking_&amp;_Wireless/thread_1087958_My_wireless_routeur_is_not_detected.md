---
title: "My wireless routeur is not detected"
date: 2009-03-05
forum: Networking &amp; Wireless
---

### Post by fa355115 on 2009-03-05
Hi there !

I have just installed ubuntu in dual boot with my vista, and I'm getting my first problem with my wireless routeur which is not detected. I do see 10 other wireless devices, but mine is not in the list.

_My routeur is configured with :_
SSID broadcast : yes
security : wpa2
Cypher suite : AES
pre-shared-key : hex

... but his name is not appearing in the list. I have also tried to configure a manual connection, but it canmt connect (just as the key was not correct)

In good student, I have tried to follow the tuto posted on top of this forum with **ndiswrapper**, but it looks like it is not installed.

When I'm typing the command to install it, it complains I'm not root (I'm effectively logged in as the user I defined during the installation). Problem is that I do not have the root pw (I have not set any), and I'm even not sure the ndiswrapper would solve my problem.

Anything to start with ?

many thanks !

---

### Post by Cybie257 on 2009-03-05
use sudo plus what you are doing to get root access..

-Cybie

IE: sudo apt-get install package

---

### Post by fa355115 on 2009-03-05
it is not working.
I think it tells the ndiswrapper can not be found.

---

### Post by Crafty Kisses on 2009-03-05
In order for us to help you, we need more information. What are the results of these commands?
```
sudo lshw -C network
lspci
```

---

### Post by fa355115 on 2009-03-06
you are ..

P.S. please note my neighboor below also has the same routeur has mine, ant it is seen in the list ...

yep@HP-ubuntu:~$ sudo lshw -C network 
[sudo] password for yep:  
  *-network                
       description: Wireless interface 
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection 
       vendor: Intel Corporation 
       physical id: 0 
       bus info: pci@0000:02:00.0 
       logical name: wmaster0 
       version: 61 
       serial: 00:13:e8:ec:d6:99 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless 
       configuration: broadcast=yes driver=iwlagn latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn 
  *-network 
       description: Ethernet interface 
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 0 
       bus info: pci@0000:06:00.0 
       logical name: eth0 
       version: 01 
       serial: 00:1b:24:ce:21:7e 
       capacity: 1GB/s 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no module=r8169 multicast=yes port=twisted pair 
  *-network DISABLED 
       description: Ethernet interface 
       physical id: 1 
       logical name: pan0 
       serial: 7e:5f:57:1d:20:47 
       capabilities: ethernet physical 
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes 

:::::::

yep@HP-ubuntu:~$ lspci 
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c) 
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c) 
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03) 
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03) 
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03) 
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03) 
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03) 
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03) 
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03) 
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03) 
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03) 
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03) 
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03) 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3) 
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03) 
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03) 
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03) 
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03) 
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600M GS (rev a1) 
02:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61) 
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01) 
07:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05) 
07:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22) 
07:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12) 
07:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12) 
07:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

---

### Post by fa355115 on 2009-03-06
I have just removed the wpa security.
Routeur is now with "no wep, no wpa", and I'm sure the "Enable broadcast" is on ...

**But is is still invisible**

So I suspect an incompatibility between the PC and the routeur, having nothing to do with wpa.
The routeur is an adsl Philips routeur CIA6720nb / 18

I'm new with linux ... so I even do not know if I could install a driver provided by philips, or if I need to install drivers fro, ubuntu community ... assuming this is a driver issue ?

Many thanks for helping me

---

### Post by fa355115 on 2009-03-07
Nobody to help me here ?

Thank you !!

---

### Post by albandy on 2009-03-07
change the wireless channel to ch 1 o ch 2.

---

### Post by fa355115 on 2009-03-07
Many Thanks ... I changed the channel on my routeur from 11 to 1, restared the routeur, restarted ubuntu, **and the routeur was seen !!!**

I changed it back to the original setting (channel 11), restarted the routeur and ubuntu, and now the routeur is also seen with channel 11 ?!?

What was the problem here ???

---

### Post by zenithdave on 2009-03-07
> **fa355115 said:**
> Many Thanks ... I changed the channel on my routeur from 11 to 1, restared the routeur, restarted ubuntu, **and the routeur was seen !!!**

I changed it back to the original setting (channel 11), restarted the routeur and ubuntu, and now the routeur is also seen with channel 11 ?!?

What was the problem here ???

[http://ubuntuforums.org/showthread.php?t=1087879](http://ubuntuforums.org/showthread.php?t=1087879) ;)

---

### Post by fa355115 on 2009-03-08
ok guys ... the problem is with using channel 12 !!

cedric@HP-ubuntu:~$ iwlist wlan0 channel
wlan0     19 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Current Frequency=2.412 GHz (Channel 1)

---

