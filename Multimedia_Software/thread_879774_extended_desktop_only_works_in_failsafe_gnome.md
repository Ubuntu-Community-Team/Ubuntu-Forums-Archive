---
title: "extended desktop only works in failsafe gnome"
date: 2008-08-04
forum: Multimedia Software
---

### Post by PewterHydra on 2008-08-04
'ello, 

I've got an ATI Radeon and two monitors, I had it all set up with a dual-head configuration. There's a second video card installed so that I can use three monitors when in Windows (I've given up trying to make that work in Linux for now). Things were fine until I decided to give the tri-monitor setup another go and in the course of things reinstalled my ATI driver. Since then, despite replacing the xorg.conf with the old, working one my 8.04 installation will only boot in failsafe gnome. Failsafe looks perfectly normal, I can't imagine what is different since I have no custom startup scripts on this machine. If I try to use the normal session I get the following details after the 'you've logged out before ten seconds' message: 

```
Setting IM im_switch for locale=en_CA
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinput.d/default
```

Oh, there is no 'session' file in ~/.gnome2. Weird eh? 

Anybody have an idea what my problem is?

Edit: I'd originally installed the ATI driver when using Feisty, and upgraded to Hardy shortly after it came out without any problems, and had been using that setup for several months before this happened. I've got a ton of applications and environment tweaks on this system and would pretty much have to spend the rest of the week reinstalling things and resetting permissions/passwords if I did a clean install, so that's just not gonna happen anytime soon.

---

### Post by markbuntu on 2008-08-04
You should look in one of your old Xorg.0.log. It will tell you what went wrong with the driver. Look for lines that start with (EE).

Also, the newest 8.7 driver from ati has support for multiple ati cards through aticonfig. Type 

aticonfig --help 

to get a list of options. 

xorg.conf is being deprecated and fglrx does not use it unless you force it to. There is more info in the forums at cchtml.com. There is no xorg.conf in Intrepid.

---

### Post by PewterHydra on 2008-08-04
> **markbuntu said:**
> You should look in one of your old Xorg.0.log. It will tell you what went wrong with the driver. Look for lines that start with (EE).

Also, the newest 8.7 driver from ati has support for multiple ati cards through aticonfig. Type 

aticonfig --help 

to get a list of options. 

xorg.conf is being deprecated and fglrx does not use it unless you force it to. There is more info in the forums at cchtml.com. There is no xorg.conf in Intrepid.

I can't find anything named Xorg.0.log, or anything ending in .log in the X11 directory. Where should I find this file? 

Also: cchtml.com is a web design site and says nothing about xorg or fglrx, nor does it have a link to any forums, and there's nothing at forums.cchtml.com either. (?)

Edit: Answers To My Own Questions

A) My problem was that (for reasons I can't fathom) the default session changed to something which I don't know from ordinary Gnome. I specified Gnome as the session to use (even though I thought it was default) and it gave me the message "Set Gnome as your default session?" ... which was my first clue that the answer here had nothing to do with the video card or drivers. I set Gnome as default and the problem went away. Perhaps the default session got reset in the course of reinstalling the driver? 

B) The forums of which markbuntu speaks can be found at wiki.cchtml.com 

C) One can see the Xorg.0.log in the System > Administration > System log gui. 

Also: Yay for Intrepid Ibix not using xorg.conf! That makes me filled with all manner of happy.

---

### Post by markbuntu on 2008-08-05
Your log files are in var/log. You can also use System/Administration/System Log to view them. 

You can start here to get the latest ati driver:

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

There are some forums here that discuss the driver.

[http://forum.compiz-fusion.org/showthread.php?t=6794](http://forum.compiz-fusion.org/showthread.php?t=6794)

You can also check out phoronix.

---

