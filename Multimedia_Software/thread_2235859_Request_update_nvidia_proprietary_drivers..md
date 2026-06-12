---
title: "Request: update nvidia proprietary drivers."
date: 2014-07-23
forum: Multimedia Software
---

### Post by silvio.alencar on 2014-07-23
Dear all who's got knowledge to do this,

please, update the nVidia proprietary driver deb packages.

Sadly my laptop's Nividia Optimus and I'm strongly dependent on nvidia-prime, nvidia-331 and their inter-dependencies and more automatized packages to solve the configurations with xrandr, dkms, initramfs and other members of the drill.

The most up-to-date package on official repositories holds the driver 331.38 officially released Jan, 13th and now (checked meanwhile posting) the drivers in a non-beta release are in the version 340.24; from 331.38 to 340.24 several GLX and EGL extensions are now supported and corrected, over and under-clock the GPUs and several other minor and major modifications that can be checked on readme available on official nVidia website.

Thanks

---

### Post by kc1di on 2014-07-23
If your looking for newer versions of nvidia drivers than the official release you can add the xorg-edgers ppa. it has currently 331.89 nividia driver.
but be warned this is not a stable release but only testing it may break your system. [here's their ppa page ]("http://www.ubuntuupdates.org/ppa/xorg-edgers")

---

### Post by silvio.alencar on 2014-07-23
Well, I was aware of the xorg-edgers drivers but they were conflicting and messing around with dependencies for quite some time in a way it became annoying (edgers mesa dependencies and gl wrappers with libmesagl from gnome-session-flashback). Well, it doesn't hurt taking a shot. In worst case circumstances I undo everything under terminal if I get no screen on X server ;p  Thanks for the tip!! I'll update with feedback editing this post.

---

### Post by Bucky Ball on 2014-07-23
Optimus? As far as I know, Bumblebee takes care of them. Wrong place to ask for third-party drivers to be improved/altered. Try emailing Nvidia.

---

### Post by Yellow Pasque on 2014-07-23
This is a user to user support forum, so this forum/site is the wrong place for such a request (file a bug instead).

As for PPA's, I would try something more focused than xorg-edgers, since xorg-edgers is aimed at providing all of the latest X components, which aren't necessary for a simple binary driver upgrade. [https://launchpad.net/~mamarley/+archive/ubuntu/nvidia](https://launchpad.net/~mamarley/+archive/ubuntu/nvidia)

> **Bucky Ball said:**
> Try emailing Nvidia.
Why? Nvidia doesn't control what version of Nvidia driver is in Ubuntu's repos.

---

### Post by silvio.alencar on 2014-07-23
Deal all, first of all thanks for the quick and clear reply.  Just sharing as promised (other users might have the same issue as I had). I'm using nVidia drivers provided by edgers ver. 340.24 and the FPS shifted from 4700~4900 to 9890~9970. I didn't test that much but I might assume at least a minor change happened. Well, at least I didn't receive any error message "X couldn't connect to screen server" like ;) I'll try some empiric rough benchmark with some apps and see the difference but I'm expecting the best already.   > **Bucky Ball said:**
> Optimus? As far as I know, Bumblebee takes care of them. Wrong place to ask for third-party drivers to be improved/altered. Try emailing Nvidia.  Hi Bucky Ball, thanks for replying. I wasn't asking for any upgrade or improvement on drivers provided by nVidia. The are some ppa releasers whose release unsupported packages with the nVidia proprietary driver plus scripts to configure dkms, ~/.xinitrc, xrandr, initramfs and other stuff that goes beyond my knowledge. Let's say they build a deb to do the same thing the binaries provided by nVidia should do (and don't).  I believe it was a misunderstanding.  Regarding Bumbleebee, I've used it before and they indeed do a good support but their alternative drivers for maximum performance on nVidia are (sorry for caps) FAR from the proprietary ones.  > **Temüjin said:**
> This is a user to user support forum, so this forum/site is the wrong place for such a request (file a bug instead).  As for PPA's, I would try something more focused than xorg-edgers, since xorg-edgers is aimed at providing all of the latest X components, which aren't necessary for a simple binary driver upgrade. [https://launchpad.net/~mamarley/+archive/ubuntu/nvidia](https://launchpad.net/~mamarley/+archive/ubuntu/nvidia)   Why? Nvidia doesn't control what version of Nvidia driver is in Ubuntu's repos.  OK Temüjin. Sorry for the inconvenience and btw thanks for the tip. This ppa indeed looks more focused than xorg-edgers. I'll try them right away.  Once again, thank you all and if the forum moderator wish to close the thread, it can be done. My doubts were cleared out and a person who's the same issue as mine (Optimus) can easily solve their problem following the tips here.  Regards!

---

### Post by Bucky Ball on 2014-07-23
We don't close them. Simply mark the thread as 'solved' by following the second link in my signature. Good luck.

---

