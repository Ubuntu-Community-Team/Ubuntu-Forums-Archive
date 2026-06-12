---
title: "Screen Resolution"
date: 2006-08-31
forum: Multimedia &amp; Video
---

### Post by Queue on 2006-08-31
Hi,

I know this has been asked a lot already but I am still havin problems with the resolution on my PC. Like all the similar threads, once I have installed 6.06 I am stuck in 640x480 with none of the other options being available in the drop-down. 

I have had a look at the xorg.conf file and the other resolution options are in there, it even picks up the make of the monitor correctly. I have also gone and deleted all but the 1024x768 options, rebooted and......nothing.

Any other suggestions? Bios?

I am running on a Dell Optiplex GX260 with the graphics onboard.

Rgds,
Q

---

### Post by Anonii on 2006-08-31
Try this first:
[http://doc.gwos.org/index.php/ChangeResolution](http://doc.gwos.org/index.php/ChangeResolution)
And if it doesnt work, this:
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

---

### Post by cousteau on 2007-02-04
Hi there.

This is my first post here, and I hope it´ ll help some ppl. :)

Well, browsing this site I figured out some ppl had problem installing Ubunto 6.x on a Dell Optiplex GX260. I own one of those smooth machines and had some problems, too. Main issues seem to be with the resolution, as the 260 seems to be stuck in 640x480, especially if you install Ubunto from scratch and there is no previous operating system on the machine or it has been deleted and the machine has been set back to standard-firmware.

Well, I had the same problem with my 260: Ubuntu booted perfectly, but the screen was stuck at 640x480 at 75 Hz with no other options. I browsed the web and found the following solution:

[http://blogs.law.harvard.edu/rlucas/2004/03/22](http://blogs.law.harvard.edu/rlucas/2004/03/22)
[http://lists.ze-linux.org/2004-02/msg00154.html](http://lists.ze-linux.org/2004-02/msg00154.html)

---quote---
With a fresh install of Red Hat 9 on a Dell Dimension 4600, the only video mode that would work with XFree86 was 640 x 480, which is ludicrously big on a decent-sized monitor.  Changing the config didn't do anything, even though the config was well within my monitor's limits.

The solution was to go into the BIOS setup and change the Integrated Devices (LegacySelect Options) / Onboard Video Buffer setting from 1 MB to 8 MB.  I'm not sure what the tradeoff with other aspects of the system is, but X nicely starts up at 1280 x 1024.  Apparently, this is the solution for other Dell models as well, including the Optiplex GX260; mine had Dell BIOS Revision A08.  Also, it seems to be the case that the problem is general to XFree86, although it manifested for me under Red Hat 9.

Thanks to Erick Tonnel at Dell, who kindly provided the solution.
---quote---

Worked on my machine. Ubuntu started at 1024x768 after this BIOS-change, not bad for a start. After that I reconfigured the XServer via the standard command

sudo dpkg-reconfigure xserver-xorg

and told the machine about the Intel-chipset and the features of my monitor, and Ubuntu booted at 1280x1024 at 75 Hz, which is perfect for my Dell 1702FP.

Well, hope this helps ...

-- 
thomas

---

