---
title: "nVidia drivers"
date: 2012-04-26
forum: Multimedia Software
---

### Post by tomatoe on 2012-04-26
Hi!

Recently installed ubuntu 12.04 on my desktop pc. 
The graphics card is nVidia geforce FX 5200.

So, I wanted to install nvidia's drivers for everything to work smoothly.

Followed these instructions
[http://www.ubuntugeek.com/how-to-install-nvidia-295-40-drivers-in-ubuntu-12-0411-10-using-ppa.html](http://www.ubuntugeek.com/how-to-install-nvidia-295-40-drivers-in-ubuntu-12-0411-10-using-ppa.html)

Then I went to additional drivers. nVidia current is there, so I activated it and rebooted. After reboot resolution was like 640x480 (native is 1920x1020). So I did this

 sudo apt-get purge xserver-xorg
 sudo apt-get install xserver-xorg xserver-xorg-video-all
 sudo reboot

Resolution got a bit better, but still no good.
I opened nvidia x server settings, but it says You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

After nvidia-xconfig nothing changes.
In Details it says graphic driver is VESA: NV34 Board - p162-1nz
Nouveau drivers are deleted, read in other topics, that it has to be deleted to enable nvidia's drivers.

Anyway, I guess the problem is that the driver isn't enabled, but how to do it?

Any help would be appreciated!
Regards.

---

### Post by BicyclerBoy on 2012-04-26
That dinosaur video card is not supported by the latest driver 295.40.xx

You need driver version 173.14.xx that has been rebuild for the later Xorg.

Check the driver readme appendix A.

---

### Post by kc1di on 2012-04-26
Also I would hold off install Nvidia Drivers in 12.04 for the moment as there was a bug in the last update. Hopefully it will be fixed before final today. 
Cheers :)

---

### Post by tomatoe on 2012-04-26
173.14.xx driver can't be installed because of dependencies. Got to stick with nouveau driver I guess.

Anyway thanks for help.

---

### Post by BicyclerBoy on 2012-04-26
Are you sure you are picking the (recently) rebuilt package 173.14.31 for Xorg 1.10 & later?

Can you try this in synaptic package manager & see the dependencies?
(nvidia-173-update or similar)

You should probably wait until 12.04 is released (today)..as kc1di mentioned..

---

### Post by flatko on 2012-04-28
Just for the record - don't install Nvidia 173 drivers from the nvidia website. It doesn't work and uninstalling it also dont work. It doesnt remove all the components and Unity launcher can't start. I had to install nvidia-current from the repos and remove it again in order to delete all the remaining files.
It adds jockey-gtk entries that I still can't manage to clean.
Too bad for nvidia... I'll never buy anything from nvidia again.

---

### Post by tomatoe on 2012-04-28
> **BicyclerBoy said:**
> Are you sure you are picking the (recently) rebuilt package 173.14.31 for Xorg 1.10 & later?

Can you try this in synaptic package manager & see the dependencies?
(nvidia-173-update or similar)

You should probably wait until 12.04 is released (today)..as kc1di mentioned..

Tried nvidia-173-updates. Here are those dependencies

The following packages have unmet dependencies:

nvidia-173: Depends: x11-common (>= 1:7.0.0) but 1:7.6+12ubuntu1 is to be installed
            Depends: xorg-video-abi-10 but it is not going to be installed
            Depends: xserver-xorg-core (>= 2:1.8.99.905-1ubuntu3) but 2:1.11.4-0ubuntu10 is to be installed

P.S.
I've done sudo apt-get update and all those things

---

### Post by BicyclerBoy on 2012-04-28
If you are considering using installer from nVidia website you need to read the driver readme & follow the instructions. Same for un-installing.
I have used nVidia drivers from the website off & on over years without issue apart for odd glx folder/symlink problems.

Is this the same version you tried?
[https://launchpad.net/ubuntu/oneiric/+source/nvidia-graphics-drivers-173/173.14.30-0ubuntu8.1](https://launchpad.net/ubuntu/oneiric/+source/nvidia-graphics-drivers-173/173.14.30-0ubuntu8.1)

Or have you taken the plunge to 12.04 ?

---

### Post by tomatoe on 2012-04-28
> **BicyclerBoy said:**
> If you are considering using installer from nVidia website you need to read the driver readme & follow the instructions. Same for un-installing.
I have used nVidia drivers from the website off & on over years without issue apart for odd glx folder/symlink problems.

Is this the same version you tried?
[https://launchpad.net/ubuntu/oneiric/+source/nvidia-graphics-drivers-173/173.14.30-0ubuntu8.1](https://launchpad.net/ubuntu/oneiric/+source/nvidia-graphics-drivers-173/173.14.30-0ubuntu8.1)

Or have you taken the plunge to 12.04 ?


No, thats not the same version, but this version isn't in synaptic at all. Tried installing from tar.gz from link you gave, but failed. Don't know how to install those .run files correctly...
I think I'll wait till it's in synaptic, or will buy new graphic card since this old crap can't be run with my monitor through DVI port.

---

### Post by BicyclerBoy on 2012-04-28
The FX5200 was good in its day, was in the iMac iLamp 20", but that day is over.

That s/w source will not be in synaptic until you change your software sources i.e. add the ppa.
Stay clear of tarballs etc..
Try to find the "deb" archive & load package archive with gedi.

The h/w problem with your graphics card is going to become a mobo problem.
I guess the 5200 is AGP.
The last AGP card was 8400. Could have been a 9400 or 8500..
Could have been a PCI version..

All current graphics cards are PCI-e (excepting AMD fusion & iCPUs & chipset)

---

### Post by tomatoe on 2012-04-29
Yep, mine 5200 is AGP. The whole computer is pretty old, but it does common things nicely.

Will look for .deb file today later.

---

### Post by BicyclerBoy on 2012-04-29
I can't find one..

Maybe if you enable proposed updates in synaptic..

---

### Post by tomatoe on 2012-04-29
Still dependencies if proposed is enabled.

---

### Post by BicyclerBoy on 2012-04-29
See if you can force xserver-xorg-core back to version 1.10..

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=641621](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=641621)

This problem is probably not going to be fixed (for 11.10).
10.04 LTS & 12.04 LTS are the focus..

---

### Post by Yellow Pasque on 2012-04-29
Downgrading X sounds like a recipe for disaster, but until Nvidia fixes their drivers, it's the only way to use the binary drivers on Precise: [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173/+bug/948053](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173/+bug/948053)

---

### Post by bigbudz on 2012-04-30
I have the same dinosaur video card in an old secondhand dell dimension i got for 60 bucks 3 or 4 years ago. I installed 12.04 and nvidia drivers failed to install, but unity 2d is running fine. It appears unity 3d is not installed. The 173.14xx driver ran fine on older pre-unity versions. 

This sounds horrible. I guess you just can't get this card to work in unity? And then having to install unity 3d??? ugh. 

If you ever figure this out please let me know how.

---

### Post by tomatoe on 2012-04-30
> **BicyclerBoy said:**
> See if you can force xserver-xorg-core back to version 1.10..

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=641621](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=641621)

This problem is probably not going to be fixed (for 11.10).
10.04 LTS & 12.04 LTS are the focus..

Synaptic won't let me force any other version.
Hope nVidia will resolve dependencies soon.

---

### Post by Jbike on 2012-04-30
I have the same problem here. I read through the post, but I am still unclear if this real problem has a solution. Which ppa exactly needs to be added? 

Thanks

---

### Post by Yellow Pasque on 2012-04-30
> **Jbike said:**
> I have the same problem here. I read through the post, but I am still unclear if this real problem has a solution. Which ppa exactly needs to be added? 

Thanks
There's no solution right now. Just use the open-source nouveau drivers until nvidia updates their 173 driver to be compatible with modern X.

---

### Post by tomatoe on 2012-04-30
Good day!

This guy did it. Actually just forced xserver to downgrade.
Worked for me :)

> **zecoyote007 said:**
> Hi guys, 

In order to use nvidia-173 or nvidia-96, please see my post here:
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173/+bug/922268](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173/+bug/922268)

I found a workaround: keep the 11.10 version of the Xorg server :grin:
No conflict at all with any package from 12.04 !!!

nvidia-173 drivers are not compatible with Xorg (ABI to be precise) version released in 12.04.
So I stick with 11.10 version of Xorg. I had to make the following changes to backport Xorg:

1) In /etc/apt/sources.list :

deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) oneiric main
deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) oneiric main

2) In /etc/apt/preferences:

Package: xorg xserver-xorg*
Pin: release a=oneiric
Pin-Priority: 1050

3) Note related to nvidia-173/96 on Ubuntu 12.04 (optional if you face slow graphics)
I'm using old hardware with nvidia-173 drivers and I don't like the fact  "composite" is mandatory to use Unity correctly (very laggy) I had to  force composite to switch it "off" to avoid laggy windows by modifying  /etc/X11/xorg.conf:

Section "Extensions"
    Option "Composite" "Disable"
EndSection

Enjoy.

Nicolas

---

### Post by codefenix on 2012-05-01
I had the same exact problem with the same card, the GeForce fx5200.  This workaround worked for me as well.  I will add, however, that I also had to remove nvidia-current and install nvidia-173.

---

### Post by Crinos512 on 2012-05-14
Just found this: [http://www.nvnews.net/vbulletin/showthread.php?t=179489&page=2](http://www.nvnews.net/vbulletin/showthread.php?t=179489&page=2)

_Summery:_
> 
Nvidia sez they're working on an update to 173.14.* for xservers 1.11 and 1.12. They can't promise that the 96.xx.xx driver will be updated as well.

( - AaronP @ NVIDIA Corporation; 05-08-12, 03:58 PM)

:popcorn:

---

### Post by fraterchristopher on 2012-05-15
> **tomatoe said:**
> Good day!

This guy did it. Actually just forced xserver to downgrade.
Worked for me :)


I tried to do this, but it didn't work for me. 

1) I'm not exactly sure what to do in the /etc/apt/preferences directory, b/c there doesn't seem to be a file to edit there
2) After adding the sources lists in the first part, synaptic still won't let me install the nvidia-173 package, because it wants "xorg-video-abi-10", which doesn't seem to be anywhere. 

Anybody able to help?

---

### Post by ZPField on 2012-07-01
Hey Guys.  I don't think this is just a Unity problem.  I'm running 12.04 with Gnome 3.4.1 and the Nvidia drivers for my 5200 refuse to install.  I think it's a problem with Ubuntu 12.04 itself.  On my old version (10.10) it installed perfectly and I had no problems with it.  I Tried installing from the Nvidia website and through Synaptic, but It wouldn't install.  Now Synaptic is telling me that the package is broken, but cannot fix it.  I think that we may just have to face the fact that the Nvidia Geforce 5200's are to old to be supported by the 'new' Ubuntu.

---

### Post by Yellow Pasque on 2012-07-01
As stated before, it's a known issue. [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173/+bug/948053](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173/+bug/948053)
Which driver did you download from nvidia site? You need the new 173.14.35 driver. 

Here is the link for 32-bit: [ftp://download.nvidia.com/XFree86/Linux-x86/173.14.35/NVIDIA-Linux-x86-173.14.35-pkg0.run](ftp://download.nvidia.com/XFree86/Linux-x86/173.14.35/NVIDIA-Linux-x86-173.14.35-pkg0.run)

Link for 64-bit: [ftp://download.nvidia.com/XFree86/Linux-x86_64/173.14.35/NVIDIA-Linux-x86_64-173.14.35-pkg0.run](ftp://download.nvidia.com/XFree86/Linux-x86_64/173.14.35/NVIDIA-Linux-x86_64-173.14.35-pkg0.run)

---

### Post by BLTicklemonster on 2012-07-15
I'm having this same problem, except it's a pci card, not agp.
e-Geforce FX5200 128  MB PCI. It has dvi out which is what I want.

From what I see here, I ought to just dump 12.04 and install 11.10 and wait it out?

How about the drivers in the previous post, anyone try them?

I also have an old nvidia agp card that says nothing about what it actually is. It has DVI out also, plus vga. Anyway, neither card will work with 12.04, and the onboard video card on this old clunker isn't setting any woods on fire, either.

(Not at all impressed with 12.04. I have a sound blaster card that it doesn't load drivers for either.)

I guess I'll fiddlefart around a little and see if I can get them going on 12, if not, I'm going back to 11 and wait til I hear any positive news. Can't afford any new stuff, and hoped Ubuntu wouldn't run off with us old poor govt employees! :)

---

### Post by BLTicklemonster on 2012-07-27
I got lucky and had someone give me a newer motherboard / cpu and memory. The board has nvidia geforce 7025 onboard video, so 12.04 is working okay.

I'd tried everything, but nothing gave me decent video. Even tried going back to the prior version of xorg, nothing worked.

So, is it Nvidia who should respond to ubuntu's new stuff, or should ubuntu have not taken off without support? Or is it xorg or x11 or whatever that's at fault?

---

### Post by Yellow Pasque on 2012-07-27
It's mostly nvidia's fault for taking their sweet time to update the legacy driver for Xserver 1.11 (though at least they do update their legacy blob driver which is more than you can say for AMD). Also, Ubuntu could have updated Precise to 173.14.35 once it was released.

---

### Post by r233967 on 2013-03-20
The following simple steps worked for me for version 12.04.02 on March 19, 2013.


- Install 12.04.02 (DO NOT enable auto login).
- When the install finishes rebooting, you will be at the login screen (DO NOT LOGIN).
- CTRL-ALT-F1 to get to a command-line.
- login at the command prompt
- sudo apt-get install nvidia-173-updates (DO NOT INSTALL nvidia-173)
- reboot
- enjoy

---

