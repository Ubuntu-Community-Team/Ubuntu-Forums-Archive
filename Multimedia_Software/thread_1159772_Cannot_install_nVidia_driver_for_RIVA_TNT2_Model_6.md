---
title: "Cannot install nVidia driver for RIVA TNT2 Model 64/Model 64 Pro"
date: 2009-05-15
forum: Multimedia Software
---

### Post by superthin on 2009-05-15
Hello,

I have read about 50pages / topic all over the Internet to get help for installing driver for my old RIVA TNT2 Model 64/Model 64 Pro (4x 32MB) with Ubuntu 8.10 but I am not successful.

What did I do?
Try envy, envyng => failed.
Go to [http://www.nvidia.com/object/linux_display_x86_71.86.09.html](http://www.nvidia.com/object/linux_display_x86_71.86.09.html) to download newest driver => failed in final.
Add repository from avenard.org (I don't remember which pages I read) => failed.

At the end of my process, I met: [http://www.nvnews.net/vbulletin/showpost.php?p=1839149](http://www.nvnews.net/vbulletin/showpost.php?p=1839149) (post no. = 6) . I am being despondent now. I cannot return Ubuntu 8.04 because many of softwares will be died.

Who can install successful? Tell me how, please.

Thanks in avandce.

---

### Post by rukiaEnix on 2009-05-15
Try installing the driver nvidia-glx-legacy, it supports TNT, TNT2 and older GeForce.
You can download it from Synaptic.

---

### Post by superthin on 2009-05-15
> **rukiaEnix said:**
> Try installing the driver nvidia-glx-legacy, it supports TNT, TNT2 and older GeForce.
You can download it from Synaptic.

Ubuntu 8.10 seems to removing this package.

```
sudo apt-get install nvidia-glx-legacy
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package nvidia-glx-legacy is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  nvidia-glx-180 nvidia-glx-96 nvidia-glx-177 nvidia-glx-173 nvidia-glx-71
E: Package nvidia-glx-legacy has no installation candidate
```
:(

What should I do?

---

### Post by rukiaEnix on 2009-05-15
Check your repositories and see if you have this entry: 
```
deb http://security.ubuntu.com/ubuntu hardy-security main multiverse
```

because there you can find the driver I told you

---

### Post by peter_nz on 2009-11-14
Hi I same nvidia riva tnt2 vid card and Just installed Karmic Koala 9.10
I added the repository from your post and yes the driver is indeed in that repo BUT
cant install besause missing dependencies. see terminal output.

peter@peter-desktop:~$ sudo apt-get install nvidia-glx-legacy
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  nvidia-glx-legacy: Depends: linux-restricted-modules-common but it is not installable
                     Depends: xserver-xorg-core (>= 1:0.99.0-1) but it is not going to be installed
E: Broken packages
peter@peter-desktop:~$ 

So how can we get the missing dependencies?.
Anyone know?

---

### Post by HappyFeet on 2009-11-14
You need to fix your broken packages first.

```
sudo dpkg --configure -a
```
```
sudo apt-get install -f
```

---

### Post by rukiaEnix on 2009-11-15
try this driver instead it also supports RIVA TNT2 model 64:

nvidia-glx-71

I have it in the jaunty repos but I think it should also work for karmic here it is if you don't have it:

```
 
deb http://mirrors.kernel.org/ubuntu jaunty main restricted
 
```but have you check the hardware drivers at System->Administration? maybe ubuntu has already detected it and you just have to enable it.

---

### Post by peter_nz on 2009-11-15
Thanks for your reply well I added the jaunty repo and installed nvidia-glx-71
and terminal says I did see below

peter@peter-desktop:~$ sudo apt-get install -f nvidia-glx-71
Reading package lists... Done
Building dependency tree       
Reading state information... Done
nvidia-glx-71 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
peter@peter-desktop:~$ 

I have rebooted and checked in the hardware drivers for proprietry drivers and dosent show there.
Its there but it isn't Hmmmm...  ?

I goto display settings and system asks if i want to use the vendors video application  I say yes but then get the problem 
You do not appear to be using the NVIDIA X DRIVER please edit your X Configuration file (just run `nvidia-xconfig` as root and restart the x server 

Unfortunatly I searched for nvidia-xconfig and its hiding real good if it is on my computer.
Any ideas ?

---

### Post by Vandyk on 2009-11-15
Hi, i have the same problem whit the same card, and i also have the same error's than peter_nz, but im using Kubuntu Karmic.

I also need your help

---

### Post by realzippy on 2009-11-15
This card is not pretty new.From this thread:


*Old Nvidia video chipsets are not supported by Ubuntu past version 8.04 (maybe earlier?) - you can still install an older Ubuntu LTS version that will support your hardware and remain supported for a few years yet.*

[http://www.uluga.ubuntuforums.org/showthread.php?p=7535646](http://www.uluga.ubuntuforums.org/showthread.php?p=7535646)

---

### Post by rukiaEnix on 2009-11-15
Just type in the terminal:

```
 sudo nvidia-xconfig 
```

don't search for it just type it but or have you already done it?

or try installing this: envyng-core or envyng-qt is at synaptic
it will download the lates ATI or NVIDIA driver, it may work -.-

---

