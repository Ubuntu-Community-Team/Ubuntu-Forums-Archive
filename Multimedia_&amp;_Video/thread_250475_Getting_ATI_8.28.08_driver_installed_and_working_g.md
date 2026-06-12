---
title: "Getting ATI 8.28.08 driver installed and working great on Dapper with AMD Athlon"
date: 2006-09-04
forum: Multimedia &amp; Video
---

### Post by BJones on 2006-09-04
This is my first post to this forum.  I only hope it's as helpful to others as the many great posts I've read here have been to me.

I have an ATI All-In-Wonder X800XT and AtlhonXP 3200+ CPU running on an NForce 2 based motherboard.  After having a multitude of problems trying to select a decent screen resolution, having really jerky DVD playback with Totem, slideshow graphics in screensavers and games, etc, on my new Ubuntu installation, I've come across several guides that have been invaluable to me and just wanted to share.

Keep in mind, much of the installation work is done in a "Terminal" window.  I'm an absolute Linux noob and found this a bit daunting at first, but a simple copy(ctrl-c)/paste(ctrl-shift-v) from Firefox to the Terminal window  made it pretty easy for me to handle.  :biggrin: 

The first thing to do is update your kernel to one that contains processor specific optimizations for the K7 (Duron/Athlon) architecture, since the Ubuntu installation seems to install a more generic kernel.  Instructions for doing so are here:  [http://ubuntuforums.org/archive/index.php/t-186792.html](http://ubuntuforums.org/archive/index.php/t-186792.html)

Look a little further than halfway down the page to "Fifth Stage:  Performace Tweaks", and follow instructions for updating the K7 kernel.  Only do this if you are using either an AMD Duron or Athlon processor!

It's actually only on command, entered in a Terminal window:

sudo aptitude install linux-k7

You must reboot afterward, and the GRUB loader will now default to the new kernel at bootup.  The older, default kernel "i386" is still selectable, in case you decide you need to load it instead later.

Once you're back up and running, check the next guide for installing your ATI video driver.  I found it to be an extremely comprehensive guide and easy to follow, with full instructions on how to install the latest ATI Linux driver 8.28.08, available directly from [www.ati.com](www.ati.com)

Follow the instructions here:
[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

Make sure to change your default download location in Firefox to your "home folder", otherwise this won't work unless you change directories in Terminal first. (which I have no idea how to do)  ;-)

Follow all instructions for Method 2 to install the ATI driver.  You will have to reboot afterward for your changes to take effect.  You should then be able to select the screen resolution of your choice and be greeted to a very snazzy looking desktop.  =D>

As per the guide, you will have to recompile the driver modules should you at some point update the kernel.

Next, In order to update your system to support playback of copy protected DVDs, you must download several codec packages and other software.  Again, there is a step by step guide here:

[http://www.ehomeupgrade.com/entry/2663/how-to_get_full](http://www.ehomeupgrade.com/entry/2663/how-to_get_full)

Be sure and reboot again before doing anything else.

Congratulations!  You should now have a really snappy Dapper AtlonXP setup with full multimedia support, silky smooth DVD playback (even on encrypted disks), as well as fully hardware accelerated graphics for the desktop and games....or at least it worked for me.  ;) 

I hope this is a help to anyone that's having any or all of the problems I listed at the beginning of the post.

---

