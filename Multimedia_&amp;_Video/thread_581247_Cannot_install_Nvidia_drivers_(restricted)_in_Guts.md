---
title: "Cannot install Nvidia drivers (restricted) in Gutsy"
date: 2007-10-19
forum: Multimedia &amp; Video
---

### Post by blop on 2007-10-19
Hi all i have just done a fresh install of Gutsy on my laptop after running Feisty successfully for a while. Very pleased to see the sound issue i had in Feisty which meant a manual hack of alsa.base has been solved with Gutsy...

but i cannot install the Nvidia drivers for my graphics card. I go to Restricted Drivers Manager and attempt to check the Nvidia accelearated graphics driver and run it but it fails with the message:

"This software source for the package

nvidia-glx-new

is not enabled"

which is a bit annoying....

any ideas?

cheers all! :)

---

### Post by Caalador on 2007-10-19
Goto System -> Administration -> Software Sources.

Make sure main/universe/restricted are selected (you can select multiverse too if you really want).

Open a terminal, then ->

```
sudo aptitude update
sudo aptitude install nvidia-glx-new
```

---

### Post by blop on 2007-10-19
thats ace thanks...

weird how in Feisty it just worked... without that change..

nevermind!

---

### Post by blop on 2007-10-19
thats ace thanks...

weird how in Feisty it just worked... without that change..

nevermind!

---

### Post by szulat on 2007-10-19
so you say Gutsy is supposed to handle nvidia automatically?
i upgraded from Feisty yesterday, but it failed to install the restricted driver :-(
after enabling it in the manager the xserver fails to run and dies with the message "Failed to initialize the NVIDIA kernel module!", yet lsmods shows the nvidia module.
perhaps this was because i haven't used the restricted manager in feisty? (i could not, because the driver version was too old for my card)

i solved the problem by installing the nvidia binary package again but this is ugly.

what should i do to switch from my current binary package configuration to ubuntu restricted manager driver?

---

### Post by ScorpionV on 2007-10-19
I had the same problem.  What I had to do is uncomment the restricted line in my sources.list file.  For some reason it said the installer commented it out because it failed to verify.  Once i uncommented it I could use the restricted drivers manager to install the nvidia driver.

---

### Post by szulat on 2007-10-19
this is something else, "restricted" software source is enabled (and it was not disabled by the upgrade process) and the restricted manager "thought" it did everything correctly (no messages about missing packages, everything was downloaded and installed). it just didn't work, perhaps because of some leftover files from my previous manual nvidia installation. i guess all i need is to "clean up" and retry with the ubuntu managed driver but i'm not sure how to do it.

---

### Post by Michael Matthews on 2007-10-30
At least Ubuntu nv driver now supports LCD resolution. Was using restricted driver in Fiesty though I had to jump through hoops to install as I remember. 
When trying to use NVIDIA restricted driver on AMD64 ubuntu it fails.
Using Restricted Driver dialog produced similar error

$ sudo aptitude install nvidia-glx-new


(Reading database ... 135043 files and directories currently installed.)
Removing libavahi-compat-howl0 ...
Removing libjack0.100.0-0 ...
Removing libquicktime0 ...
Removing libswfdec0.3 ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
(Reading database ... 134997 files and directories currently installed.)
Unpacking nvidia-glx-new (from .../nvidia-glx-new_100.14.19+2.6.22.4-14.9_amd64.deb) ...
dpkg-divert: `diversion of /usr/X11R6/lib32/libGL.so.1 to /usr/X11R6/lib32/nvidia/libGL.so.1.xlibmesa by nvidia-glx-new' clashes with `diversion of /usr/X11R6/lib32/libGL.so.1 to /usr/X11R6/lib32/nvidia/libGL.so.1.xlibmesa by nvidia-glx'
dpkg: error processing /var/cache/apt/archives/nvidia-glx-new_100.14.19+2.6.22.4-14.9_amd64.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/nvidia-glx-new_100.14.19+2.6.22.4-14.9_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:


Maybe bug report already exists...

---

### Post by No(R)way on 2007-10-30
Hi,,
Had a similar problem with an older nvidia card, my solution was to run ENVY, it is a program who installs video drivers, read more [here]("http://www.albertomilone.com/nvidia_scripts1.html")
Hope this helps

---

