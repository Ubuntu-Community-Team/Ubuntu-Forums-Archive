---
title: "Can't get Nvidia drivers working in Natty"
date: 2011-10-03
forum: Multimedia Software
---

### Post by adrianj2012 on 2011-10-03
I recently bought a Dell XPS L502X laptop with an nvidia graphics card hoping that I could get it to work with Ubuntu 11.04 (64-bit), but so far, I've tried many things and haven't been able to solve the problem alone.  Currently, if I try to boot normally, the bootscreen shows many lines of text with different messages, such as:

stopping Flush boot log to disk
save udev log and update rules
skipping profile in /etc/apparmor.d/disable usr.bin.firefox
stopping Userspace bootsplash
starting AppArmor profiles
starting TiMidity++ ALSA midi emulation
... and then it just stops there and doesn't proceed.

I've run the script located below to try to fix it, but I'm not sure whether it did anything.
[http://paolobernardi.wordpress.com/2011/05/01/fix-plymouth-on-ubuntu-after-installing-nvidia-or-ati-proprietary-drivers-for-ubuntu-11-04-natty/](http://paolobernardi.wordpress.com/2011/05/01/fix-plymouth-on-ubuntu-after-installing-nvidia-or-ati-proprietary-drivers-for-ubuntu-11-04-natty/)

I tried installing the actual nvidia drivers using the steps here:
[http://ubuntuforums.org/showthread.php?t=1647855](http://ubuntuforums.org/showthread.php?t=1647855)
... but no success.  However, I am still able to boot into failsafe mode without issue from the recovery console and interestingly enough, if I select "Additional Drivers" from the menu, it tells me the NVIDIA accelerated graphics driver (version current) [Recommended] "is activated and currently in use".  I think that's off, especially since I can't even run a game of Hedgewars.

Any help would be greatly appreciated, and I would me more than willing to provide any additional information.

Edit: I now have the drivers working... somewhat.  I use Bumblebee to use the graphics card to run graphics-heavy application. The only problem now is that I can't seem to run compiz or hedgewars normally.  If I want to run hedgewars, I need to type in "optirun hedgewars" to get it working.  Besides that, everything seems alright.  Any ideas?

Edit2: Seems like all I need is running fine.  If I run glxgears, however, it gives me this message:
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual
But "optirun glxgears" works fine.  Certain screensavers (ant, GLxx) don't work/show, but I don't really need them.  Hedgewars won't start a game unless using the preceding "optirun" command, and quadrapassel won't run at all, but those seem like minor annoyances.  Everything necessary seems to be doing fine.  Thanks to anyone who read this post and I hope this helps someone in a similar situation.

---

