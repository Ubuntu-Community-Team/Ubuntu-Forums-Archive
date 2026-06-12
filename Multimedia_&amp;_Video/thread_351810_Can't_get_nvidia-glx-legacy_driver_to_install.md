---
title: "Can't get nvidia-glx-legacy driver to install"
date: 2007-02-02
forum: Multimedia &amp; Video
---

### Post by landrand on 2007-02-02
I'm a Gentoo and Archlinux user and I thought I'd give Ubuntu Edgy a try.  I'm having a heck of a time getting the nvidia legacy drivers to install.  I've followed the howto's and read several posts, but no luck.  I have a GeForce2 GTS card installed which is a candidate for the legacy driver.

No matter what I do, when I try to install, I get the following error:

root@ubuntu-ws:/home/lind# apt-get install nvidia-glx-legacy
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package nvidia-glx-legacy is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package nvidia-glx-legacy has no installation candidate

When I try the graphics installer, I get this message when I just select the Nvidia legacy driver.

NVidia binary X.Org 'legacy' driver
NVidia binary X.Org 'legacy' driver cannot be installed on your computer type (i386). Either the application requires special hardware features or the vendor decided to not support your computer type.

I'm not sure why it refuses to install on my computer type i386.  My running kernel is the generic. 
Here's my running kernel.
uname -r
2.6.17-10-generic

Here's my /etc/sources.list

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

I've tried installing the regular nvidia-glx driver but that doesn't work either.  Here's the the install ouput as well as the xorg.log when I restarted the Xserver.

root@ubuntu-ws:/home/lind# apt-get install nvidia-glx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  nvidia-kernel-source
The following NEW packages will be installed:
  nvidia-glx
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/4066kB of archives.
After unpacking 12.6MB of additional disk space will be used.
Selecting previously deselected package nvidia-glx.
(Reading database ... 91096 files and directories currently installed.)
Unpacking nvidia-glx (from .../nvidia-glx_1.0.8776+2.6.17.7-10.1_i386.deb) ...
Setting up nvidia-glx (1.0.8776+2.6.17.7-10.1) ...

Here's the /var/log/Xorg.log showing the errors when I try to restart the X server.

II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "ramdac"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Any thoughts or help would be greatly appreciated.

---

### Post by MoLE on 2007-02-03
> **landrand said:**
> 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe


I take my hat off to you for being able to install Gentoo and ArchLinux, so I hope you won't take offence at the solution.

You need to enable the edgy multiverse repository - you currently have main, restricted, universe enabled.  Easiest way to do this is through the GUI, or you could just add universe and multiverse to the top two lines and comment out the second edgy universe entry lower down.

Then, its a simple matter of:
sudo aptitude update
sudo aptitude install nvidia-glx-legacy
sudo nvidia-glx-config enable

Let us know if this helps.

---

### Post by Mets on 2007-02-03
I have a similar question about the drivers, but I definitely can't install Gentoo :)  How exactly is this done?  Also, should it be main restricted, or just main for the first repository (what's the difference).  Thanks.

---

### Post by MoLE on 2007-02-03
> **Mets said:**
>  How exactly is this done?  Also, should it be main restricted, or just main for the first repository (what's the difference).

Cleverer people than me have already written a good howto on the differences between the repositories and why.  You'll find them in [the wiki]("https://help.ubuntu.com/community/Repositories/Ubuntu") and in the [official documentation]("https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/extra-repositories.html").

Once you have enabled these extra repositories and updated, you can use the above terminal commands for the nvidia-glx-legacy drivers or you can do a search using the synaptic package manager for nvidia,  which should bring up the relevant packages.

---

### Post by Arup on 2007-02-04
There is a problem installing nvidia legacy via synaptic or sudo aptitude, if one has the generic kernel, Ubuntu removes it and installs the i386 which has no SMP support, fine if one has a single CPU machine, bad news if you have dual, dual core etc. Wonder when Ubuntu will fix this. It installs fine with Envy but only the older .73 version, newer .8x series gives a md5 checksum error with Legacy drivers.

---

### Post by landrand on 2007-02-08
I gave up trying to install the legacy driver.  I'll reinstall and try again and make sure I have the correct repo's in my sources.list.

I think it's funny about the differences between Gentoo and archlinux and other easier distro's such as Ubuntu or Suse.  After trying out Ubunto and Suse 10.2, I found Gentoo and archlinux to be soooo much simpler and less troublesome.  Sure, it's a more difficult to install, but you learn so much about how everything works and you don't depend on so many extra's/scripts to suddenly make changes to the system.  Although Ubuntu is a great operating system for someone new to linux, it's kindof is a pain for someone who's used to getting "under the hood" and working on the internals.  I've also noticed that Ubuntu is not a responsive on the same hardware that runs Gentoo/archlinux.

---

### Post by C-A on 2007-02-08
Give [Envy]("http://albertomilone.com/nvidia_scripts1.html") a try!

---

### Post by Blenderdan on 2007-02-13
I figured out my mistake.  I didn't uninstall nvidia-glx-legacy and its components.  After they were uninstalled, I ran Envy again and now everything works fine!
THANKS! :D 

This was my post before I found my problem.
"After a day or 2 trying to setup my Nvidia drivers to be able to run Blender3D, Envy  seemed to be the magic bullet to my problems. After running envy everything seemed to be working without touching a config file.

Now my system mysteriously crashes.  If I Render a scene in Blender my computer will crash.  If I run Google earth for a while my computer will crash.  

My Previous installation of Ubuntu was stable and could be left running for days at a time.  I could render as many scenes as I wanted, I could run google earth,  Xgl etc...  

I am not sure what to do about this, but I am going to try to install the Nvidia Beta driver off their web site "again" and see if I can get it working."

---

### Post by MoLE on 2007-02-13
This sounds much more like a heat problem than a driver problem.  If you can run Blender and GoogleEarth, then OpenGL is certainly working correctly, which suggests the drivers are installed.  Crashing after running for a while is well-known in overclockers circles as being a heat issue.

---

### Post by Blenderdan on 2007-03-18
My system has been running fine ever since.  It was because I didn't uninstall the nvidia-glx-legacy driver before running Envy. No heat problem, or other hardware issues. I leave my system running 24/7 much of the time.

Thanks again. :D

---

