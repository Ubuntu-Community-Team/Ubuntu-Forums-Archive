---
title: "Latest 8800GTS Driver"
date: 2007-06-08
forum: Multimedia &amp; Video
---

### Post by DHC-2 on 2007-06-08
It appears that NVIDIA has released a new driver today June 8 for the GeForce 8 series cards.  Is this the correct driver for the 32 bit Ubuntu?  NVIDIA-Linux-x86_64-100.14.09-pkg2.run

If not what is the lastest driver for a 32 bit install and how do I go about installing it to a fresh install of Ubuntu 7.04?

I'm a complete noob at this and have been reading the forum for days and I'm still confused as to the best method to install the video driver.  Would greatly appreciate any help and insight.

---

### Post by Bachstelze on 2007-06-08
The correct driver for 32 bit Linux is here :

[http://www.nvidia.com/object/linux_display_ia32_100.14.09.html](http://www.nvidia.com/object/linux_display_ia32_100.14.09.html)

To install it in Ubuntu :

```
sudo apt-get remove linux-restricted-modules* nvidia-glx*
sudo apt-get install build-essential linux-headers-$(uname -r) pkg-config xorg-dev
sudo sh /path/to/file.run
```

---

### Post by DHC-2 on 2007-06-08
Thank you so much for your reply and the link to the latest driver.

I'll give it a try.

---

### Post by jme on 2007-06-09
> **HymnToLife said:**
> The correct driver for 32 bit Linux is here :

[http://www.nvidia.com/object/linux_display_ia32_100.14.09.html](http://www.nvidia.com/object/linux_display_ia32_100.14.09.html)

To install it in Ubuntu :

```
sudo apt-get remove linux-restricted-modules* nvidia-glx*
sudo apt-get install build-essential linux-headers-$(uname -r) pkg-config xorg-dev
sudo sh /path/to/file.run
```

Sorry to hijack the post.  I have been trying for the last week to get my 8800 GTS working and came across your advice which has got me the closest to getting it working to date.  The install works without any errors, I can then startx into a working Gnome session and use the Nvidia software to configure the resolution of my monitor.  The problems come when I restart.  As soon as I turn the computer off and reboot I get a black screen again.

The error message reads: 

```

Error: API mismatch: this NVIDIA driver component has version 100.14.09, but the NVIDIA kernel module's version does not match. 

```

Any thoughts or advice on the problem would be great.

Jamie

---

### Post by jme on 2007-06-09
Excellent! I've finally managed to get it working.

One thing people want to be aware of if using this method:

> 

If you wish to install the NVIDIA Linux graphics driver on a Debian GNU/Linux or Ubuntu system that ships with Xorg 7.x, please ensure that your system meets the following requirements:

    * development tools like make and gcc are installed
    * the linux-headers package matching the installed Linux kernel is installed
    * the pkg-config and xserver-xorg-dev packages are installed
    * the nvidia-glx package has been uninstalled with the --purge option and the file /etc/init.d/nvidia-glx or /etc/init.d/nvidia-kernel does not exist.

If you use Ubuntu, please also ensure that the linux-restricted-modules or linux-restricted-modules-common packages have been uninstalled. Alternatively, you can edit the /etc/default/linux-restricted-modules or /etc/default/linux-restricted-modules-common configuration file and disable the NVIDIA linux-restricted kernel modules (nvidia, nvidia_legacy) via:

    DISABLED_MODULES="nv nvidia_new"

From: [http://www.nvnews.net/vbulletin/showthread.php?t=72490](http://www.nvnews.net/vbulletin/showthread.php?t=72490)



Once I had ensured all of that was met and then reinstalled the driver it all worked :)

Thanks to everyone on the forum who has contributed to posts about 8800GTS drivers.

---

### Post by showty on 2007-06-15
> **HymnToLife said:**
> The correct driver for 32 bit Linux is here :

[http://www.nvidia.com/object/linux_display_ia32_100.14.09.html](http://www.nvidia.com/object/linux_display_ia32_100.14.09.html)

To install it in Ubuntu :

```
sudo apt-get remove linux-restricted-modules* nvidia-glx*
sudo apt-get install build-essential linux-headers-$(uname -r) pkg-config xorg-dev
sudo sh /path/to/file.run
```

But what about for those that need the madwifi drivers in the restricted-modules!!!!

ASAP NEED HELP! :(

---

