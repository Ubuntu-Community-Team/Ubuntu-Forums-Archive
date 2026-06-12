---
title: "New Graphics Card Question"
date: 2008-05-22
forum: Multimedia Software
---

### Post by crimsonandred on 2008-05-22
I need a new graphics card, and I am looking at a GeForce 8600 GT. Will this card work with everything in Ubuntu?

(my current card causes the entire system to crash when I run a 3d program i.e. World of Warcraft)

---

### Post by cor2y on 2008-05-22
I have a 8600GTS it works in hardy heron 8.04 i currently use the official ubuntu closed source/restricted drivers to this day i can't the latest drivers to be installed using Envy.
A few caveats , if you are upgrading from a previous version of ubuntu you WILL run into problems trying to enable the closed source drivers, i recommend a clean install or at least remove the closed drivers and use the open source ones before starting the update/upgrade.
Second with the new driver there is a hue color issue on video playback, you will have to manually set the hue setting in the default media player (totem) in order to get videos to display the correct color setting, this is not an ubuntu issue but something nvidia themselves did with the hue setting in the closed drivers.
And thats about the only problems i ran into when trying to install the closed drivers for hardy heron.
The open drivers worked but unlike ati's theres no way to get compiz to work without using the closed drivers.

---

### Post by Xiong Chiamiov on 2008-05-22
There are some problems with the NVIDIA drivers in the repos.  However, this applies to all NVIDIA cards, not just the 8600.  You should be able to get it running by following [this]("http://ubuntuforums.org/showthread.php?p=4978329#post4978329").

---

