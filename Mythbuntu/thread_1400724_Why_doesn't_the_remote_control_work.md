---
title: "Why doesn't the remote control work?"
date: 2010-02-07
forum: Mythbuntu
---

### Post by sourcefinder on 2010-02-07
I bought an serial IR transmitter from leibtech ([www.irblaster.info]("http://www.irblaster.info")) and followed the instructions on [http://ubuntuforums.org/showthread.php?t=742672&highlight=lirc&page=2](http://ubuntuforums.org/showthread.php?t=742672&highlight=lirc&page=2). I reinstalled, experimented and reinstalled again, but nothing seems to work. I tested the IR blaster with a battery; it works. I've got two remotes to choose between: an Yamaha RAV302 and an Pinnacle remote from the PInnacle PCTV Sat receiver I installed in my system.
 
Does anyone know what I am doing wrong (exept of course the fact that I didn't use the search option in this forum good enough?). Thanks in advance!
 
PS: I use Mythbuntu 9.10 32-bits (tested on two PC's, so the COM-port can't be the problem...).

---

### Post by azmyth on 2010-02-07
Please post your hardware.conf and the lircd.conf file for the codes you're trying to blast.

Also try to blast via the command line ./change_chan_script 20

Also what does dmesg | grep lirc give you.

---

