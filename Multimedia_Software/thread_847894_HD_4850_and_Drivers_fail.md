---
title: "HD 4850 and Drivers fail"
date: 2008-07-03
forum: Multimedia Software
---

### Post by loki0347 on 2008-07-03
I just got an Asus HD 4850 card and have tried three times unsuccessfully to get them to work on 8.04 x86_64. What I have tried:

(as root)
apt-get install linux-restricted-modules-generic restricted-manager
apt-get install xorg-driver-fglrx

edited my xorg to contain Driver "fglrx" under Device

aticonfig --initial -f

and rebooted, ubuntu would try to use driver and fail, I have resorted to using the generic Vesa driver for now. I know that this whole process usually goes better with log files, but I don't know which ones to give. I apologize to all for the grammar, it's 12:04AM so brain is shutting down.

---

### Post by Melcar on 2008-07-03
You need to install the latest version (8.6).  Use either Envy or install it yourself.  The one in the repos (8.3) is too old to support the card.

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide")

---

### Post by loki0347 on 2008-07-03
Thanks for the help Melcar I'll have to see if that is what I needed.

---

