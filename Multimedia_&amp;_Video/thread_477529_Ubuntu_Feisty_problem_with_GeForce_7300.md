---
title: "Ubuntu Feisty problem with GeForce 7300"
date: 2007-06-18
forum: Multimedia &amp; Video
---

### Post by Verminoz on 2007-06-18
Hello there,
I have Kubuntu Feisty and I have a NVIDIA GeForce 7300 GS graphics card. I am trying to add 3D Acceleration to it and I simply can't make it.
I tried to do it manually, I tried the Ubuntu wiki way, I tried the Ubuntu Guide way (pretty similar), I tried the envy scripts, I tried the scripts from NVIDIAs website but NOTHING worked!!! After every installation, when I restart my PC Kubuntu boots but the X server simply won't start. I've tried playing around with xorg.conf but nothing worked there either. A blank black screen appears with a useless cursor at the top left! Not even a command line!
I also attempted using the legacy and the new drivers although my graphics card is supported by the standard drivers and that of course didn't work either!

I could really use some help here! I am attaching the xorg.0.log file plus the working and the not-working versions of xorg.conf. :( :( :(

---

### Post by stchman on 2007-06-18
> **Verminoz said:**
> Hello there,
I have Kubuntu Feisty and I have a NVIDIA GeForce 7300 GS graphics card. I am trying to add 3D Acceleration to it and I simply can't make it.
I tried to do it manually, I tried the Ubuntu wiki way, I tried the Ubuntu Guide way (pretty similar), I tried the envy scripts, I tried the scripts from NVIDIAs website but NOTHING worked!!! After every installation, when I restart my PC Kubuntu boots but the X server simply won't start. I've tried playing around with xorg.conf but nothing worked there either. A blank black screen appears with a useless cursor at the top left! Not even a command line!
I also attempted using the legacy and the new drivers although my graphics card is supported by the standard drivers and that of course didn't work either!

I could really use some help here! I am attaching the xorg.0.log file plus the working and the not-working versions of xorg.conf. :( :( :(

Enable the restricted drivers for nvidia cards.  Worked for my PCs with nvidia cards.

---

### Post by Verminoz on 2007-06-19
I tried that after you said but it didn't work. That's pretty logical. The restricted drivers manager simply installs the nvidia-glx driver and enables it...more or less nothing different than what I did through other ways.

Thank you for your help anyway! Any other suggestions?

---

### Post by Verminoz on 2007-06-20
anyone?

---

