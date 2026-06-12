---
title: "Getting linux-alsa-driver-modules-2.6.32-35-generic"
date: 2011-11-12
forum: Multimedia Software
---

### Post by antar on 2011-11-12
System info: Ubuntu 10.04, 64-bit

So in order to run a piece of Windows software, I had to update my Wine to the unstable branch (1.3), and in order to get Wine 1.3 working, I had to update alsa to 1.0.24, which required getting my alsa packages from the team-iquik repo.

Problem is, ever since upgrading, I can't record any audio.

Following the troubleshooting directions, I get to this point:

```
sudo apt-get linux-alsa-driver-modules-$(uname -r)
```

and get the following error:

```
E: Couldn't find package linux-alsa-driver-modules-2.6.32-35-generic
```

Googling the problem, I find out that basically, the team-iquik people have been slacking, and haven't released an updated package for the newest few kernels.

So I'm hoping someone can link me to directions as to how to obtain linux-alsa-driver-modules-2.6.32-35-generic through some other method. I'm not afraid to build from source.

Thanks in advance!

---

### Post by BicyclerBoy on 2011-11-12
Unless you have a real need for the later alsa kernel module, don't bother.

You can run the 1.0.24 lib/utils/tools/plugins with the 1.0.23 kernel module. This is a soln used by XBMC Live users for HDMI audio etc...

Could try this for kernel space:
```
https://launchpad.net/~ubuntu-audio-dev/+archive/ppa?field.series_filter=lucid

```

But I seem to remember that using this ppa, for kernel module, & iQuik ppa caused some dependencies problems (could have been with alsa plugins).

---

### Post by antar on 2011-11-13
The problem turned out to be something entirely different.

As per [http://www.linuxformat.com/forums/viewtopic.php?p=91180]("http://www.linuxformat.com/forums/viewtopic.php?p=91180"), I ran

```
sudo apt-get purge bluez-alsa
```

and now everything appears to be working.

---

### Post by BicyclerBoy on 2011-11-13
Glad you solved it..
If you need (slightly) later alsa modules without compiling, you can enable lucid-proposed & install linux-backport-alsa-modules-lucid-generic.
This package works okay with iQuik ppa.

---

### Post by Tronman on 2011-11-25
Hey folks,

Running into the exact same issue here. I need the latest linux-alsa-driver-modules package in order to get HDMI audio out working on my video card.

It seems to stop working every time my system update and I need to install the new package. Unfortunately, it doesn't seem to be available.

Does anyone know if it will be long before it gets up on the ubuntu-audio-dev repository? Any suggestions until then?

Thanks!

---

