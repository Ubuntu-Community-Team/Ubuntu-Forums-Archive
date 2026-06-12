---
title: "How can I install/use i810 driver instead of intel?"
date: 2009-03-25
forum: Multimedia Software
---

### Post by roach of discord on 2009-03-25
How can I do this? The reason I ask, is because the "intel" driver for me, is absolutely horrible. I use an integrated intel graphics card. I've tried numerous xorg tweaks, turning off composite, etc..and I've had little luck. There are small speed-ups, but still nothing compared to the i810 driver. I reinstalled slackware 12.2 the other day, and it apparently has the i810 driver available still. I've been using it..and everything is perfect. No weird glitches..no slowness..none of it. 

I know it's not common for people to use the i810 driver anymore, but is it possible to use it with ubuntu? If so how? 

Thanks!

---

### Post by Vadi on 2009-03-25
Try installing the [xserver-xorg-video-i810]("apt:xserver-xorg-video-i810") package.

---

### Post by roach of discord on 2009-03-25
installing the package alone didn't work..however, I did get it to work :). Unfortunatly I had to downgrade my xorg to the gutsy version and put a lock on it, so it can't be upgraded.

It's a fix for now. Everything is perfect. I plan on getting an nvidia card soon enough..but this will help until then. With the intel driver things are almost unbareable...but with i810 it's fine. Weird.

---

### Post by Vadi on 2009-03-25
yeah. glad you have something showing atm

---

### Post by ERRDivideByZero on 2009-03-30
Can you give instructions on how to "downgrade" my xorg version. I am using intrepid (8.10) with gnome.

I am not new to linux, but I am new to ubuntu and debian based systems. I will say this, after using redhat based systems and the occasional slack distro... this is a welcome change with minimal things that I have had to do to get my system running properly. 

thanks in advance.
M~

---

### Post by Vadi on 2009-04-08
The only available version in ubuntu 8.10 is 7.4.

If you'd need to downgrade it, need to find an older package (maybe on packages.ubuntu.com for an older ubuntu version) or downgrade the whole ubuntu... both of which aren't really common to do.

Do you need to run some ancient drivers or something?

---

### Post by ERRDivideByZero on 2009-04-08
No, I am having issues getting 3d acceleration to work on my laptop... i know it sounds kinda dumb, but i would really like to be able to play a few games i know and love, that i have installed on linux ever since i have owned them.

Unreal Tournament, UT2k4, and Never Winter Nights.

I have heard about some updates to xorg and the kernel with the new jaunty release... i may be able to wait, if all else fails.

M~

---

### Post by Vadi on 2009-04-08
Ah yeah, downgrading wont help. Best to start a new thread so people can help you troubleshoot.

---

### Post by ERRDivideByZero on 2009-04-08
Well thank you for your time.
I greatly appreciate it.... and now to scan the forums again to see if anyone has anything like the problem i am having.... 

take care
M~

---

