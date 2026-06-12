---
title: "Manually installed nvidia drivers, how to make them work?"
date: 2009-07-21
forum: Multimedia Software
---

### Post by Nick255 on 2009-07-21
I have manually installed the latest nvidia drivers (the ones installed via apt-get don't support 2.6.30.1) but I don't know how to tell X to use it.  Normally this wouldn't be a problem as I would just use the xorg.conf that it came with, but apparently you aren't supposed to use xorg.conf anymore and I have no idea what to do after reverting xorg.conf to the normal one that came with kubuntu.

---

### Post by HousieMousie2 on 2009-07-22
I am using Hardy, my manually installed nVidia driver works great.

I (more or less) followed the advice from the NVNews web site.

> Debian GNU/Linux or [K]Ubuntu with Xorg 7.x

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

---

