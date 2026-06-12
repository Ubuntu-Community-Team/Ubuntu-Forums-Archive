---
title: "Installed nvidia-glx-new, want to revert to default nvidia driver."
date: 2007-05-15
forum: Multimedia &amp; Video
---

### Post by meldroc on 2007-05-15
Here's a somewhat tricky one.  In an effort to get Beryl to behave itself a little more, I installed the nvidia-glx-new package, which set me up with nvidia driver version 9755 (IIRC).  Unfortunately, 9755 isn't quite as well-behaved as I would like (suspend-to-ram and resume causes the virtual terminals to display nothing but random green squares...)

So I would like to revert back to the default nvidia drivers that are in the nvidia-glx package (I think that's version 9631) since that version appears to be more stable.

There's a catch.  When I uninstalled the nvidia-glx-new package and reinstalled the nvidia-glx package, it didn't switch the kernel module back.  So when I did that, X refused to start, with loud complaints about how the kernel module and the GLX library versions didn't match.  I ended up having to reinstall nvidia-glx-new just so I could get X working again (that or go to the sucky nv drivers.)

So the question is: once I uninstall nvidia-glx-new and reinstall nvidia-glx, how do I switch back to 9631 of the nvidia kernel module so I can be correctly reverted?

---

### Post by meldroc on 2007-05-16
Anyone?  Anyone?

Bueller?  Bueller?

Just from snooping around my filesystem and the nvidia-glx, nvidia-glx-new and linux-restricted-modules packages in Feisty, it looks like there are no less than three separate versions of the nVidia proprietary driver kernel module - one called nvidia_new that's version 9755, one that's just nvidia, that's version 9631, and one called nvidia_legacy that's the version set up to handle ancient nVidia cards like TNT2s and such.

Right now, my system will always load the nvidia_new module, which will cause loud screaming about version mismatches from the X server if I have package nvidia-glx installed instead of nvidia-glx-new.  I want to set my system so it loads module nvidia, not nvidia_new so I can revert to driver and glx library versoin 9631.  How do I do this?

---

### Post by dabl on 2007-05-16
> **meldroc said:**
> Anyone?  Anyone?


Bueller?  Bueller?



It's sounding a little desperate there -- I'll give a try, although I've not solved THAT Nvidia driver problem before.

Try running ```
sudo dpkg-reconfigure xserver-xorg
``` and on the first screen do NOT let it autodetect the video system.  On the second screen, tell it to use the VESA display, and then go on through the script with your default choices, whatever screen resolution you are comfortable with for the next 15 minutes, etc.  Upon completing the script, run ```
startx
``` and you will have a VESA display, probably generating a headache at 60 Hz refresh (or 50 if you're in Europe).

Now run Synaptic and delete all nvidia packages.  If you have linux-restricted-modules-`uname -r` installed, leave it. If not, you'd better install it.

Now re-start x (Ctrl-Alt-Backspace), log in, open Synaptic, and install nvidia-glx.

Now re-start x again, and (Lord willing) you will be greeted by the Nvidia driver splash screen for -9631, and all will be well in your world once again.

:)

---

### Post by meldroc on 2007-05-16
Hmm.  Reconfiguring my X server will probably be a bit of work, as historically I've manually edited my xorg.conf file, and running the automated tools used to set up that file will mangle my work.  I can certainly switch it from the nvidia driver to the nv driver so I can tinker with the kernel modules, but I'm certainly not going to keep it there - I like 3-D acceleration, which the nv driver doesn't handle at all.

I did try uninstalling and reinstalling the linux-restricted-modules-`uname -r` package - that didn't seem to accomplish anything.

I'm suspecting there's a line somewhere in /etc that tells the kernel which flavor of nvidia kernel module to use, but I'm not sure what that is.

I'll try uninstalling and purging all nvidia-related packages, then reinstalling them - that might do something.

---

### Post by meldroc on 2007-05-16
AHA, I found it!

It turns out that when you install nvidia-glx-new, it adds a file /lib/linux-restricted-modules/.nvidia_new_installed.  When Ubuntu gets around to loading kernel modules, it runs a script /sbin/lrm-video that simply checks for the existence of this file.  If it exists, it loads the nvidia_new module, if it doesn't exist, it loads the standard nvidia module.

So by uninstalling nvidia-glx-new, installing nvidia-glx, and removing the file /lib/linux-restricted-modules/.nvidia_new_installed, I correctly reverted.

Thanks for the suggestions.  I just needed to peek around the scripts and config files until I figured it out.

---

### Post by dabl on 2007-05-16
Excellent -- thanks for sharing the solution! :popcorn:

---

### Post by moopere on 2007-05-19
Fantastic!  Thanks a bunch.

Leaving that file behind when the package has been removed would surely be a bug?  I'll go and snoop around launchpad.

Craig

---

