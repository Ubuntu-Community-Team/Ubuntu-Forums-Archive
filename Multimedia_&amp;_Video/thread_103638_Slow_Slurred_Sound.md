---
title: "Slow Slurred Sound"
date: 2005-12-14
forum: Multimedia &amp; Video
---

### Post by satbunny on 2005-12-14
Breezy Gnome Tosh portge 3440CT laptop

Very slow sound, literally slow motion, when I use totem. perfetctly fine sound when I use amarok. Sounds sometimes slurs on startup, sometimes not.

lspci reports:

0000:00:00.0 Host bridge: Intel Corp. 82440MX Host Bridge (rev 01)
0000:00:00.1 Multimedia audio controller: Intel Corp. 82440MX AC'97 Audio Controller
0000:00:02.0 Communication controller: Lucent Microelectronics 56k WinModem (rev 01)
0000:00:04.0 VGA compatible controller: S3 Inc. 86C270-294 Savage/IX-MV (rev 11)
0000:00:07.0 Bridge: Intel Corp. 82440MX ISA Bridge (rev 01)
0000:00:07.1 IDE interface: Intel Corp. 82440MX EIDE Controller
0000:00:07.2 USB Controller: Intel Corp. 82440MX USB Universal Host Controller
0000:00:07.3 Bridge: Intel Corp. 82440MX Power Management Controller
0000:00:09.0 IRDA controller: Toshiba America Info Systems FIR Port Type-DO
0000:00:0b.0 CardBus bridge: Toshiba America Info Systems ToPIC95 PCI to Cardbus Bridge with ZV Support (rev 20)
0000:00:0b.1 CardBus bridge: Toshiba America Info Systems ToPIC95 PCI to Cardbus Bridge with ZV Support (rev 20)
0000:05:00.0 Network controller: Intersil Corporation Intersil ISL3890 [Prism GT/Prism Duette] (rev 01)

Have run the Multimedia Systems Selector and chosen ALSA, ESD also works. No others work. Selecting OSS actually makes the error beep go into slow motion, so I think that this does have something to do with totem maybe using OSS?

How can I force all apps to use ALSA or ESD?

Totem doesn't seem to have a prefernces menu that addresses this, so I guess it's editng a file time.

(I want to use Totem for video, if it was just music I'd stay with amarok).

---

