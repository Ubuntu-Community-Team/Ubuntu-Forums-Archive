---
title: "Ubuntu 11.04 make Quake 3 no sound"
date: 2011-07-27
forum: Multimedia Software
---

### Post by pamanes7 on 2011-07-27
hi,
 
One of my favorite all time game is Quake 3, I have installed it on my Ubuntu 11.04 machine, but there is no sound at all. I've been playing around with the sound option in the q3aconfig.cfg file changing /dev/dsp to /dev/dsp0, /dev/dsp1, /dev/dsp2, etc and no luck.
 
(SORRY POST SHOULD BE **Ubuntu 11.04 make Quake 3 sound work** )
 
Doing a little research, found out that oss support has been removed from recent kernel versions ?
 
Then, I found this similar problem with a decent solution, not sure if it'll work thou...
 
Please share your thoughts on this , I would like to know if the solution below is the best to make the sound work in Quake 3,'cause I don't know how to revert things back to normal if this does not help.
 
**1.install oss-compat**
apt-get install oss-compat
 
**2. load these modules**
modprobe snd-pcm-oss
 
modprobe snd-mixer-oss
 
**This should create /dev/dsp for you. If not, then try this: **
 
mknod /dev/dsp c 14 3 && chmod 777 /dev/dsp
 
**3. make sure the modules load at boot-time**
gedit /etc/modules
 
**add the following:**
snd-pcm-oss
 
snd-mixer-oss
 
**4. Now here is the trick**
run this in a terminal:
aoss wxcam **(HERE I WOULD REPLACE wxcam with quake3)**
 
The program should load with a sound interface.
**5. Change your menu properties to make it permanent**
aoss wxcam **(HERE I WOULD REPLACE wxcam with quake3)**

---

### Post by metalfan_ on 2011-10-08
with what kernel did you accomplish this?

snd_pcm_oss       is not included in the kernel 2.6.38-11


i get these error at install time:
```

sudo apt-get install oss-compat
[sudo] password for julius: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  oss-compat
0 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
Need to get 2,818 B of archives.
After this operation, 61.4 kB of additional disk space will be used.
Get:1 http://de.archive.ubuntu.com/ubuntu/ natty/universe oss-compat all 0.0.4+nmu3 [2,818 B]
Fetched 2,818 B in 0s (9,113 B/s)
Selecting previously deselected package oss-compat.
(Reading database ... 196602 files and directories currently installed.)
Unpacking oss-compat (from .../oss-compat_0.0.4+nmu3_all.deb) ...
Setting up oss-compat (0.0.4+nmu3) ...
FATAL: Module snd_seq_oss not found.
FATAL: Module snd_mixer_oss not found.
FATAL: Module snd_pcm_oss not found.

```

---

