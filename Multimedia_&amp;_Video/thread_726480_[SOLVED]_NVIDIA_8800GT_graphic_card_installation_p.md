---
title: "[SOLVED] NVIDIA 8800GT graphic card installation problem"
date: 2008-03-16
forum: Multimedia &amp; Video
---

### Post by bobetko on 2008-03-16
Since I built my new pc with nvidia 8800gt video card I don't have any fun time with my ubuntu installation. It took me a week to figure how to install ubuntu (in text mode) and now there is no way to install my 8800GT. 

I've downloaded newest drivers, and after trying to install them I was informed that kernel source tree cannot be found and installation failed.
This is my second attempt to install it and I am pretty much at point where I figured that I wasted a whole lot time.

**So, does anybody know how to fix this problem with kernel?**

Second part of problem is (this happened on my first attempt)...nvidia  installation went fine (2 months ago) with older drivers, and everything looked OK. The fan was working crazy, at 100% rate... kind of making wind tunnel under my desk... I could live with that (until nvida update their drivers), but after reboot, my ubuntu was in low resolution mode. So every time I would log in I would have to reinstall graphics drivers. This was the point where I gave up. I noticed that other people are having the same problem, I just didn't see any solutions. This leads me to other question (I am linux novice) why would somebody come up with product (this nvidia driver) which doesn't work? I this Ubuntu issue or something else? 
I spent a lot of time advertising ubuntu to my friends talking about how easy is to use and install.... and ... now I am quiet.... :-)

I am using ubuntu 7.10

---

### Post by bobetko on 2008-03-16
hm... sort of found solution myself on nvidia forum website.
For others who have this problem, make sure you follow guide below.
Full article is here: [http://www.nvnews.net/vbulletin/showthread.php?t=72490](http://www.nvnews.net/vbulletin/showthread.php?t=72490)

I made sure packages below are installed or uninstalled (as required). For some reason nvidia-kernel file remained, so I removed it with **sudo rm nvidia-kernel**  
I also used **uname -r** to get version of kernel I am using.
Nvidia'l driver I installed is x86-169.12. I think that is the newest one.

The fan is not too noisy. It seems that problem is fixed. And I also don't have issue with rebooting. works fine... The only thing not working is my dual display support. I'll try to figure that one later on. So happy....

As extension to my question: why was so hard to post these requirements on driver download web page? Unless ubuntu becomes user friendly, it will never get to the masses....

----------------------------------------------------------

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

---

### Post by louminati on 2008-03-19
Oh my...  After MANY hours of banging my head against my nvidia 8800gt and Ubuntu Gusty Gibbons, your post here had the only procedure I could find that finally worked for me.

I cannot begin to thank you enough for taking the time to post it!!

Cheers!

---

