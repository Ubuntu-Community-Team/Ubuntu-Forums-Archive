---
title: "Why is my video output so poor?"
date: 2010-10-19
forum: Multimedia Software
---

### Post by cknight on 2010-10-19
Attached is an example of what my video output looks like.

Other than awful, does this artifacting have a name? It's worst when the video pans and OK'ish when the video is still.  

I'm using VLC to run this video from a DVD.  Currently using "X11 Video output".  I've tried other video outputs without much difference.  OK, I know I'm on a laptop which doesn't have the worlds greatest video card, but surely I should get better output than this?

Here's my lspci output:
```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3650
01:00.1 Audio device: ATI Technologies Inc RV635 Audio device [Radeon HD 3600 Series]
04:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
08:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)
09:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
09:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
09:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
09:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)

```

I currently have Compiz enabled (but again, I don't think it makes any difference as I've tried it without as well).  Additionally, I'm running the open source video drivers.  Any help appreciated on how to get better quality than the attached.

---

### Post by cknight on 2010-10-20
bump

---

### Post by ron999 on 2010-10-20
Hi
Those lines are "mouse's teeth".:)
Caused because DVD videos are 'interlaced'.
Interlacing is fine for TV sets, but causes problems with PC monitors.

So you need to de-interlace it with your media player.
If you're using VLC Media Player look in Video > Deinterlace and choose one of the options. 
Similarly with SMPlayer.

There's information at Wikipedia here:- [http://en.wikipedia.org/wiki/Interlace]("http://en.wikipedia.org/wiki/Interlace")

---

### Post by cknight on 2010-10-20
> **ron999 said:**
> Hi
Those lines are "mouse's teeth".:)
Caused because DVD videos are 'interlaced'.
Interlacing is fine for TV sets, but causes problems with PC monitors.

So you need to de-interlace it with your media player.
If you're using VLC Media Player look in Video > Deinterlace and choose one of the options. 
Similarly with SMPlayer.

There's information at Wikipedia here:- [http://en.wikipedia.org/wiki/Interlace]("http://en.wikipedia.org/wiki/Interlace")

Ah, so interlacing is at fault.  At last I have something to google with!  For anyone else who finds this, its not as simple as changing the deinterlace settings within Video->Deinterlace Mode.  You also have to turn the deinterlace video filter on as well (how naff is it that setting a deinterlace mode doesn't automatically turn the output filter on?).  Anyway, here's what you need to do:

1) Goto Video->Preferences
2) Select 'All' from Show Settings (lower left corner)
3) Click on 'Filters' under the Video submenu
4) Check the box next to 'Deinterlacing video filter' under the Video Filter Module list.
5) Select 'Simple' from Show Settings
6) Under the Video options, choose anything except 'Discard' under 'Deinterlacing Mode'.
7) Restart VLC

Thanks Ron999!

---

