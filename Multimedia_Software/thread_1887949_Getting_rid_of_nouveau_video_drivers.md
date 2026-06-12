---
title: "Getting rid of nouveau video drivers"
date: 2011-11-28
forum: Multimedia Software
---

### Post by wabbit46 on 2011-11-28
I am trying to setup v 11.10 of  Ubuntu with an Nvidia GeForce FX 5500 graphics card with 256 MB of memory.

The standard 3D drivers result in a resolution of 640x480 with no other option. I have downloaded from Nvidia the correct driver for my video card. To install this X windows must be turned off - have done that and the installation program says that the nouveau drivers must be disabled and creates a file nvidia-installer-disable-nouveau in the /etc/modprobe.d directory. 

The driver still will not install. Can anyone help me PLEASE

---

### Post by BC59 on 2011-11-28
You could remove nouveau

> Nouveau, an open source driver, is installed by default. It's possible to remove it completely, but it is not necessary and therefor not recommended.

If you still desire to remove it, you can do so by entering the following command in a terminal:

sudo apt-get --purge remove xserver-xorg-video-nouveau


-BUT! I'm not sure if it's safe and you are not going to crash your system.

---

### Post by BC59 on 2011-11-28
There is a guide here which could help you to avoid crashing your system:

[http://linuxers.org/howto/how-remove-nouveau-drivers-ubuntu](http://linuxers.org/howto/how-remove-nouveau-drivers-ubuntu)

---

### Post by wabbit46 on 2011-11-29
> **BC59 said:**
> There is a guide here which could help you to avoid crashing your system:

[http://linuxers.org/howto/how-remove-nouveau-drivers-ubuntu](http://linuxers.org/howto/how-remove-nouveau-drivers-ubuntu)

Thanks BC59 I followed the instructions exactly and still the NVIDIA driver would not install. There seems to be some vestige of the nouveau drivers left on my system.

I also tried totally removing the nouveau drivers as per your other suggestion. This results in a totally white terminal with undecipherable black characters on it. It is beginning to look like I need a new video card.

---

### Post by BC59 on 2011-11-29
Usually you can correct the Nvidia problems while installing the proprietary drivers recommended from Ubuntu and from the application Jockey.

---

### Post by buntudawg on 2011-11-29
I don't know if this link is of any use (it's for 11.04):

[http://www.pc-freak.net/blog/how-to-install-nvidia-geforce-fx-5500-on-ubuntu-11-04/](http://www.pc-freak.net/blog/how-to-install-nvidia-geforce-fx-5500-on-ubuntu-11-04/)

Personally, I gave up trying to get this video card to work in one of my boxes (even back with 10.04), and installed Lubuntu on that machine instead.

Good Luck.

---

### Post by beew on 2011-11-29
First of all, you shouldn't download the driver from Nvidia and try to install the .run file. Ubuntu is not Windows, usually you don't need to download and install drivers from manufactures' website. Click on Additional Drivers and let Ubuntu detects and installs the driver for you. Installing from Nvidia is problematic because the generic Linux driver may not have been patched or optimized for whatever Ubuntu idiosyncrasies that may exist; also you have to reinstall every time you have a kernel update.

Secondly if you install Nvidia's driver with "Additional Drivers" you don't need to do anything with the nouveau driver. Just install the Nvidia driver, go to the terminal and type
```
sudo nvidia-xconfig 
``` Then reboot and that's it. Since Ubuntu 10.10 Ubuntu has been able to automatically load the Nvidia driver if it detects its presence, you don't need to remove or blacklist nouveau and risk removing the wrong packages and break your system in the process. I have installed Ubuntus 10.10, 11.04 and 11.10 on my Nvidia machine with Nvidia's driver without having once to do anything funny with gdm, initramfs  or the Nouveau drivers. :)

---

### Post by wabbit46 on 2011-11-29
> **beew said:**
> First of all, you shouldn't download the driver from Nvidia and try to install the .run file. Ubuntu is not Windows, usually you don't need to download and install drivers from manufactures' website. Click on Additional Drivers and let Ubuntu detects and installs the driver for you. Installing from Nvidia is problematic because the generic Linux driver may not have been patched or optimized for whatever Ubuntu idiosyncrasies that may exist; also you have to reinstall every time you have a kernel update.

Secondly if you install Nvidia's driver with "Additional Drivers" you don't need to do anything with the nouveau driver. Just install the Nvidia driver, go to the terminal and type
```
sudo nvidia-xconfig 
``` Then reboot and that's it. Since Ubuntu 10.10 Ubuntu has been able to automatically load the Nvidia driver if it detects its presence, you don't need to remove or blacklist nouveau and risk removing the wrong packages and break your system in the process. I have installed Ubuntus 10.10, 11.04 and 11.10 on my Nvidia machine with Nvidia's driver without having once to do anything funny with gdm, initramfs  or the Nouveau drivers. :)

Initially I tried using the Additional Drivers recommended by Ubuntu and it resulted in a screen resolution of 640 x 580 with no other options available. This was clearly not a viable option.

---

### Post by kurt18947 on 2011-11-29
> **buntudawg said:**
> I don't know if this link is of any use (it's for 11.04):

[http://www.pc-freak.net/blog/how-to-install-nvidia-geforce-fx-5500-on-ubuntu-11-04/](http://www.pc-freak.net/blog/how-to-install-nvidia-geforce-fx-5500-on-ubuntu-11-04/)

Personally, I gave up trying to get this video card to work in one of my boxes (even back with 10.04), and **installed Lubuntu on that machine instead**.

Good Luck.

This seems like a good choice for older machines/video subsystems.

---

### Post by wabbit46 on 2011-11-29
> **buntudawg said:**
> I don't know if this link is of any use (it's for 11.04):

[http://www.pc-freak.net/blog/how-to-install-nvidia-geforce-fx-5500-on-ubuntu-11-04/](http://www.pc-freak.net/blog/how-to-install-nvidia-geforce-fx-5500-on-ubuntu-11-04/)

Personally, I gave up trying to get this video card to work in one of my boxes (even back with 10.04), and installed Lubuntu on that machine instead.

Good Luck.

Thanks for the tip Buntudawg. Unfortunately some of the modules referred to in this article are not available in 11.10 and the guide therefore did not work.

---

### Post by rsvancara on 2011-11-29
Never install the binary drivers directly from Nvidia.  Just my two cents.  You will spend a lot of time cleaning up your system.  I keep hoping BTRFS will mature enough for snapshots.  

Randall Svancara
[http://www.knowyourlinux.com/]("http://www.knowyourlinux.com/content/backing-dvd-using-handbrake-linux")

---

### Post by wabbit46 on 2011-12-05
> **rsvancara said:**
> Never install the binary drivers directly from Nvidia.  Just my two cents.  You will spend a lot of time cleaning up your system.  I keep hoping BTRFS will mature enough for snapshots.  

Randall Svancara
[http://www.knowyourlinux.com/]("http://www.knowyourlinux.com/content/backing-dvd-using-handbrake-linux")

Thanks for the advice Randall. It appears I have two options.

1. Install the binary drivers from Nvidia and get 3D acceleration.

2. Put up with 2D resolution or buy a new Video card (preferably not an NVidia one).

---

### Post by inobe on 2011-12-05
> **rsvancara said:**
> Never install the binary drivers directly from Nvidia.  Just my two cents.  You will spend a lot of time cleaning up your system.  I keep hoping BTRFS will mature enough for snapshots.  

Randall Svancara
[http://www.knowyourlinux.com/]("http://www.knowyourlinux.com/content/backing-dvd-using-handbrake-linux")

what does that link have to do with drivers?

should i report you as a spammer?

> **wabbit46 said:**
> Thanks for the advice Randall. It appears I have two options.

1. Install the binary drivers from Nvidia and get 3D acceleration.

2. buy a new Video card (preferably not an NVidia one).

a newer nvidia card would be best, you just won't find a decent agp model these days, we've been using pci-e for some years now:P

---

### Post by BicyclerBoy on 2011-12-05
The link in post #6 is all wrong..the nVidia driver is not even running..no GLX acceleration just mesa.. 

The old nVidia GPU like fx5200 etc are not supported in the latest drivers.
see appendix A of the driver readme..

The legacy driver (nVidia 96 & 173) exists to support the old h/w.

This legacy driver was recently rebuilt to match the ABI changes in Xorg shipping with 10.04 11.10.
You may have to get it from nVidia or from xorg-edgers/x-swat team ppa..

The nVidia driver installer scripts should generate the nouveau blacklisting. (.conf file in /etc/modprobe.d/)

Look in the /var/log/Xorg.0.log file for the driver loading errors..
Your resolution problems may be EDID related & not driver failure..
You need to debug step-by-step..


Installing the driver from nVidia website is not that onerous, but you must read the driver readme first.
[http://us.download.nvidia.com/XFree86/Linux-x86_64/173.14.31/README/part-01.html](http://us.download.nvidia.com/XFree86/Linux-x86_64/173.14.31/README/part-01.html)

---

### Post by jimbo99 on 2012-06-06
My advise is to NEVER use anything but nVidia's proprietary drivers.  They are full featured and more stable.  In my 10+ years of using Linux clearly the proprietary drivers for nVidia (though not necessarily ATI) are vastly superior to the open source equivalent.

The open source drivers for nvidia, the nouveau drivers, are a pipe-dream.

---

### Post by wabbit46 on 2012-06-12
> **jimbo99 said:**
> My advise is to NEVER use anything but nVidia's proprietary drivers.  They are full featured and more stable.  In my 10+ years of using Linux clearly the proprietary drivers for nVidia (though not necessarily ATI) are vastly superior to the open source equivalent.

The open source drivers for nvidia, the nouveau drivers, are a pipe-dream.

Thanks for the advice jimbo99. That is what I wish to do but the nouveau drivers are preventing me from installing the latest nVidia drivers.

---

### Post by millerthegorilla on 2013-02-11
Hi, I have installed the nvidia drivers without problems.   I think that you will find that in order to install them properly you need to stop the x windowing system, something like sudo lightdm stop before switching to a different terminal (using ctrl and alt and F1, F2 etc) and then signing into root and running the nvidia installer.  If this works ok then it will install and add a module blacklist to the appropriate directory for blacklisting the nouveau driver.
*Make certain to check* ...  that you're card is supported.   Nvidia recently migrated a number of cards to the legacy driver, the one I am now using, so check the supported model list by running lspci -v and comparing the model name with the list that Nvidia provides and then download the appropriate driver.

This is based on using the nvidia-legacy driver for ubuntu-studio 12.10.  I am still having problems with getting Xinerama working with seperate screens but only when composite is enabled and this has only happened since the latest upgrade, so it would appear the DKMS is not working (if that is the system for automatically upgrading).
If you are using the realtime patched kernel then xinerama will not work at all until a patch is released for the nvidia legacy driver, so far this has not been addressed.

If anyone knows if a patch has been released for the realtime kernel or where to obtain/request one, then please let me know.   Many thanks!

---

