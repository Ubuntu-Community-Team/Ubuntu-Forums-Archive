---
title: "MythTV and Kworld DVB-T 210SE"
date: 2009-08-09
forum: Multimedia Software
---

### Post by qpegasus on 2009-08-09
I've been unable to get my Kworld DVB-T 210SE working with MythTV... or Kaffeine for that matter. I'm on Ubuntu 9.04 btw.

My card isnt listed at all in myth setup under DVB DTV, only under Analogue. After some searching I tried modprobe saa7134-dvb, which doesnt help.

I've also tried editing /etc/modprobe.d/options with the following -

options saa7134 card=114 tuner=17
install saa7134 /sbin/modprobe --ignore-install saa7134; /sbin/modprobe saa7134-alsa
options saa7134-alsa index=1

This DOES allow myth and kaffeine to detect it as a DVB-T card and it gives a signal strength reading when tuning... but myth still detects no channels and kaffeine only a few, but totally garbled. I think I have the tuner set wrong (perhaps NTSC instead of PAL?) but I dont know what else to try.

I really appreciate any help... I'm a total noob at this.

---

