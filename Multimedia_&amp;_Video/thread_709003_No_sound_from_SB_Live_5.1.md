---
title: "No sound from SB Live 5.1"
date: 2008-02-27
forum: Multimedia &amp; Video
---

### Post by 240r on 2008-02-27
I have tried the steps outlined in the comprehensive guide, going as far as saving the changes in module but still no sound. I believe my onboard sound is on but not sure. I am not sure how to check in BIOS or how to modify it.

I am using Kubuntu 7.1 and below is my output of lspci -v

00:05.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
        Subsystem: ASUSTeK Computer Inc. CMI8738 6ch-MX
        Flags: bus master, stepping, medium devsel, latency 32, IRQ 19
        I/O ports at d800 [size=256]
        Capabilities: [c0] Power Management version 2

00:0e.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
        Subsystem: Creative Labs SBLive! Player 5.1
        Flags: bus master, medium devsel, latency 32, IRQ 19
        I/O ports at b800 [size=32]
        Capabilities: [dc] Power Management version 1

00:0e.1 Input device controller: Creative Labs SB Live! Game Port (rev 07)
        Subsystem: Creative Labs Gameport Joystick
        Flags: bus master, medium devsel, latency 32
        I/O ports at b400 [size=8]
        Capabilities: [dc] Power Management version 1

---

### Post by Placified on 2008-02-27
When I installed the KDE desktop, for some reason my sound quit.  what I did to rectify the situation was to right click on the sound icon go to preferences and select the proper device to manipulate.  This may not be your problem but I hope it helps.

---

### Post by 240r on 2008-02-27
Thanks for the note. I didn't notice it before. Alas, it did not help.

---

