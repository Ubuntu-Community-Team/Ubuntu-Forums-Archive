---
title: "Kernel compiled with module built-in works, but don't build /dev/dsp, so..."
date: 2006-08-08
forum: Multimedia &amp; Video
---

### Post by fberbert on 2006-08-08
So some app doesn't work, such as skype and avidemux, that requires /dev/dsp to link to sound device.

It looks like that my sound support compiled as part of kernel (<*>) doesn't create the dispositive inside /dev. The sound works perfect in Gnome apps like totem and console apps like mpg123. 

How can I burlate apps that understand that is no sound when /dev/dsp doesn't exist?

Thanks,
Fabio

---

### Post by fberbert on 2006-08-08
Uauuu, I found a solution. Posting here for future users with the same problem:


Create a char with mknod:

mknod /dev/dsp c 14 3

Give the right permissions:

chgrp audio /dev/dsp
chmod g+w /dev/dsp

Put it on /etc/init.d/bootmisc.sh to make it automaticaly in the boot.

---

