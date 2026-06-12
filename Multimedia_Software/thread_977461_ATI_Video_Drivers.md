---
title: "ATI Video Drivers"
date: 2008-11-10
forum: Multimedia Software
---

### Post by rtubes on 2008-11-10
I just installed Ubuntu 8.04 on an old Dell Insiron 8000 laptop computer and would like to run it at a higher video resolution than the default 800 x 600.

I am a newbie to Ubuntu and would like to know how to download and install the drivers for an ATi Mobility M4 AGP 4X video card or generic card that would work and then choose a higher resolution.

Any help would be greatly appreciated.

---

### Post by Bablefish on 2008-11-10
You may want to rethink installing those drivers. I admit some had no problem, but you might not be so lucky....like me. When I tried to install those same drivers, it crashed my video drivers and I got nothing on my screen. I was just lucky to get it up and running again. But I still have to reinstall my OS...so be warned.

---

### Post by Skripka on 2008-11-10
Odds are you can go into Add/Remove or Synaptic and click off check boxes to install the drivers, and then go into "Hardware drivers" to activate them, then reboot.  Doing things this way I've never killed xorg on a driver install.....double check if your card is supported (odds are it is)


The other option being to download ATi's .run driver installer file....BUT......

Last time I tried an ATi card and the *.run file from ATi, the ATi *.run file would not even RUN under *buntu linux (they used bizzaro compiling commands that *buntu does not have, last I knew).....those cats at ATi have finally learned how to write decent Windows drivers, but they still make linux drivers like the proverbial room full of monkeys typing at GNU emacs.

---

