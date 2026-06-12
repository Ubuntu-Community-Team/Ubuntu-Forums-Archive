---
title: "GMA X4500 video problems"
date: 2009-10-21
forum: Multimedia Software
---

### Post by tsm2010 on 2009-10-21
Mother: Asus P5QPL-VM EPU
Video: GMA x4500/G41
Distro: Jaunty (X Updates)
        xserver-xorg-video-intel 2.2.9.0
Monitor: Dell
HDTV: Sharp Aquos 1080p

The Asus motherboard has three video outputs: VGA, DVI, & HDMI.  I'm
ignoring the VGA output.  The graphic processor is an
Intel GMA X4500:G41:2E32.

-----
lspci -vvnn:
00:02.0 VGA compatible controller [0300]: Intel Corporation 4 Series
Chipset Integrated Graphics Controller [8086:2e32] (rev 03)

Subsystem: ASUSTeK Computer Inc. Device [1043:836d]

Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr-
Stepping- SERR- FastB2B- DisINTx+
-----

If I connect the DVI port to my Dell monitor, I can select (and do select)
the full 1920x1080 resolution.

If I connect the HDMI port to the Aquos and reboot, I get 1600x1200,
60hz, period, on both displays.  I cannot change the resolution on either
display, at all.  I cannot change HDMI1, the Dell, or HDMI2, the Aquos.

XRandR tells me that I may choose 1920, 1368, etc, but I can't actually
select any of these other resolutions.  This is kind of annoying, to tell
the truth.  I bought this Motherboard as the basis for a home theater
PC.  Don't tell me that I have to go the Windows route...

/etc/X11/xorg.conf is no help at all, it's filled with generic blab:

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Where are the real config files?

How the heck do I fix this?  I want 1920x1080 on both my Dell and
my Sharp.

~Tom

---

### Post by cignu on 2010-01-19
bump

i have the same problem..

---

