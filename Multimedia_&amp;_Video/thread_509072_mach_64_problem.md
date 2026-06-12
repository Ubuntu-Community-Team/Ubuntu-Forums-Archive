---
title: "mach 64 problem"
date: 2007-07-25
forum: Multimedia &amp; Video
---

### Post by ujack_tivation on 2007-07-25
I have an ATI Technologies Inc Rage Mobility P/M A GP 2x (rev 64) and am using Dapper. Up until yesterday I had direct rendering, but now I get. 

ujack@ujack-laptop:~$ glxinfo | grep "direct"
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect

and 

ujack@ujack-laptop:~$ sudo modprobe -v mach64
Password:
insmod /lib/modules/2.6.15-28-386/kernel/drivers/char/drm/mach64.ko
FATAL: Error inserting mach64 (/lib/modules/2.6.15-28-386/kernel/drivers/char/drm/mach64.ko): Unknown symbol in module, or unknown parameter (see dmesg)

Should I just ditch my current mach 64 driver and repeat the install or is there an easier way to fix this/are there other possible problems.

---

### Post by dougfractal on 2007-07-27
[http://ubuntuforums.org/showpost.php?p=3084274&postcount=33](http://ubuntuforums.org/showpost.php?p=3084274&postcount=33)

sudo apt-get install linux-headers-386 build-essential
before running (feisty) script,  though should work with dapper. 

Problems
Unsupported script with no updates.

---

