---
title: "Upgraded NVidia proprietary driver available"
date: 2011-04-12
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Harry33 on 2011-04-12
There is a new NVidia proprietary driver available.
The version is nvidia-current_270.41.03
and
you can go download it either from
X Updates PPA
or
Xorg-edgers PPA

There is also a new nvidia-settings package.

> Changelog
nvidia-graphics-drivers (270.41.03-0ubuntu1~xup) natty; urgency=low

  * New upstream release.
  * Fixed a bug causing the X server to hang every 49.7 days on
    32-bit platforms.
  * Added support for the following GPUs:
  * GeForce GT 520
  * GeForce GT 525M
  * GeForce GT 520M
  * GeForce GT 445M
  * GeForce GT 530
  * GeForce 405
  * GeForce GTX 590
  * GeForce GTX 550 Ti
  * GeForce GT 420
  * GeForce GT 440
  * GeForce GTX 470M
  * GeForce GTX 485M
  * GeForce GT 550M
  * GeForce GT 555M
  * NVS 4200M
  * Quadro 1000M
  * Quadro 2000M
  * Quadro 2000 D
  * Quadro 400
 -- Robert Hooker <email address hidden>   Mon, 11 Apr 2011 16:17:50 -0400

---

### Post by farlander762 on 2011-04-17
I'm running Lucid 64 bit.  Is there a good driver for a GT 420 card that is available now?  I'm not finding any (even direct from nVidia) and it leaves me in single monitor dum-dum mode...

---

### Post by cariboo on 2011-04-17
Nvidia-current is always the latest driver available in the repositories, currently the version number is 270.41.03

---

### Post by Harry33 on 2011-04-18
> **farlander762 said:**
> I'm running Lucid 64 bit.  Is there a good driver for a GT 420 card that is available now?  I'm not finding any (even direct from nVidia) and it leaves me in single monitor dum-dum mode...

The driver Cariboo just mentioned (nvidia-current_270.41.03), available also from Natty repos, is the only one working with Nvidia GT 420.

---

### Post by farlander762 on 2011-04-18
I enabled the PPA (X Updates PPA) that you mentioned above as well as turned on every available check box in "software sources" and that driver version still doesn't show up.  Newest Synaptic shows is 270.29-0.  I'm pretty Linux stupid still so I'm probably forgetting something...

Any ideas?
Thanks,

---

### Post by dino99 on 2011-04-18
> **farlander762 said:**
> I enabled the PPA (X Updates PPA) that you mentioned above as well as turned on every available check box in "software sources" and that driver version still doesn't show up.  Newest Synaptic shows is 270.29-0.  I'm pretty Linux stupid still so I'm probably forgetting something...

Any ideas?
Thanks,

you should have not set it correctly

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates?field.series_filter=natty](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates?field.series_filter=natty)

---

### Post by Harry33 on 2011-04-18
> **farlander762 said:**
> I enabled the PPA (X Updates PPA) that you mentioned above as well as turned on every available check box in "software sources" and that driver version still doesn't show up.  Newest Synaptic shows is 270.29-0.  I'm pretty Linux stupid still so I'm probably forgetting something...
Any ideas?
Thanks,

You are not using Natty Narwhal (11.04-beta2), you are using Lucid Lynx (10.04 LTS).
This is the Natty Development Forum.

---

### Post by Harry33 on 2011-04-18
The Natty nvidia-current_270.41.03 package depends on xorg-video-abi-10.
That means it depends on xserver 1.10 too.

---

