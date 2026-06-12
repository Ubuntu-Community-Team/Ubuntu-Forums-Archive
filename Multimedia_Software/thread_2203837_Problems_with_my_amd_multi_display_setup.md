---
title: "Problems with my amd multi display setup"
date: 2014-02-05
forum: Multimedia Software
---

### Post by balugege on 2014-02-05
Hello,
after I installed the amd proprietary driver my multi display setup is not longer working how i want it.
I have a 1920x1080 display at my hdmi port on the left and a smaller 1280x1024 monitor on my avi port on the right.
I want my 1080p display as my main display and the smaller one as secondary.
If i change the settings in amdcccle to multi-desktop and restart,the right(smaller) monitor is set as primary screen and working,but if i put my mouse over the left(bigger) screen the mouse turns into an x.The system settings only show my smaller monitor. Not only is the main screen the wrong monitor also the bigger screen doesnt to work.
So I tried the stretched over two displays mode.
Surprisingly this time both desktops seem to work like they should in multi monitor setup BUT the right screen is still the main one.If i go into the system settings and change anything something weird happens:
The output from the right display is on the left and the output from the left on the right, also I cant see my coursor.
In amdcccle my smaller monitor is always number 1 and the bigger one is number 2 but i didnt find a way to change wich is number one (maybe that could be the solution?).
My grapics Crad is a radeon hd 6700.Hope that someone can help me :)

---

### Post by cschroter on 2014-02-07
I have dual monitors working w/ AMD Radeon HD6850. Extended Desktop - 3200x1080 (1920x1080 | 1280x720)

Depending on what is powered on at startup, the main desktop can change, just open CCC and change it.

Had problems with the latest AMD fglrx-amdcccle driver. Currently have the **non** 'post-release update' activated (System Settings > Additional Drivers).

2:13.101-0ubuntu0.0.1 is the version if using Synaptic Package Manager.

---

