---
title: "Compaq CQ60-418DX nVidia 8200m - strange issue"
date: 2009-08-24
forum: Multimedia Software
---

### Post by Lord Landis on 2009-08-24
Hi everyone.  I just purchased a new compaq cq60-418DX, and I'm getting some very aberrant behavior when I install the proprietary nVidia drivers.  The laptop has an HP High Definition LED display (manufactured by AUO) that is supposed to function at 1366x768, but it simply won't do that.

On a virgin install of 9.04x64, I have relatively 'normal' resolutions, though the display lags due to a lack of acceleration.  Once I install the nVidia drivers (173, 177, or 180), regardless of whether I pull them from the repos or from nVidia themselves, my X session fragments into 6 cramped little replicants of itself, stacked 3 high and 2 wide, with about an inch of black space between them.  If I could attach a screenshot in any way, I would...

I've spent about six hours searching for any answers to this, and I've yet to find anything that works.  I've installed six or seven different builds of the drivers, I've added modelines to my Xorg.conf (provided by runnin g'gtf 1366 768 60'), and I've tried using Envy - in every case the results are the same - no joy, just 6 cramped copies of my screen on one display.

Now, I've tried using the 'nvidia-settings' tool, and it seems to think that the monitor is only capable of 640x480.  There's no way that I can change this through the normal nvidia tool...  I've heard that this could be due to corrupt EDID files, but I really have no clue how to fix those, or even where to find the correct information.

Any help that anyone can provide would be greatly appreciated.  I really hope that the answer isn't 'deal with the generic driver', but if that's what it comes down to, well, so be it.

To help, I've attached the contents of my current Envy-created xorg as well as the one I added the modelines to on this post.

---

### Post by Lord Landis on 2009-08-24
Okay, so after another five or six hours of research, it turns out that the solution is far more simple than I had anticipated...  In xorg.conf, under "Devices", you just have to add a line that reads

```
Options "ModeValidation" "NoTotalSizeCheck"
```

I found this nugget of information in another forum that, unfortunately, I can't remember the URL of right now...

Now I have X running with the nVidia drivers in a nice, full, 1366x768 window.  

There's a new issue, however, and that's that I can't resize the panel or else it crashes KDM and I have to reboot.  I'm going to try using the nVidia 190 Beta drivers to see if this fixes it.  At least I'm making progress, so if things continue to go strangely, I can easily get back to a mostly functional state.

More updates to follow.

---

### Post by Lord Landis on 2009-08-24
Okay, so I managed to fix the bugginess associated with trying to resize the panel as well.  This was just a matter of uninstalling the Ubuntu-provided nvidia-glx-180 and replacing it with the official nVidia 190-series beta driver.

I'm happy now, and am looking forward to finishing out my install.

---

### Post by CleverTrick on 2009-08-27
Thank you! This solution worked PERFECTLY for my new laptop, which is the same model. I installed the Nvidia beta driver for good measure, and it's working very nicely with GNOME and Compiz. :) 
I was utterly baffled when I saw SIX screens pop up on the display, so again, I'm grateful that you posted this! 
The "Options" part of the code made X complain about parsing errors, so here's the code that worked for me: 
```
Option "ModeValidation" "NoTotalSizeCheck"
```

---

### Post by kickdrive on 2009-08-28
Did you have to do anything fancy to get the wireless on that machine working?

---

### Post by CleverTrick on 2009-08-31
Wireless worked out of the box. 

Suspend was not working until I edited /boot/grub/menu.lst by scrolling down to Mint's entry and adding pci=nomsi to the "kernel" line. *

The speakers buzz when no windows are open on the desktop, and I haven't found a solution to that yet.

*found that fix here: [http://blog.deliciousrobots.com/2009/08/10/suspend-fix-for-linux-on-a-compaq-cq60-215dx/](http://blog.deliciousrobots.com/2009/08/10/suspend-fix-for-linux-on-a-compaq-cq60-215dx/)

---

### Post by jocampo on 2009-09-04
> **Lord Landis said:**
> Okay, so I managed to fix the bugginess associated with trying to resize the panel as well.  This was just a matter of uninstalling the Ubuntu-provided nvidia-glx-180 and replacing it with the official nVidia 190-series beta driver.

I'm happy now, and am looking forward to finishing out my install.

Thanks a lot for taking the time and post this. I just got the same laptop and was having the same exact issue. Like the other forum friend, the one that worked for me was

```
Option "ModeValidation" "NoTotalSizeCheck"
``` 

I also got the option to update the WIfi driver but I am afraid of breaking the network connectivity which of course is vital for everything. Did you update or replace wifi driver as well? the available option is  ALternate Atheros ...

---

### Post by haeuslein on 2009-09-05
Thank you so much for this post! I thought I was going crazy when I saw that six-panel output... :D

Editing the xorg.conf with the "Option"-entry mentioned above did the trick.

---

### Post by SlothX311 on 2009-09-19
Thank you very much for putting the time into this post.  I have a CQ60-215DX which is essentially the same computer with less memory than yours, and I was having a hell of a time figuring out this re-size issue.  I used the 180 Nvidia drivers and was able to get the correct resolution, however on re-size, the system would crash and need to be hard booted.

---

### Post by SlothX311 on 2009-09-20
I was able to find the beta nvidia drivers on the website.  I am new to ubuntu and linux in general and I'm having a hard time executing (for lack of a less "microsoft" word) the driver package.

The package I downloaded is titled: "NVIDIA-Linux-x86-190.32-pkg1.run"

I get an error when try to double click this file as it is trying to launch it package in a program called "gedit."



I found this text on the nvidia website and I think it is the answer to my problem.  I guess I'm just looking for a translation as to what this means.

"Installation  instructions: Once you have downloaded the driver,   change to the  directory containing the driver package and install the driver by  running, as root, sh  ./NVIDIA-Linux-x86-190.32-pkg1.run"




Again I appologize for the stupid question.  I am still learning my way around the ubuntu OS.  Thank you guys for helping me with this driver problem.  I was able to find my answer at:
[http://ubuntuforums.org/showthread.php?t=990978](http://ubuntuforums.org/showthread.php?t=990978)

---

### Post by jocampo on 2009-09-21
> **SlothX311 said:**
> I was able to find the beta nvidia drivers on the website.  I am new to ubuntu and linux in general and I'm having a hard time executing (for lack of a less "microsoft" word) the driver package.

The package I downloaded is titled: "NVIDIA-Linux-x86-190.32-pkg1.run"

I get an error when try to double click this file as it is trying to launch it package in a program called "gedit."



I found this text on the nvidia website and I think it is the answer to my problem.  I guess I'm just looking for a translation as to what this means.

"Installation  instructions: Once you have downloaded the driver,   change to the  directory containing the driver package and install the driver by  running, as root, sh  ./NVIDIA-Linux-x86-190.32-pkg1.run"




Again I appologize for the stupid question.  I am still learning my way around the ubuntu OS.  Thank you guys for helping me with this driver problem.  I was able to find my answer at:
[http://ubuntuforums.org/showthread.php?t=990978](http://ubuntuforums.org/showthread.php?t=990978)

You don't have to compile or run anything :-) ... just update your Ubuntu this way

```

sudo aptitude update
sudo aptitude safe-upgrade

```

reboot is necesary... after that ... go to 

System>Administration>Hardware Driver

From there you just activate the Nvidia driver and reboot again. You will have problems with the initial setting but you are going to edit the X11 config and that's it

---

