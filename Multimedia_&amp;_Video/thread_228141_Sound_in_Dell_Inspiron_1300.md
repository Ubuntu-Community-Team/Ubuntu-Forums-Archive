---
title: "Sound in Dell Inspiron 1300"
date: 2006-08-02
forum: Multimedia &amp; Video
---

### Post by steveob on 2006-08-02
Have read all the posts I can find so apokogies if I have m9issed the one!

Bought the Dell a few weeks ago and installed kubuntu from the live cd as a dual boot with windows.  At the same time installed it on an old desktop.  Sound on the old desktop is fine using a Creative SB Live! Value card with emu10k1 emulation.

So far on the Dell, nothing.  Have followed the instructions in LordRaiden's sticky with no success whatsoever, even though the soundcard (hda-intel) is listed and the module appears to be loaded.

In KsCD the default was set to arts rather than alsa so changed that.  Made sure that kmix was not muted nor alsamixer.

Has anyone got sound from an Inspiron 1300 (B150 in USA?)?

Any replies/suggestions/assistance greatly appreciated.

---

### Post by gholen on 2006-08-08
Yes, I do got sound working.
first, have you done the update and upgrade thing?

sudo apt-get update
sudo apt-get upgrade

For me, it started working with the kernel 2.6.15-19 i think.... try that.

---

