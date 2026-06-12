---
title: "Video driver broken.  Can't get correct drivers to install."
date: 2012-12-04
forum: Multimedia Software
---

### Post by patriot56 on 2012-12-04
Hello forum.
I recently installed Linux Mint 13 - Maya on this old IBM with an Nvidia GeForce MX 440 video card in it.  Both of the items mentioned here are 10 years old - *they probably should be in a museum*.  Everything was working fine, but then I started having some unusual video issues in a game that I was playing (Oolite, a Elite clone).  These video issues (missing chunks of graphics, artifacts, very slow frame rates, video freezing, as well as causing system crashes) migrated into several screensavers as well.

All of this seemed to happen suddenly.

When attempting to load the correct drivers from the Package Manager, I am alerted that the current status of the package is "[COLOR=#ff0000]BROKEN[/COLOR]"[COLOR=#ff0000]!  [/COLOR]and won't install.  The driver for this Legacy video card is the 96.43.xx series which is for the GeForce4 MX 440 (among others) but Nvidia has discontinued support for this driver according to their web site.

Using the Terminal, I entered the following: 
```
sudo apt-get install mesa-utils
```This reports that the current ver. is already installed. 

When I entered the command, ```
glxinfo
``` the computer rebooted immediately.
I have since been able to successfully enter the command.  The output of that command is quite long so I didn't include it with this post.  If it is needed, I will add it in my reply.


I attempted to install the correct drivers using the Additional Drivers menu item but it displays this: [COLOR=#ff0000]**SystemError: E:Unable to correct problems, you have held broken packages.**[/COLOR]
And I have no idea how to repair or remove these broken packages except to use the Package Manager --> Edit --> Fix Broken Packages.  Which I did.  It didn't work.

My display is currently at something like, 600 x 400 (it may be 800 x 600 but I don't think so) and I can't seem to get it back to its original 1280 x 1024.

The window manager is xfce. If that is important.

If anyone can help, please do.  My next option is to reinstall.  I really don't want to do that if I don't have to.:sad:

Thank you in advance.

---

### Post by BicyclerBoy on 2012-12-04
What makes you say the legacy drivers are not supported?
The facts suggest the opposite. 

nVidia maintains 1 current & 3 legacy driver series.
96.43.23 was updated in Sept 2012 to support the later Xorg..
In the driver archives you can find all the previous releases of 96.xx series.

The symptoms you tabled sound like h/w failure (GPU memory or PSU).

You could determine the Xorg version etc from the log file:
/var/log/Xorg.0.log

Do [you have | does your distro have] synaptic package manager installed?
Your broken packages problem will be more obvious in synaptic.

May be your distro is using the non-updated nVidia legacy driver.

---

### Post by patriot56 on 2012-12-04
> **BicyclerBoy said:**
> What makes you say the legacy drivers are not supported?
The facts suggest the opposite. 

nVidia maintains 1 current & 3 legacy driver series.
96.43.23 was updated in Sept 2012 to support the later Xorg..
In the driver archives you can find all the previous releases of 96.xx series.
I went to NVidia's web page to look for the correct driver.  They had a link titled "[_What is a Legacy GPU_]("http://www.nvidia.com/object/IO_32667.html")"?

If you visit this link you will find four (4) groups of GPU's that are apparently supported by the current NVIDIA drivers.
Two of the four are listed as unsupported; "The ** 96.43.xx** driver supports the following set of GPUs:
  *Note: Support for the 96.43.xx series is discontinued. No further releases from  this series are planned.*"
And
**"The  71.86.xx driver supports the following set of GPUs:**
  [I]Note: Support for the 71.86.xx series is discontinued. No further releases from  this series are planned."

[/I]If I have misread this or am not understanding, then I apologize.  :(

I agree with you however.  The facts would indeed seem to suggest the opposite.

> **BicyclerBoy said:**
> The symptoms you tabled sound like h/w failure (GPU memory or PSU).
That  is exactly what I was afraid of.  Unfortunately, I am forced to agree.   I was hoping though, that it was a driver issue.   But the fact remains  that the card is 10 years old and while I don't care about loosing the card, it is in a machine that is just as old and I am just not interested in spending any money on it. :)  It is just a test machine anyhow.
> **BicyclerBoy said:**
> You could determine the Xorg version etc from the log file:
/var/log/Xorg.0.log
That is a good idea.  I will look at the log and post back if there is anything to post.
> **BicyclerBoy said:**
> Do [you have | does your distro have] synaptic package manager installed?
Your broken packages problem will be more obvious in synaptic.
Yes,  I do have Synaptic Package Manager installed and I used it to try to  "fix" the broken packages but when I attempt to install the suggested  Nvidia driver using the Additional Drivers menu item I still get the  error that I mentioned in my OP.

I have even tried.....
```
$  sudo apt-get update && sudo apt-get upgrade && sudo  apt-get clean && sudo apt-get clean --purge
```I like cleaning up the packages after updating.  And I also used...
```
$ sudo apt-get autoclean
```hoping to get rid of any broken packages.

Thank you BicyclerBoy, for your help. 
It is greatly appreciated.

---

### Post by BicyclerBoy on 2012-12-07
I have an old (was working) AGP MX440 avio lying in a box somewhere, in anti-static bag of course.
I'd give it away to a good home except for the tyranny of distance.
You could prob find a "gold coin donation" one somewhere.

nVidia are not continuing to develop the legacy series but have re-compiled to allow them to work with later Xorg.
That's a lot more than the "other" brand.

AFAIK There were **some** AGP version of the 8400GS or GT.
Note there are 3 different versions of 8400GS
Was a good HTPC video card about 6 years ago.

Synaptic should let you select packages by status, than try to ungrade & see what error messages it outputs.
You can access the install/upgrade log file from synaptic menus..

---

