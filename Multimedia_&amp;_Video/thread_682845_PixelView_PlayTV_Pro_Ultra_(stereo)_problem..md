---
title: "PixelView PlayTV Pro Ultra (stereo) problem."
date: 2008-01-30
forum: Multimedia &amp; Video
---

### Post by b0rka7a on 2008-01-30
Hi all ! 
I can't use my PixelView PlayTV Ultra Pro (stereo) TV tuner.
I installed tvtime, but I see only blue screen.
Here's the output of dmesg:
```
...
...
[   33.661735] cx88[0]: Your board has no valid PCI Subsystem ID and thus can't
[   33.661737] cx88[0]: be autodetected.  Please pass card=<n> insmod option to
[   33.661738] cx88[0]: workaround that.  Redirect complaints to the vendor of
[   33.661740] cx88[0]: the TV card.  Best regards,
[   33.661741] cx88[0]:         -- tux
[   33.661743] cx88[0]: Here is a list of valid choices for the card=<n> insmod option:
[   33.661746] cx88[0]:    card=0 -> UNKNOWN/GENERIC
[   33.661748] cx88[0]:    card=1 -> Hauppauge WinTV 34xxx models
[   33.661751] cx88[0]:    card=2 -> GDI Black Gold
[   33.661753] cx88[0]:    card=3 -> PixelView
[   33.661755] cx88[0]:    card=4 -> ATI TV Wonder Pro
[   33.661757] cx88[0]:    card=5 -> Leadtek Winfast 2000XP Expert
[   33.661759] cx88[0]:    card=6 -> AverTV Studio 303 (M126)
[   33.661761] cx88[0]:    card=7 -> MSI TV-@nywhere Master
[   33.661763] cx88[0]:    card=8 -> Leadtek Winfast DV2000
[   33.661765] cx88[0]:    card=9 -> Leadtek PVR 2000
[   33.661767] cx88[0]:    card=10 -> IODATA GV-VCP3/PCI
[   33.661769] cx88[0]:    card=11 -> Prolink PlayTV PVR
[   33.661770] cx88[0]:    card=12 -> ASUS PVR-416
[   33.661772] cx88[0]:    card=13 -> MSI TV-@nywhere
[   33.661774] cx88[0]:    card=14 -> KWorld/VStream XPert DVB-T
[   33.661776] cx88[0]:    card=15 -> DViCO FusionHDTV DVB-T1
[   33.661778] cx88[0]:    card=16 -> KWorld LTV883RF
[   33.661780] cx88[0]:    card=17 -> DViCO FusionHDTV 3 Gold-Q
[   33.661782] cx88[0]:    card=18 -> Hauppauge Nova-T DVB-T
[   33.661784] cx88[0]:    card=19 -> Conexant DVB-T reference design
[   33.661786] cx88[0]:    card=20 -> Provideo PV259
[   33.661788] cx88[0]:    card=21 -> DViCO FusionHDTV DVB-T Plus
[   33.661790] cx88[0]:    card=22 -> pcHDTV HD3000 HDTV
[   33.661792] cx88[0]:    card=23 -> digitalnow DNTV Live! DVB-T
[   33.661794] cx88[0]:    card=24 -> Hauppauge WinTV 28xxx (Roslyn) models
[   33.661797] cx88[0]:    card=25 -> Digital-Logic MICROSPACE Entertainment Center (MEC)
[   33.661799] cx88[0]:    card=26 -> IODATA GV/BCTV7E
[   33.661801] cx88[0]:    card=27 -> PixelView PlayTV Ultra Pro (Stereo)
[   33.661803] cx88[0]:    card=28 -> DViCO FusionHDTV 3 Gold-T
[   33.661805] cx88[0]:    card=29 -> ADS Tech Instant TV DVB-T PCI
[   33.661807] cx88[0]:    card=30 -> TerraTec Cinergy 1400 DVB-T
[   33.661810] cx88[0]:    card=31 -> DViCO FusionHDTV 5 Gold
[   33.661812] cx88[0]:    card=32 -> AverMedia UltraTV Media Center PCI 550
[   33.661814] cx88[0]:    card=33 -> Kworld V-Stream Xpert DVD
[   33.661816] cx88[0]:    card=34 -> ATI HDTV Wonder
[   33.661818] cx88[0]:    card=35 -> WinFast DTV1000-T
[   33.661820] cx88[0]:    card=36 -> AVerTV 303 (M126)
[   33.661822] cx88[0]:    card=37 -> Hauppauge Nova-S-Plus DVB-S
[   33.661824] cx88[0]:    card=38 -> Hauppauge Nova-SE2 DVB-S
[   33.661826] cx88[0]:    card=39 -> KWorld DVB-S 100
[   33.661828] cx88[0]:    card=40 -> Hauppauge WinTV-HVR1100 DVB-T/Hybrid
[   33.661830] cx88[0]:    card=41 -> Hauppauge WinTV-HVR1100 DVB-T/Hybrid (Low Profile)
[   33.661833] cx88[0]:    card=42 -> digitalnow DNTV Live! DVB-T Pro
[   33.661835] cx88[0]:    card=43 -> KWorld/VStream XPert DVB-T with cx22702
[   33.661837] cx88[0]:    card=44 -> DViCO FusionHDTV DVB-T Dual Digital
[   33.661839] cx88[0]:    card=45 -> KWorld HardwareMpegTV XPert
[   33.661842] cx88[0]:    card=46 -> DViCO FusionHDTV DVB-T Hybrid
[   33.661844] cx88[0]:    card=47 -> pcHDTV HD5500 HDTV
[   33.661846] cx88[0]:    card=48 -> Kworld MCE 200 Deluxe
[   33.661848] cx88[0]:    card=49 -> PixelView PlayTV P7000
[   33.661850] cx88[0]:    card=50 -> NPG Tech Real TV FM Top 10
[   33.661852] cx88[0]:    card=51 -> WinFast DTV2000 H
[   33.661854] cx88[0]:    card=52 -> Geniatech DVB-S
[   33.661856] cx88[0]:    card=53 -> Hauppauge WinTV-HVR3000 TriMode Analog/DVB-S/DVB-T
[   33.661858] cx88[0]:    card=54 -> Norwood Micro TV Tuner
[   33.661860] cx88[0]:    card=55 -> Shenzhen Tungsten Ages Tech TE-DTV-250 / Swann OEM
[   33.661863] cx88[0]:    card=56 -> Hauppauge WinTV-HVR1300 DVB-T/Hybrid MPEG Encoder
[   33.661866] CORE cx88[0]: subsystem: 0000:0000, board: UNKNOWN/GENERIC [card=0,autodetected]
[   33.661870] TV tuner -1 at 0x1fe, Radio tuner -1 at 0x1fe
[   34.205838] tveeprom 0-0050: Huh, no eeprom present (err=-121)?
[   34.205861] cx88[0]/0: found at 0000:02:02.0, rev: 5, irq: 20, latency: 32, mmio: 0xeb000000
[   34.269449] tuner 0-0061: chip found @ 0xc2 (cx88[0])
[   34.270413] tuner 0-0063: chip found @ 0xc6 (cx88[0])
[   34.279518] cx88[0]/0: registered device video0 [v4l2]
[   34.279551] cx88[0]/0: registered device vbi0
[   34.279562] tuner 0-0061: tuner type not set
...
...
```
I can't tell you anything more.
Anyone can help ? :confused:

---

