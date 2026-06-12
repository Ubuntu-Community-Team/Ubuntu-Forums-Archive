---
title: "GeForce 9800 GT freezes, 6600 TD doesn't"
date: 2009-02-09
forum: Multimedia Software
---

### Post by foto-alex on 2009-02-09
Hi everyone,

I'm having a hardware problem. I've just build a new PC with the following components:

MSI P43 Neo-F mobo
Intel E5200 dual-core CPU
2x A-Data 1 GB DDR2 800 MHz RAM
Gigabyte GeForce 9800 GT 512 MB

Freshly installed Kubuntu 8.10 boots and works OK until I install restricted drivers. With either nvidia-glx-177, nvidia-glx-180 or 180.22 drivers from nVidia's web site, the system locks up on boot, before he KDE login screen. I'm left with a blank screen (not a console) and nothing works, incl. Ctrl+Alt+anything, Caps Lock is not reacting etc.

I swapped KDM for XDM and after that, I booted successfully to Xfce4 through XDM. When I run KDE from Xfce by 'startkde', KDE starts and then locks after a while, most likely as a reaction to double-click.

Swapping the video card for my old 6600 TD fixed everything, that card runs smoothly with any drivers.

I've found a few posts with complains about blank screen with a 9800GT, but no solution for my case. [_Ubuntu Wiki also lists 9800GT as freezing._]("https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsNvidia") But a lot of people are running 9800GTs just fine.

I tried running Kubuntu in recovery mode and while booting, there's a lot of nVidia messages at one point. But I haven't found a valid boot log, maybe I'm looking at the wrong place.

Any idea what can I try?

Thanks a lot for suggestions.

---

### Post by norwoods on 2009-02-10
i used synaptic to install nvidia driver 180.27 from

[https://launchpad.net/~anders-kaseorg/+archive/ppa](https://launchpad.net/~anders-kaseorg/+archive/ppa)

and all seems good on a 9600gt. be sure to change the

apt sources.list entries
Display sources.list entries for:

drop down list box from jaunty to intrepid and follow the instructions.

---

### Post by foto-alex on 2009-02-11
Thanks norwoods. I'll check newer drivers. First I'll try to resurrect my old WinXP installation and try the video card there.

Anyway. Yesterday I switched from KDM to GDM and when I went back to KDM, my system locked up in the same way (with a 6600). Maybe the problem is related to KDM/KDE and no anything else.

Is there a way to debug this situation? Ie. search where and when the problem occurs?

---

### Post by dennymallow on 2009-02-11
You said you've installed the drivers from nVidia *website*, what about the drivers proposed by the restricted drivers manager?
I don't know if the situation can change switching to gnome, but I have the system you see in the signature, I installed the latest nvidia drivers only using the restricted drivers manager that Ubuntu presents after the first fresh boot, and until now nothing has broken, even with kernel upgrades...

EDIT: Sorry, the first two drivers you mentioned were the restricted manager ones, I didn't realize reading the first time!

---

### Post by foto-alex on 2009-02-11
I've now upgraded to nvidia's own 180.29 and it's the same. While in console mode, I've tried to switch to gdm and it's still the same. So far, I've only had luck with xdm+xfce. There must be some hardware conflict or whatever which I don't know how to track. Any ideas how to get to the root?

---

