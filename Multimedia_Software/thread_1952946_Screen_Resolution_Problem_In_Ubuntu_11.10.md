---
title: "Screen Resolution Problem In Ubuntu 11.10"
date: 2012-04-05
forum: Multimedia Software
---

### Post by kenkencoronado on 2012-04-05
I installed Ubuntu 11.10 about two months ago and have noticed immediately that my screen resolution is not correct. Right now its default resolution is at 1080x768 and my laptop's native resolution is 1600x900. I am using a Gateway NV78 with an Intel Mobility 3 Series GM45. I installed the driver for my video card, but no luck. I am running the newest kernel and I've been reading that the driver can only be used on lower kernel versions. 

I'm a noobie at this stuff, so don't expect me to know everything that you tell me. Here is my xandr info:

xrandr: Failed to get size of gamma for output default
Screen 0: minimum 1024 x 768, current 1024 x 768, maximum 1600 x 900
default connected 1024x768+0+0 0mm x 0mm
   1024x768       76.0* 
   1600x900_60.00   59.9  

When I try to change my resolution up to 1600x900 I get this error message :

required virtual size does not fit available size: requested=(1600, 900), minimum=(1024, 768), maximum=(1024, 768)

I've tried changing the resolution manually through the terminal, but I get error messages on failing to get the size of the gamma output and what not. 

So how do I get my laptop's screen resolution on Ubuntu to its native resolution? Do I have to wait for Ubuntu 12.04 to be released by the end of this month? 


Please help!

---

### Post by carod on 2012-04-14
I am having the same problem.  I am trying to change my screen resolution from a depressing 800 x 600.  The monitor utility only shows that option and the monitor is shown as "unknown".  I tried the solution found on various wikis involving editing xrandr but get the "failed to get size of gamma for output default" message.  I have a Toshiba NB525.  Intel® Graphics Media Accelerator 3600 Series- Integrated.  I am assuming I have to convince ubuntu to recognize my monitor somehow? thanks for any (explained in small words) help for a newbie.

---

### Post by BicyclerBoy on 2012-04-14
@carod
I don't think the latest atom CPU/GPU combo cedar-trail has kernel/driver support yet..at least not in mainline..The latest atom GPU is another closed secret PowerVR device bit like GMA500 poulsbo.

edit:
cedar-trail/cedar-view is already made obsolete by intel valley-view (which is not PowerVR) which means open source support from Intel..
This could mean that GMA500 & GMA3600 (atom 2600) never ever get full linux support.

@kenken
How did you install this video driver?
The correct driver is included with *buntu (i915)..but it sounds like the VESA driver is being loaded. (max 1024x768)

glxinfo | grep OpenGL
post your /var/log/Xorg.0.log files..

---

### Post by rhss6-2011 on 2012-04-14
Hello there,
I made a guide for such issues and you can find it here:

[http://forums.debian.net/viewtopic.php?f=16&t=78330](http://forums.debian.net/viewtopic.php?f=16&t=78330)

Also, at the very bottom of the post is a list of resolutions that computers recognize...

Hope it helps!

---

### Post by carod on 2012-04-14
[I]I don't think the latest atom CPU/GPU combo cedar-trail has  kernel/driver support yet..at least not in mainline..The latest atom GPU  is another closed secret PowerVR device bit like GMA500 poulsbo.

edit:[/I] [I]
cedar-trail/cedar-view is already made obsolete by intel valley-view  (which is not PowerVR) which means open source support from Intel..
This could mean that GMA500 & GMA3600 (atom 2600) never ever get full linux support.

[/I]Thanks for your reply (which was mostly in words I could understand).  I guess this means I am out of luck.  It seems like meego has come up with a OS that works with cedar-trail, but I am reluctant to switch to that since I am unfamiliar with it.  I *really* dislike Windows, so I guess I will just have to put up with 800 x 600 unless a later version of Ubuntu integrates the meego solution.

---

### Post by BicyclerBoy on 2012-04-15
I only have a passing interest in Intel GPUs..
Meego uses the closed proprietary PowerVR driver. Intel can not open source this.
People hope/hoped that this meego driver could be pinched & used with other linux. This was the hope for pousbo..

AIUI This has not been the instant success..This could be old incorrect news now..but the mythical Meego driver turned out to be an old version with incomplete h/w acceleration.

I would sell/give any GMA500/GMA3600 netbook/laptop to a windows user & buy the Intel valley-view. Indications are the performance (battery life etc) are improved.

---

