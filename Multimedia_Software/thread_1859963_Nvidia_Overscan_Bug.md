---
title: "Nvidia Overscan Bug"
date: 2011-10-14
forum: Multimedia Software
---

### Post by solitaire on 2011-10-14
I'm running 10.10
Zotac atom 330 Nvidia ION board
Just upgraded my Nvidia drivers to 285.05.09

My monitor has an overscan so i usually use the Nvidia "Overscan Compensation" to fix this. (value of the compensation is 80)

But in this version of the drivers when ever I go above 2 the bottom 3rd of the screen goes black. If I keep increasing the slider more and more of the screen goes black. till their is only a small section of the screen left (thiner than the top bar). This only happens in this version of the Nvidia drivers!

Anyone else had the same issue!?

---

### Post by solitaire on 2011-10-18
*bump*
Anyone?

---

### Post by CosineQuaNon on 2011-11-06
I'm having a similar problem with my NVIDIA Ion-based custom HTPC, but with Ubuntu/Xubuntu 11.10 and Arch. In Ubuntu the overscan option in the NVIDIA driver intermittently disappeared upon restart of X11, with most of the screen going black at times, with only a small strip at the top remaining as is.

In Arch, the overscan option intermittently disappears as well. When it *is* there and I try to change the setting, about 2/3rds of the screen goes black. I've checked the logs and haven't been able to find anything.

Do you have a DLP (rear projection) TV? I have two TVs, and this issue only shows up on my DLP TV (granted, I don't have overscan issues with my LCD, so I don't know if it would show up if I were to try changing the overscan setting).

---

### Post by Flashyman on 2011-11-07
I don't get what you're trying to say, but maybe this will help, I'm also not sure if this will change anything, anyway:

open terminal:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bup
sudo rm /etc/X11/xorg.conf
sudo nvidia-xconfig
```
This should give you a new xorg.conf file and might fix the problem.

I'm new to ubuntu, quiet new to linux and just trying to help.

---

### Post by solitaire on 2011-11-09
It's when you change the "overscan" value by 1 or 2 i loose HALF the screen!
I have a LCD TV

It's not a problem with the Xorg.conf it's the Nvidia drivers as older drivers are fine. 

i've not tried the 3rd November drivers (275.36) yet...

---

