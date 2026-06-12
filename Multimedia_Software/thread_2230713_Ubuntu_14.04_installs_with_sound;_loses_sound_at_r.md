---
title: "Ubuntu 14.04 installs with sound; loses sound at reboot"
date: 2014-06-20
forum: Multimedia Software
---

### Post by Resisty on 2014-06-20
Hello,

When I install a computer with Ubuntu 14.04, it comes up just fine and is able to play sound (youtube, sound preferences test, etc). However, after the first reboot, no soundcard is detected and all the usual tests fail.

alsa-info: [http://pastebin.com/WvJdQ9vz](http://pastebin.com/WvJdQ9vz)

Thanks very much for any help!

---

### Post by soodvarun78 on 2014-06-21
Hi,

It looks like you alsa driver might not be getting installed at reboot.
In file /lib/modules/<your kerenl version>modules.pcimap
Check whether vendorid:deviceid --> 8086:284b is there for under snd-hda-intel module.


Regards
Varun Sood

---

