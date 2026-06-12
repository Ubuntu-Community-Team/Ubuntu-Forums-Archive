---
title: "ATI TV Wonder Pro not working"
date: 2006-08-05
forum: Multimedia &amp; Video
---

### Post by reckless2k2 on 2006-08-05
From what I can tell from reading around, this card is supported in Linux but I just can't seem to get it working. Any help would be appreciated. 

lspci -v

0000:02:0b.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
        Subsystem: ATI Technologies Inc: Unknown device 00f9
        Flags: bus master, medium devsel, latency 64, IRQ 193
        Memory at f6000000 (32-bit, non-prefetchable) [size=16M]
        Capabilities: <available only to root>

dmesg

[4294693.539000] cx2388x v4l2 driver version 0.0.5 loaded
[4294693.539000] ACPI: PCI Interrupt 0000:02:0b.0[A] -> GSI 23 (level, low) -> IRQ 193
[4294693.539000] cx88[0]: Your board isn't known (yet) to the driver.  You can
[4294693.539000] cx88[0]: try to pick one of the existing card configs via
[4294693.539000] cx88[0]: card=<n> insmod option.  Updating to the latest
[4294693.539000] cx88[0]: version might help as well.
[4294693.539000] cx88[0]: Here is a list of valid choices for the card=<n> insmod option:
[4294693.539000] cx88[0]:    card=0 -> UNKNOWN/GENERIC
[4294693.539000] cx88[0]:    card=1 -> Hauppauge WinTV 34xxx models
[4294693.539000] cx88[0]:    card=2 -> GDI Black Gold
[4294693.539000] cx88[0]:    card=3 -> PixelView
[4294693.539000] cx88[0]:    card=4 -> ATI TV Wonder Pro
[4294693.539000] cx88[0]:    card=5 -> Leadtek Winfast 2000XP Expert
[4294693.539000] cx88[0]:    card=6 -> AverTV Studio 303 (M126)
[4294693.539000] cx88[0]:    card=7 -> MSI TV-@nywhere Master
[4294693.539000] cx88[0]:    card=8 -> Leadtek Winfast DV2000
[4294693.539000] cx88[0]:    card=9 -> Leadtek PVR 2000
[4294693.539000] cx88[0]:    card=10 -> IODATA GV-VCP3/PCI
[4294693.539000] cx88[0]:    card=11 -> Prolink PlayTV PVR
[4294693.539000] cx88[0]:    card=12 -> ASUS PVR-416
[4294693.539000] cx88[0]:    card=13 -> MSI TV-@nywhere
[4294693.539000] cx88[0]:    card=14 -> KWorld/VStream XPert DVB-T
[4294693.539000] cx88[0]:    card=15 -> DViCO FusionHDTV DVB-T1
[4294693.539000] cx88[0]:    card=16 -> KWorld LTV883RF
[4294693.539000] cx88[0]:    card=17 -> DViCO FusionHDTV 3 Gold-Q
[4294693.539000] cx88[0]:    card=18 -> Hauppauge Nova-T DVB-T
[4294693.539000] cx88[0]:    card=19 -> Conexant DVB-T reference design
[4294693.539000] cx88[0]:    card=20 -> Provideo PV259
[4294693.539000] cx88[0]:    card=21 -> DViCO FusionHDTV DVB-T Plus
[4294693.539000] cx88[0]:    card=22 -> pcHDTV HD3000 HDTV
[4294693.539000] cx88[0]:    card=23 -> digitalnow DNTV Live! DVB-T
[4294693.539000] cx88[0]:    card=24 -> Hauppauge WinTV 28xxx (Roslyn) models
[4294693.539000] cx88[0]:    card=25 -> Digital-Logic MICROSPACE Entertainment Center (MEC)
[4294693.539000] cx88[0]:    card=26 -> IODATA GV/BCTV7E
[4294693.539000] cx88[0]:    card=27 -> PixelView PlayTV Ultra Pro (Stereo)
[4294693.539000] cx88[0]:    card=28 -> DViCO FusionHDTV 3 Gold-T
[4294693.539000] cx88[0]:    card=29 -> ADS Tech Instant TV DVB-T PCI
[4294693.539000] cx88[0]:    card=30 -> TerraTec Cinergy 1400 DVB-T
[4294693.539000] cx88[0]:    card=31 -> DViCO FusionHDTV 5 Gold
[4294693.539000] cx88[0]:    card=32 -> AverMedia UltraTV Media Center PCI 550
[4294693.539000] cx88[0]:    card=33 -> Kworld V-Stream Xpert DVD
[4294693.539000] cx88[0]:    card=34 -> ATI HDTV Wonder
[4294693.539000] cx88[0]:    card=35 -> WinFast DTV1000-T
[4294693.539000] cx88[0]:    card=36 -> AVerTV 303 (M126)
[4294693.539000] CORE cx88[0]: subsystem: 1002:00f9, board: UNKNOWN/GENERIC [card=0,autodetected]
[4294693.539000] TV tuner -1 at 0x1fe, Radio tuner -1 at 0x1fe
[4294693.753000] cx88[0]/0: found at 0000:02:0b.0, rev: 5, irq: 193, latency: 64, mmio: 0xf6000000
[4294693.775000] tuner 0-0060: All bytes are equal. It is not a TEA5767
[4294693.775000] tuner 0-0060: chip found @ 0xc0 (cx88[0])
[4294693.811000] cx88[0]/0: registered device video0 [v4l2]
[4294693.811000] cx88[0]/0: registered device vbi0
[4294693.811000] tuner 0-0060: tuner type not set
[4294895.687000] tuner 0-0060: tuner type not set
[4294895.871000] tuner 0-0060: tuner type not set
[4295724.953000] tuner 0-0060: tuner type not set
[4295725.173000] tuner 0-0060: tuner type not set
[4296389.744000] bttv: driver version 0.9.16 loaded
[4296389.744000] bttv: using 8 buffers with 2080k (520 pages) each for capture

Any tv program I use is not working. For instance, using tvtime and trying to run tvtime-scanner, I get the "no tuner found on input 0" error.

---

### Post by Pooch on 2006-08-10
I have the same problem. Did you ever get it working?

---

### Post by reckless2k2 on 2006-08-18
I returned it for a Hauppauge PVR150. Supposedly, the ATI PCI TV Wonder will work but I couldn't get it to. The PVR150 does work but ONLY with MythTV after you've compiled the ivtv driver. If you don't want to deal with all that mess, the $50 Hauppauge WinTV card works great out of box with tvtime and such.

---

