---
title: "Enabling dual monitors on ATI drivers"
date: 2008-12-24
forum: Multimedia Software
---

### Post by Alex Carroll on 2008-12-24
Hi, I have two monitors: one with resolution 1024x768 and one with resolution 1440x900. The larger resolution one is my primary monitor, and is to the right of my secondary one on my desk.

Using the ATI drivers, I have attempted to create a "Big Desktop," but this leaves me with a stretched wallpaper and space around the sides of each monitor. Logging out and then back in causes the secondary monitor to become a clone of the primary monitor.

In various other forums posts the following page has been linked to: [http://wiki.debian.org/XStrikeForce/HowToRandR12](http://wiki.debian.org/XStrikeForce/HowToRandR12)
Which appears to describe what I want to do, but following the instructions does not appear to change anything. I have checked my xorg.conf file for each of the entries it tells me to remove, but they are not there in the first place. Doing "xrandr --auto" also changes nothing, and xrandr doesn't detect my secondary monitor anyway.

Basically, is there a way to set my secondary monitor to 1024x768 with a refresh rate of 75Hz, while my primary monitor stays at 1440x900 and refreshes at 60Hz?

I am using the latest ATI linux drivers downloaded from their website (8.12). My graphics card is an ATI HD4850 with two screens attached to it.

Thanks for any help.

---

