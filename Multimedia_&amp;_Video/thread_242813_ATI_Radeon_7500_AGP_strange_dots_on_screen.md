---
title: "ATI Radeon 7500 AGP strange dots on screen"
date: 2006-08-24
forum: Multimedia &amp; Video
---

### Post by pneaveill on 2006-08-24
Been working on this since April and I have not found any answers to this ATI Radeon 7500 AGP with the oft-mentioned, semi-random dots on certain buttons. What I am hoping for is help resolving this dot problem please.  kernel is 2.6.15-26-386  lspci readout says this: >  0000:00:00.0 Host bridge: Intel Corporation 82845 845 (Brookdale) Chipset Host Bridge (rev 03) 0000:00:01.0 PCI bridge: Intel Corporation 82845 845 (Brookdale) Chipset AGP Bridge (rev 03) 0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 12) 0000:00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 12) 0000:00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 (rev 12) 0000:00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 12)0000:00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus (rev 12) 0000:00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #2) (rev 12)0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV200 QW [Radeon 7500] 0000:02:08.0 Ethernet controller: Intel Corporation 82801BA/BAM/CA/CAM Ethernet Controller (rev 03) 0000:02:0c.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07) 0000:02:0c.1 Input device controller: Creative Labs SB Live! MIDI/Game Port (rev 07) 0000:02:0d.0 Communication controller: Conexant HSF 56k HSFi Modem (rev 01)   Then, to make matters worse, am not sure who/what/when/where /why this happened:  >  fglrxinfo display: :0.0  screen: 0 OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org) OpenGL renderer string: Mesa GLX Indirect OpenGL version string: 1.2 (1.5 Mesa 6.4.1)    Please be advised that I have googled many times and ways, searched pretty much everything I can think of trying to get this resolved.  Thanks in advance

---

### Post by Falados on 2006-08-24
I have this same problem with my Radeon 7500 (RV200)
Couldn't fix it, however... The dots go away if you mouse over the buttons that are affected... but that is not really a fix now is it :-(

---

### Post by pneaveill on 2006-08-24
> **Falados said:**
> I have this same problem with my Radeon 7500 (RV200)
Couldn't fix it, however... The dots go away if you mouse over the buttons that are affected... but that is not really a fix now is it :-(

 This is probably the one issue that I don't like since moving to linux.

---

### Post by funchords on 2006-08-24
1.  Click on System, Preferences, Theme
2.  Click on the Theme Details button
3.  On the Controls tab, choose LegacyHuman
4.  Click Close
5.  Click SaveTheme (I called mine MixedHuman)

The dots are gone.

---

### Post by pneaveill on 2006-08-25
> **funchords said:**
> 1.  Click on System, Preferences, Theme
2.  Click on the Theme Details button
3.  On the Controls tab, choose LegacyHuman
4.  Click Close
5.  Click SaveTheme (I called mine MixedHuman)

The dots are gone.
To be honest, I thought it was too easy of a fix. Happily I was wrong!! :D

---

### Post by RistoE on 2006-08-26
I had the same problems. Big thanks for fixing it :D

---

