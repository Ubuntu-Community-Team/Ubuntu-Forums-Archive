---
title: "Lost wireless after upgrading to 8.10"
date: 2009-01-05
forum: Networking &amp; Wireless
---

### Post by nirpius on 2009-01-05
I was running 8.04 for ages on Ubuntu with no internet issues. I upgraded to 8.10 and have had a problem with my wireless. I kept my home folder the same as it was before and expected that it would connect to the internet fine.

It didn't. It could read the signal strength and when I tried to connect, the first of the two little circles on that network connection thingy in the panel would go green but ti would never go to the second one.

It would then ask me to re-enter the network key (wpa) and I would put it in. It would again flash the first circle but not the second. Whenever it asks me to re-enter the passcode it has substititued the 8 digits I put in originally for loads of them in a sequence like f23h42v56v23j54m34n6m25... and I have no idea where this has come from.

Like I said, everything worked fine on 8.04 but after upgrading, it doesn't work. I've reinstalled a couple of times but it's the same issue.

Any ideas?

---

### Post by rallen32 on 2009-01-10
Hi, I am completely new and have identical problem... wireless worked ok in Heron and not in Ibex.  If i disable security (WPA) it connects just fine.  I updated on wired connection to see if there were any fixes but am at a loss.  Any help?
Thanks
Bob

---

### Post by nirpius on 2009-01-15
Bump?

---

### Post by ProNux on 2009-01-23
In my case, (though, kernel upgrade only in 8.04 Hardy), I removed the old install, then recompiled the source code again.  I am using Ralink RT3-based Wireless LAN.

---

### Post by Elotero on 2009-01-23
Same issue... only with Gutsy. 

I went from Gusty to Hardy and my connection got hosed. I figured if i upgraded to Ibix it would get fixed. Never happened. 

Really hesitant to upgrade to anything after this. 

Initially it took months of lurking around the forums to get it to work only to get hosed "upgrading" 

I do get some message on bootup that asks me to go to linuxwireless.com and download something... the message usually pops up so fast i cant tell what it wants me to do.

All i know is Broadcom modems suck for Ubuntu.

---

### Post by jsternberg on 2009-01-23
Same thing with Hardy 8.04/ My wireless also stopped working a week or so ago, although I didn't change anything (except automatic upgrades). Running 8.04 with Verizon DSL and a Westell modem, my other windows computer connects to wireless ok, so I know it's not a router problem. My Ubuntu machine sees various wireless networks, including mine, but keeps asking for hex password (although router uses WEP 138 passphrase in plain text). I see folks using Intrepid are having similar problems, but I haven't seen a fix yet, and don't know enough Linux myself. Any clues appreciated.

Ubuntu 8.04 (hardy)
2.6.24-23-generic (#1 SMP Thu Nov 27 18:44:42 UTC 2008)

i'm currently online using my ethernet connection because wireless isn't working]
*-network
description: Wireless interface
product: PRO/Wireless 3945ABG Network Connection
vendor: Intel Corporation
physical id: 0
bus info: pci@0000:0c:00.0
logical name: wmaster0
version: 02
serial: 00:1c:bf:36:2b:c4
width: 32 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g
*-network
description: Ethernet interface
product: NetLink BCM5906M Fast Ethernet PCI Express
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:09:00.0
logical name: eth0
version: 02
serial: 00:1d:09:3a:ff:1e
size: 100MB/s
capacity: 100MB/s
width: 64 bits
clock: 33MHz
capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 duplex=full ip=192.168.1.46 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s
jsternberg is online now Report Post   	Edit/Delete Message

 iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.
wmaster0  no wireless extensions.
eth1      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:12:0E:0F:36:F0   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

 lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

---

### Post by nirpius on 2009-12-14
Out of date, I admit but I am going through my old posts and marking those that are solved.

This issue has followed me around since it started but it is now put to rest by installing Wicd (in universe repositories) instead of networkmanager.

---

