---
title: "Trying to get ethernet working"
date: 2010-04-11
forum: Networking &amp; Wireless
---

### Post by jonathan3087 on 2010-04-11
I have an old ThinkPad T20 that was running Win2000, everything worked, NIC, CD-ROM, etc.  But wanted to revive this old laptop by installing Ubuntu.  I downloaded and installed Ubuntu 9.10.

The machine boots into Ubuntu, but I can't get connected to the internet, via Ethernet.  I think that I need a driver for the NIC, but don't really know where to begin.  I am pretty new at this.  I did see another post that requested that the requeseter use the lspci -nn command to give some system info.  I am posting my results for that below:

lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge [8086:7190] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge [8086:7191] (rev 03)
00:02.0 CardBus bridge [0607]: Texas Instruments PCI1450 [104c:ac1b] (rev 03)
00:02.1 CardBus bridge [0607]: Texas Instruments PCI1450 [104c:ac1b] (rev 03)
00:03.0 Communication controller [0780]: Agere Systems WinModem 56k [11c1:0449] (rev 01)
00:05.0 Multimedia audio controller [0401]: Cirrus Logic CS 4614/22/24/30 [CrystalClear SoundFusion Audio Accelerator] [1013:6003] (rev 01)
00:07.0 Bridge [0680]: Intel Corporation 82371AB/EB/MB PIIX4 ISA [8086:7110] (rev 02)
00:07.1 IDE interface [0101]: Intel Corporation 82371AB/EB/MB PIIX4 IDE [8086:7111] (rev 01)
00:07.2 USB Controller [0c03]: Intel Corporation 82371AB/EB/MB PIIX4 USB [8086:7112] (rev 01)
00:07.3 Bridge [0680]: Intel Corporation 82371AB/EB/MB PIIX4 ACPI [8086:7113] (rev 03)
01:00.0 VGA compatible controller [0300]: S3 Inc. 86C270-294 Savage/IX-MV [5333:8c12] (rev 11)


Thanks in advance for any advice.

---

### Post by Iowan on 2010-04-12
I prefer **sudo lshw -C network** - mostly because I'm used to it. 
Another T20 post to check:
[http://ubuntuforums.org/showthread.php?t=1362600]("http://ubuntuforums.org/showthread.php?t=1362600")

---

### Post by jonathan3087 on 2010-04-12
Ran the command you posted, and I got the following.  I don't know what it all means.  Also, I'll read through posts at the link you posted, thanks.

  *-network               
       description: 802.11b CardBus
       vendor: Broadcom
       physical id: 0
       version: 8.0
       slot: Socket 1
       resources: irq:11
  *-network
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:06:00.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:11 memory:18000000-18001fff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:4b:ca:92:2b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

---

### Post by jonathan3087 on 2010-04-12
I remembered that the first time I installed I did not have the network cable plugged in from my router to the laptop, so, with that plugged in this time, I just reinstalled from the ISO disk ver 09.10.

My thinking was that if the connection was there, that maybe it would detect it.

I have no internet from the Thinkpad T20 that I am installing on at all, I can't get ethernet to work nor can I get the PCMCIA Dell 1350 wireless card to get installed.

I will take either at this point, but ultimately I want the wireless.

Any help you can provide would be so helpful.  

Thanks in advance,
Jonathan

---

