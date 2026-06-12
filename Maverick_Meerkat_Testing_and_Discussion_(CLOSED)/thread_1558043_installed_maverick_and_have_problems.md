---
title: "installed maverick and have problems"
date: 2010-08-21
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by terry_gardener on 2010-08-21
before anyone says it, i know it is development version and that makes it more fun because things break.
i have tested the last 2-3 ubuntu's at different stages on development.

i have 2 problems, 

one with nvidia driver when installed system wont boot, so removed nvidia driver and removed xorg.conf and computer started again.
xorg automatically had ignoreABI true in it.

second the lirc remote control doesn't work anymore.

when i install the lirc package and select windows media center remote (all) and reboot. 
normally it will work without issues.

this time it doesn't and when i try to start manually get message. 
```
find: ‘/sys/devices/virtual/rc/’: No such file or directory
 * Stopping remote control daemon(s): LIRC                               [fail] 
 * Loading LIRC modules                                                  [ OK ] 
 * Unable to load LIRC kernel modules. Verify your
 * selected kernel modules in /etc/lirc/hardware.conf
find: ‘/sys/devices/virtual/rc/’: No such file or directory

```

any ideas to fix either problem.

---

### Post by ktp on 2010-08-21
There is some buzz in these threads about nvidia card which might be helpful:

[http://ubuntuforums.org/showpost.php?p=9744665&postcount=159](http://ubuntuforums.org/showpost.php?p=9744665&postcount=159)
[http://ubuntuforums.org/showthread.php?t=1556297](http://ubuntuforums.org/showthread.php?t=1556297)

As for lirc, i would write up a bug if one doesn't exist yet.

---

