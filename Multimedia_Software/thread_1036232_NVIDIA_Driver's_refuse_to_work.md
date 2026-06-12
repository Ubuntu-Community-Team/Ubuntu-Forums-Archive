---
title: "NVIDIA Driver's refuse to work"
date: 2009-01-10
forum: Multimedia Software
---

### Post by ogivol on 2009-01-10
Hey all, yes I know first post and he asks for help, but what can I say...

My specs:

I am currently using 8.10 (with no special modifications etc...)
My video card is a NVIDIA Driver 8500 GT (although I feel this problem may be beyond the specific card...)
-----------------------------------------

The Problem:
1. I'd like to install a NVIDIA driver, first thing I try is hardware drivers. Both 180.22 and 177 fail to work giving the error:

"Failed to initialize the NVIDIA graphic device" ...

2. Envy/Envyng also respond after install with the same message

3. A manual install responds with the same message....

4. I have tried every sort of modification in the book from manually editing my xorg file, to recovery mode...to well...everything

Being the newbie I am, these things were very difficult but that aside it still DOES NOT WORK


Let me give you a detailed run through of my error:

We load up the comp, and for a instant what looks like a cracked and corrupted image of NVIDIA logo pops up, and then in the next instant moves to the Ubuntu progress bar image.....

after fully loaded, it moves into a black and white text based image which looks to be checking the status of various computer objects like battery (all of which say it is ok), and the screen will blink exactly 3 times....

Boom, Ubuntu low graphics message pops up with a whole bunch of options, all of which I've tried, none of which have worked.....



MAYBE..........just MAYBE.....its a hardware thing.....what would be helpful is if more knowledgeable members than me could post some solutions. I will instantly let you know if I've tried it, if not I will immediately try it and tell you if it worked....yes I'm that desperate =O...

I do appreciate the help though

---

### Post by ed-koala on 2009-01-10
Read this thread []("http://ubuntuforums.org/showthread.php?t=1035873").  Drivers are funny about what packages are installed.    Took me a number of reinstalls to figure it out after collecting info from various threads.

---

### Post by ogivol on 2009-01-14
You didn't post a link....

---

### Post by Egi_Power on 2009-01-14
Hi there!

I'm having similar problems with nVidia driver.

I'm using Ubuntu 8.04.1.

My card is 8800 GT.

My problem started after the kernel update, when I tried to install the 180.22 driver from nVidia.

[Here is the link to my thread.]("http://ubuntuforums.org/showthread.php?t=1037915")

Just in case you solve your issue, you could leave me a post in my thread.

Good luck with it.

Egi_Power

P.s:

Debian GNU/Linux or [K]Ubuntu with Xorg 7.x

If you wish to install the NVIDIA Linux graphics driver on a Debian GNU/Linux or Ubuntu system that ships with Xorg 7.x, please ensure that your system meets the following requirements:

    * development tools like make and gcc are installed
    * the linux-headers package matching the installed Linux kernel is installed
    * the pkg-config and xserver-xorg-dev packages are installed
    * the nvidia-glx package has been uninstalled with the --purge option and the files /etc/init.d/nvidia-glx and /etc/init.d/nvidia-kernel do not exist

If you use Ubuntu, please also ensure that the linux-restricted-modules or linux-restricted-modules-common packages have been uninstalled. Alternatively, you can edit the /etc/default/linux-restricted-modules or /etc/default/linux-restricted-modules-common configuration file and disable the NVIDIA linux-restricted kernel modules (nvidia, nvidia_legacy) via:

    DISABLED_MODULES="nv nvidia_new"

Additionally, delete the following file if it exists:

    /lib/linux-restricted-modules/.nvidia_new_installed

Please note: unfortunately, it has become difficult to keep track of the pre-/post-installation steps required for [K]Ubuntu, and the above instructions may be incomplete. If in doubt, it is recommended that you use your distributor's NVIDIA Linux graphics driver packages, exclusively.


If you require further assistance after following the instructions above, please see:
[http://www.nvnews.net/vbulletin/showthread.php?t=46678](http://www.nvnews.net/vbulletin/showthread.php?t=46678).

[You can find it on this website.]("http://www.nvnews.net/vbulletin/showthread.php?t=72490")

---

