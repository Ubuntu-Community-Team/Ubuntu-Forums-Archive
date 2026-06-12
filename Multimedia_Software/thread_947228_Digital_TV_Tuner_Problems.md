---
title: "Digital TV Tuner Problems"
date: 2008-10-14
forum: Multimedia Software
---

### Post by seanlano on 2008-10-14
Hello!
I have an Acer Aspire E700 PC, which came with Windows Vista. Under Vista I could use the Media Center to record from the digital tuner. I never did like this set-up, the proprietary Microsoft format means I can't edit, copy, or view on another machine the recorded videos. I have Ubuntu on a laptop, and decided to dual-boot it on this machine too. 

This is my problem: My TV Tuner card is not recognised by Ubuntu/MythTV. In Windoze the device manager says "Hauppauge WinTV-HVR 67xx" is the tuner device, however a Google search reveals very little info about this, and no tutorial I have found says how to install it. I myself know very little about it, there was no documentation with the computer about the tuner. (Typical!). I saw on some tutorial people running:
```
dmesg | grep card
```
and getting something about their card. I just get:
```
dmesg | grep card
[   20.081659] isapnp: Scanning for PnP cards...
[   20.472231] EISA: Detected 0 cards.
[   39.488185] saa7133[0]: subsystem: 0070:6700, board: UNKNOWN/GENERIC [card=0,autodetected]
[   39.821301] saa7133[0]/alsa: saa7133[0] at 0xefbff000 irq 23 registered as card -2

```
The bit that says: "subsystem: 0070:6700" seems to mention the 67xx in the tuners Windows name, so I'm guessing that Ubuntu can "see" the card in the motherboard. 
But now I am stuck. How, if at all, do I get this bloody card to work?

---

### Post by xc3RnbFO8P on 2008-10-14
You got this Tv card:
[http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1110]("http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1110")

---

