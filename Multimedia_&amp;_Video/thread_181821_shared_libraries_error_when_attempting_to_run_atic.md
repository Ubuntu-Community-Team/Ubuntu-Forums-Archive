---
title: "shared libraries error when attempting to run aticonfig"
date: 2006-05-24
forum: Multimedia &amp; Video
---

### Post by Rippy on 2006-05-24
I have a Radeon 9250, 128mb cache, and I was trying to get the ATI linux drivers to work for it. It installed ok, however when I attempt to use
```
sudo aticonfig --initial
```
I get the following error: "aticonfig: error while loading shared libraries: libfglrx_pp.so.1: cannot open shared object file: No such file or directory"

Is there something I've forgotten to do, or install, that would cause this? I need help! If I can get the display drivers working right, my ubuntu will be complete >_>

Thanks,

-Paul

---

### Post by Rippy on 2006-05-26
This thread has fallen off the first page, so I'm assuming I'm allowed to bump it?

---

### Post by keller.baum on 2006-05-26
im having the same problem and have had no luck solving it

---

### Post by Rippy on 2006-05-27
Ah, I see. Well, I suppose I don't really NEED it right now. I was only gonna install UT2004 as an experiment, and probly not play it that much. :P

---

### Post by dport113 on 2006-05-29
Same problem here, no luck according to #ubuntu-devel its contained in xorg-driver-fglrx, its not.

Edit:
avid@mobile:/usr/X11R6/lib$ dir *fglrx*
libfglrx_dm.a  libfglrx_dm.so.1.0  libfglrx_gamma.a  libfglrx_gamma.so.1  libfglrx_gamma.so.1.0  libfglrx_pp.a  libfglrx_pp.so.1  libfglrx_pp.so.1.0

fglrx:
libGL.so.1.2.xlibmesa  libGL.so.1.xlibmesa
david@mobile:/usr/X11R6/lib$ sudo aticonfig
aticonfig: error while loading shared libraries: libfglrx_pp.so.1: cannot open shared object file: No such file or directory
david@mobile:/usr/X11R6/lib$
avid@mobile:/usr/X11R6/lib$ dir *fglrx*
libfglrx_dm.a  libfglrx_dm.so.1.0  libfglrx_gamma.a  libfglrx_gamma.so.1  libfglrx_gamma.so.1.0  libfglrx_pp.a  libfglrx_pp.so.1  libfglrx_pp.so.1.0

fglrx:
libGL.so.1.2.xlibmesa  libGL.so.1.xlibmesa
david@mobile:/usr/X11R6/lib$ sudo aticonfig
aticonfig: error while loading shared libraries: libfglrx_pp.so.1: cannot open shared object file: No such file or directory
david@mobile:/usr/X11R6/lib$

Edit
copying libfglrx_pp.so.1 to /usr/lib solves this.

---

### Post by Punio4 on 2006-07-13
Same problem here after reinstaling Ubuntu... Funny thing is it worked the first time i installed ubuntu >_<

---

### Post by RJARRRPCGP on 2006-07-13
> **Rippy said:**
> I have a Radeon 9250, 128mb cache, and I was trying to get the ATI linux drivers to work for it. It installed ok, however when I attempt to use
```
sudo aticonfig --initial
```
I get the following error: "aticonfig: error while loading shared libraries: libfglrx_pp.so.1: cannot open shared object file: No such file or directory"

Is there something I've forgotten to do, or install, that would cause this? I need help! If I can get the display drivers working right, my ubuntu will be complete >_>

Thanks,

-Paul

This appears to be the classic missing dependency problem. Please look for the libfglrx 1 (or similar) package in Synaptic and select it for installation.

---

### Post by ronoc on 2006-08-07
I have had this same issue and was not a dependency problem. 
The path from where the aticonfig was being executed did not have the lib... in it's path. A work mate of mine fixed this but I can't remember what he did. I suppose he made the path to the lib visible from where the aticonfig is being executed from. 
aticonfig is in /usr/bin and the lib is in /usr/lib.
Anyone know what would fix this problem
C

C

---

### Post by BigB-84 on 2006-08-07
Hai,

i had the same problem. I deleted my earlyer solution because a friend explained me how to do it right.

You start the ATI-driver with ./atidriver.run --listpkg

This will give you a list of supported distibutions.

Now you run ./atidriver --buildpkg /Ubuntu/6.06

This takes some time but it will be created 5 deb-packages you can easily install afterwards with dpkg -i name.deb

The package xor-driver-fglrx includes the missing libfglrx_pp.so.1

BigB-84

---

