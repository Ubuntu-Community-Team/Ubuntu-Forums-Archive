---
title: "Can not install nvidia-glx-new"
date: 2007-07-30
forum: Multimedia &amp; Video
---

### Post by PhishingJimi on 2007-07-30
I was trying to follow this guide on how to install the nvidia drivers, since my previous install doesnt seem to produce a correct a proper xorg.conf file. 

[http://doc.gwos.org/index.php/Latest_nvidia_feisty](http://doc.gwos.org/index.php/Latest_nvidia_feisty)

I got up to this line:

sudo apt-get install nvidia-glx-new

Then my terminal gave me an error: 
> 
The following NEW packages will be installed:
  nvidia-glx-new
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/4833kB of archives.
After unpacking 14.7MB of additional disk space will be used.
(Reading database ... 141649 files and directories currently installed.)
Unpacking nvidia-glx-new (from .../nvidia-glx-new_1.0.9755+2.6.20.5-16.29_i386.d
eb) ...
dpkg: error processing /var/cache/apt/archives/nvidia-glx-new_1.0.9755+2.6.20.5-
16.29_i386.deb (--unpack):
 trying to overwrite `/usr/bin/nvidia-settings', which is also in package nvidia
-settings
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/nvidia-glx-new_1.0.9755+2.6.20.5-16.29_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Does anyone know what could be wrong here?

Any help would be greatly appreciated.

---

### Post by MrHippocampus on 2007-07-30
Looks like its saying that the "nvidia-settings" package is blocking the nvidia-glx-new package from being installed. Try uninstalling the nvidia-settings package and then try again (the nvidia-glx-new should have nvidia-settings built in).

---

### Post by rocknrolf77 on 2007-07-30
Maybe it will install if you try aptitude instead of apt-get...

---

