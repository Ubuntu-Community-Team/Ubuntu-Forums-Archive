---
title: "ERROR: Module fglrx does not exist in /proc/modules"
date: 2007-12-07
forum: Multimedia &amp; Video
---

### Post by Mysticle31 on 2007-12-07
I have been trying to get a linux distro going for DAYS without some kind of problem.

This one is really getting annoying.  I've reformatted and installed kubuntu many times becouse I mess things up somehow.  I've gotten very close to a usable desktop with everything I need (burning, web, mythTV..etc)  Sometimes when I install Kubuntu installing fglrx goes very well with envy or the restricted manager.  Sometimes not.  My solution up to now has been just to reinstall again and again until it works.  However, I want to fix this.  This is the problem.

ERROR: Module fglrx does not exist in /proc/modules
FATAL: Error inserting fglrx (/lib/modules/2.6.22-14-generic/misc/fglrx.ko): Operation not permitted

My Fglrxinfo is still reporting Mesa.

Yes FGLRX is blacklisted, yes I have commented out "#install fglrx /sbin/lrm-video fglrx $CMDLINE_OPTS" in "/etc/modprobe.d/lrm-video", Yes my xorg.conf says fglrx in the driver section. I'm still reporting Mesa.

The funny thing is that the restricted drivers manager will say that the restricted drivers are in use, but fglrxinfo does not.

---

### Post by Mysticle31 on 2007-12-07
All in all when I retry in the same installation of Kubuntu I get:

ERROR: Module fglrx does not exist in /proc/modules



I just tried shutting down X and running this.

sudo rmmod fglrx

but it says ERROR: module FGLRX is in use.

so I go here:

cd /lib/modules/2.6.22-14-generic/misc

lo and behold fglrx.ko exists in here.

I also went to /proc and found modules, which is a text file.
Inside I searched for fglrx and found

fglrx 1489004 3 - Live 0xf8d4b000 (P)

---

### Post by Mysticle31 on 2007-12-07
Someone has to know something....

ERROR: Module fglrx does not exist in /proc/modules
FATAL: Error inserting fglrx (/lib/modules/2.6.22-14-generic/misc/fglrx.ko): Operation not permitted

or just 

ERROR: Module fglrx does not exist in /proc/modules

---

### Post by Mysticle31 on 2007-12-08
Here is part of my Xorg.0.log.  Can someone who knows what their doing tell me what's going on?:confused:

---

### Post by Yellow Pasque on 2007-12-08
Why are you trying to load a module that you've blacklisted? :?

---

