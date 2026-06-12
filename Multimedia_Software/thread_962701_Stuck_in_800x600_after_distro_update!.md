---
title: "Stuck in 800x600 after distro update!"
date: 2008-10-29
forum: Multimedia Software
---

### Post by b0z0dcl0wn on 2008-10-29
I have been using ubuntu on this desktop for a while now. Last time I updated to 8.04 it broke my video too, but then I just edited the xorg.conf and everything was ok. Now it's not working.  I have an GeForce Ti4200 video card, and none of the nvidia drivers have ever seemed to work... But i've always been able to use the nv driver for higher resolutions. Any help on configuring video drivers and displays in 8.10 would be appreciated!

---

### Post by xc3RnbFO8P on 2008-10-29
Try this,
ALT-F2  **gksudo gnome-display-properties**

---

### Post by Jim Lewis on 2008-10-29
Well, I'm someone else, but I have the same problem.  I ran the command you suggested and got the same thing I get when I look in System-Preferences-Screen Resolution.  The highest it offers is 800x600, and I've had this at MUCH higher resolution in Windows and with Ubuntu when I was running a dual boot system.

---

### Post by freakzilla on 2008-10-29
I've been having a similar problem.  I've made some progress through trial and error.  I had to reinstall the "linux-restricted-module" in synaptic, then re-enable my nvidia drivers under system>administration>hardware drivers.  Finally i used the command "gksu displayconfig-gtk" suggested by Ringi in another thread to choose my dispaly specs.

---

### Post by b0z0dcl0wn on 2008-11-03
> **Ringi said:**
> Try this,
ALT-F2  **gksudo gnome-display-properties**

that only takes me to the Screen Resolution tweaker found in system, preferences. It doesn't give me any other options than 800x600 or 640x480. I really don't want to go lower. 

I tried the restricted drivers option, there is no restricted drivers in use it says.  Is there anyway to set up which driver xorg uses anymore? It used to be defined in xorg.conf right?

---

### Post by mmcmonster on 2008-11-03
Try changing "nv" to "vesa" in /etc/X11/xorg.conf.  [This bug]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-177/+bug/282214") may be similar to your problem (but involves the nvidia geforce 6100 card) and so does [this thread]("http://ubuntuforums.org/showthread.php?p=6075129").

---

### Post by b0z0dcl0wn on 2008-11-03
> **mmcmonster said:**
> Try changing "nv" to "vesa" in /etc/X11/xorg.conf.  [This bug]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-177/+bug/282214") may be similar to your problem (but involves the nvidia geforce 6100 card) and so does [this thread]("http://ubuntuforums.org/showthread.php?p=6075129").

looks like it is set to vesa now.  I guess I will try nv instead.  I thought the xorg.conf file wasn't really relevant anymore with the new changes? Thanks for the suggestions!

---

### Post by b0z0dcl0wn on 2008-11-03
> **b0z0dcl0wn said:**
> looks like it is set to vesa now.  I guess I will try nv instead.  I thought the xorg.conf file wasn't really relevant anymore with the new changes? Thanks for the suggestions!

Okay okay! switching to NV gave me more options for resolutions... unfortunately all of them are smaller than 640x480 even. Is there a way I can tell Ubuntu that i've got a 21 inch monitor that supports up to 1600x1200?  

"sudo dpkg-reconfigure xserver-xorg" used to ask you about your monitor and video, now it just asks about your input devices...

---

### Post by b0z0dcl0wn on 2008-11-03
Okay so in /etc/X11/ I found a file named xorg.conf.dist-upgrade200810211459. I backed up the xorg.conf I was using now, and cped the old one ontop of xorg.conf. restarted, and i'm back in the big world. Ahh it's nice to have real estate again!

---

