---
title: "Wireless Install won't in Persistent USB Install"
date: 2010-12-21
forum: Networking &amp; Wireless
---

### Post by M_Mynaardt on 2010-12-21
Hi!

I'm trying to use a persistent install of Lubuntu 10.10 on a USB flash drive.  I _thought_ it was working at first, but the wireless connection won't happen at all; period!

Whenever I click on the network Icon, all I get is a pop up message telling me I'm not connected to the wireless  Then when I click on the wireless menu to select a network, the sign in window closes before I can even try to do anything with it, and then I get that "your not connected" pop up message again.

It's quite irritating.  It basically won't let me sign on to a wireless Internet connection at all.  Every time I do try to connect all I get is the "your not connected" message and nothing else.

I'm using a 16 GB Kingston Data Traveler USB flash drive and am trying to run it on a Toshiba A100 Satellite laptop.

I've also been experimenting with a 16 GB Kingston Data Traveler 102 USB flash drive, with Linux Mint 9 LXDE installed on it and haven't had any problems with that one accessing wireless connections on the same computer.

Does anyone know what would cause this?  It seems to boot well enough.  But I just can't get Lubuntu 10.10 to access wireless networks to save my life.  Could it be a hardware issue?

I should note too that I used exactly the same USB flash drive on the same computer when giving Xubuntu 10.10 a "test drive" as a persistent install.  But I didn't have any troubles like that with it...

Thanks...

---

### Post by slooow on 2010-12-21
It seems to me that you need to find out what your wireless card is and if the module (driver) for it is installed.
Try 
```
lspci
```
first, to see if the card is seen in your system.

---

### Post by M_Mynaardt on 2010-12-22
> **slooow said:**
> It seems to me that you need to find out what your wireless card is and if the module (driver) for it is installed.
Try 
```
lspci
```
first, to see if the card is seen in your system.

I never thought of checking the wireless card and/or module.  I just assumed it would be up and running pretty as you please.

I tried the lspci command and do not know enough to know exactly what I'm looking for.  I deleted the obvious irrelevant things like *USB Controller*, or *Audio device*.  And what I have left is::

00:00.0 Host bridge: ATI Technologies Inc Device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
     [snip, snip, snip]
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
     [snip, snip, snip]
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
     [snip, snip, snip]
02:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
05:06.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
05:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
05:0a.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev c0)

Is any of that helpful?  I"m not going to pretend that it makes sense to me right now!
:-\"

Thanks for your time!

---

