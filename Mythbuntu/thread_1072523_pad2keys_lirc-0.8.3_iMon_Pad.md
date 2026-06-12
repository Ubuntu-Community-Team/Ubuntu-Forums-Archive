---
title: "pad2keys lirc-0.8.3 iMon Pad"
date: 2009-02-17
forum: Mythbuntu
---

### Post by marcos1974 on 2009-02-17
hello everybody

first of all let me thank you for all the good hints, that I found until now in this forum.

a little introduction of myself...
I've been using ubuntu (8.04 and now 8.10) on my private notebook for about one year almost.
now I have decided to move my htpc from windows media center to mythbuntu.
installation worked fine and now I'm trying to configure it.

one of the things I want to configure is the imon pad.
out of the box some keys work but other doesn't.
I've searching for few hours in the forum and found something abou pad2keys patch
I'm running lirc-0.8.3 and wanted to patch it with pad2keys patch
so far I've done the following steps:
- download lirc-0.8.3-imon-pad2keys.patch
- download lirc-0.8.3.tar.bz2
- cd lirc-0.8.3
- patch -pl <../lirc-0.8.3-imon-pad2keys.patch
- ./setup.sh
- choosed the rigth remote (imon pad)
after the application has done his job I get a message:
run make and make install

running make I get some erros (see attached file) 

my questions are now:
has anyone manage to do it succesfully?
if yes could you please post the steps you followed?

I would really appreciate if someone posts some hints...

regards,
marcos

---

### Post by skg on 2009-02-17
The patch is allready in lirc for 8.10

[https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/153184/comments/11](https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/153184/comments/11)

I use it succesfully on my system. You only need to activate it.

> pad2keys function can be (de-)activated via a module-parameter. Deactivated by default!!  Add "options lirc_imon pad2keys_active=1" to /etc/modprobe.conf (or where ever you like/have to) to activate the pad2keys translation.

Quote from: [http://brakemeier.de/electronics/vdr/lirc-imon.html](http://brakemeier.de/electronics/vdr/lirc-imon.html)

Regards
Stefan

---

### Post by marcos1974 on 2009-02-18
hi stefan

thanks for your hint...

I have an additional question
the file /etc/modprobe.conf should it already be on the system?

I didn't find any file named modprobe.conf on my system.
can you help me on this?

regards,
marcos

---

