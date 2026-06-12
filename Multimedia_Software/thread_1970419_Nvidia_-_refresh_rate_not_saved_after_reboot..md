---
title: "Nvidia - refresh rate not saved after reboot."
date: 2012-05-01
forum: Multimedia Software
---

### Post by ppparadox on 2012-05-01
Hi, i can't get the refresh rate to stay after a reboot.
I have to open the nvidia-settings control panel every time and switch to 60Hz.
I am using two monitors at the moment.
Tried running nvidia-settings as root, still no luck.
```

AMD Athlon 64 X2 6000+
3GB DDR2 800
Asus m4n78 pro (motherboard)
Ge Force GTX 550 Ti
Ubuntu 12.04 x86
Driver version: 295.40
Xserver: 1.11.3
NV-CONTROL version 1.27

```
My xorg.conf:

---

### Post by ppparadox on 2012-05-04
Up!

---

### Post by solitaire on 2012-05-04
> **ppparadox said:**
> Up!
Can't help you 

I've also been having problems with Nvidia-Settings with twin monitors since I upgraded to 12.04

For some reason Nvidia-Settings does not read it's config file when it starts!

---

### Post by ppparadox on 2012-05-05
Is there already a bug report for this?
Do you think we might file one?
But... against which package? :confused:

---

### Post by solitaire on 2012-05-05
report your bug here:
[https://bugs.launchpad.net/ubuntu/+source/nvidia-settings](https://bugs.launchpad.net/ubuntu/+source/nvidia-settings)
or here:
[https://bugs.launchpad.net/nvidia-drivers-ubuntu](https://bugs.launchpad.net/nvidia-drivers-ubuntu)

i think...

---

### Post by ppparadox on 2012-05-05
This should be the one: [https://bugs.launchpad.net/ubuntu/+source/nvidia-settings/+bug/634648](https://bugs.launchpad.net/ubuntu/+source/nvidia-settings/+bug/634648)

---

### Post by ppparadox on 2012-05-06
Well there seems to be many reported bugs which are just duplicate s because the real problem here is the damn nvidia-settings won't save your settings.

---

### Post by solitaire on 2012-05-06
> **ppparadox said:**
> Well there seems to be many reported bugs which are just duplicate s because the real problem here is the damn nvidia-settings won't save your settings.

It's a problem with "Xinerama" and "RandR" i think...

If you turn "Xinerama" off in Nvidia-settings does it save the settings?

---

### Post by ppparadox on 2012-05-07
Neither "Xinerama" nor "RandR" are even mentioned in my nvidia-settings. :-k

---

### Post by mightymouse2045 on 2012-05-27
> **solitaire said:**
> It's a problem with "Xinerama" and "RandR" i think...

If you turn "Xinerama" off in Nvidia-settings does it save the settings?


Xinerama off has no effect with this problem - If I use disper to change the resolution at startup (which is basically using xrandr as a backend), it creates a new mode on the fly and changes it to the max reported resolution (and refresh). When I check the settings it has just changed it to 50Hz still if I have the script run right at login.

If however I delay the switch by sleeping the disper command until my desktop appears it creates a new mode with 60Hz refresh.

So somewhere in the 7 second delay nvidia-settings and it's metamodes comes into play and it correctly detects the max setting, and if I open nvidia-settings it has selected the 1st metamode profile 1-"1920x1080_60 +0+0".

xrandr by itself lists 1920x1080 50 as the highest, which nvidia picks up as metamode 9-"1920x1080_50i +0+0"

So I think you are correct that it is a problem with RANDR. I didn't have this problem in Ubuntu 11.10, even when I did an upgrade to 12.04. However due to other issues I reinstalled 12.04 and straight off the bat I have had this issue. So WTF to that one!

UPDATE!

After updating to 302.07 beta drivers this is now fixed - with the default xorg.conf created during install

---

### Post by orange2k on 2012-05-28
I think this is the correct bug report for this problem:

[https://bugs.launchpad.net/ubuntu/+source/nvidia-settings/+bug/949071](https://bugs.launchpad.net/ubuntu/+source/nvidia-settings/+bug/949071)

There seems to be a workaround described later in the comment nr. 9...

---

