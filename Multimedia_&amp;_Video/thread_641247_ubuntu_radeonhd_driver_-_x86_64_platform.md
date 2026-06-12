---
title: "ubuntu radeonhd driver - x86_64 platform"
date: 2007-12-15
forum: Multimedia &amp; Video
---

### Post by tgilber1 on 2007-12-15
Has anybody been able to make the radeonhd driver that comes with Ubuntu work?  Presently, I am using the ati proprietary version on my Linux box because I was unable to load the version that comes with Ubuntu.  Everytime I used the radeonhd driver, it fails and defaults to the vesa driver.

Unlike the proprietary driver, I cannot manually load the Ubuntu version with a modprobe.  Additionally, it is not listed when I try to list the modules with a "modprobe -l radeonhd"  The proprietary version loads the fglrx version.  Furthermore, I tried to manually install the xorg version, to no avail, with the following instructions:

[http://www.phoronix.com/scan.php?page=article&item=843&num=1](http://www.phoronix.com/scan.php?page=article&item=843&num=1)

Is there postscript that should run to build the kernel-object module?  Appreciate some guidance.

Thanks,

---

### Post by tgilber1 on 2007-12-16
Sounds like that there are not too many out there that are using radeonhd driver.  What is peculiar the following command does not generate a kernel object module

sudo apt-get install xserver-xorg-video-radeonhd

which is why "modprobe -l radeonhd" does not list a radeonhd module

I tried other Ubuntu video adapter modules such as radeon and fglrx to no avail.

radeon does generate a kernel object modules, fglrx does not.

Is there different way to init the radeonhd driver to get the adapter going without a .ko module?  Appreciate anyone's help.

Thanks,

---

### Post by angryfirelord on 2007-12-18
I'm curious about it too. I'll experiment around with it when I have some free time, but in the meantime, try changing your xorg driver to say "radeonhd".

---

### Post by tgilber1 on 2007-12-27
I could not make the Ubuntu radeonhd driver work with ATI Radeon 2400 HD Pro.  Instead, I had to install the latest from open source radeonhd developers.  In addition to following the directions from the Phoronics website I had to add the following line to the /etc/xorg.conf file under the device section:  

Option          "HPD" "swap"

Here's an excerpt from phoronix website on installing the radeonhd

sudo apt-get install build-essential git-core configure-debian automake autoconf xorg-dev libtool

Now that git is installed, execute the below command to check out the RadeonHD driver from FreeDesktop.org.

git-clone git://anongit.freedesktop.org/git/xorg/driver/xf86-video-radeonhd

Now that there is a copy of the RadeonHD code locally, it's time to build and install the X.Org driver using the below commands.

cd xf86-video-radeonhd/; ./autogen.sh --prefix=/usr/; make; sudo make install

After that, it's time to update the xorg.conf to reference this new driver. In the Section "Device" area that is showing vesa, avivo, or fglrx, change the Driver "<driver-name>" line to radeonhd.

sudo gedit /etc/X11/xorg.conf

Since the RadeonHD driver doesn't yet support Composite/AIGLX, you need to manually disable them.

In the device section, which has the radeonhd driver, populate the following line:

#This line is critical to get by the broken connector error message
Option          "HPD" "swap" #This line is critical to get by the broke

Section "Extensions"
Option "Composite" "Off"
EndSection

Section "ServerFlags"
Option "AIGLX" "Off"
EndSection

Reference: [http://www.phoronix.com/scan.php?page=article&item=843&num=1](http://www.phoronix.com/scan.php?page=article&item=843&num=1)

---

### Post by tgilber1 on 2007-12-29
The xorg radeonhd development group fixed the issue with this video card.  Please, refer to the link:  [http://lists.opensuse.org/radeonhd/2007-12/msg00488.html](http://lists.opensuse.org/radeonhd/2007-12/msg00488.html).  Hence, with the card added to the rhd_id.c via a patch, I am able to fire the radeonhd driver without the HPD swap option.

---

### Post by markoloka on 2008-03-04
Yesterday i installed radeonhd driver. Was quite a work but it's running.

---

