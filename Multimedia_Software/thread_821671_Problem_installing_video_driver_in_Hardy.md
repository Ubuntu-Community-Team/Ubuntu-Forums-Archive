---
title: "Problem installing video driver in Hardy"
date: 2008-06-07
forum: Multimedia Software
---

### Post by atman on 2008-06-07
I have an Athlon 64 3000+ with an ATI Radeon HD2400 video card.  I installed Hardy recently and was looking around on how to get the card working right.  I found a wiki at cchtml.com that had a walk through on installing the driver.  I got about half way through and then got an error.  I rebooted and now I only get a blank white screen with the arrow.  Here is what I typed in:

[I]sudo apt-get update

sudo apt-get install linux-restricted-modules-generic restricted-manager

sudo apt-get install xorg-diver-fglrx

sudo depmod -a

sudo gedit /etc/X11/xorg.conf[/I]

This is where I get the error.  It comes up with:

[I]cannot open display
Run 'gedit --help' to see a full list of available command line options[/I]

I'm still quite new with Linux and am trying to learn it when I get time.  Any ideas how to get my video working again?  Thanks.

---

### Post by Pjotr123 on 2008-06-07
Try applying this how-to:
[http://ubuntutip.googlepages.com/thefirstthingstodo](http://ubuntutip.googlepages.com/thefirstthingstodo)
(number 2 )

---

### Post by atman on 2008-06-07
Thanks, but I can't even get into the desktop.  I get to the log in screen, I log in and it goes to a solid white screen.  The cursor is there, but nothing else.  I can log into save mode and to the command prompt.  Any ideas what I did and how I can get it fixed?  Thanks.

---

### Post by Pjotr123 on 2008-06-07
You can still boot in Recovery Mode: have you already done this option: 
Try to fix X-server

---

### Post by atman on 2008-06-07
I tried the fix X-sever option and it still didn't fix it.  Still the blank white screen.

---

### Post by atman on 2008-06-09
I'm still having this problem and hoping someone could help me out.  Thank you.

---

### Post by Yellow Pasque on 2008-06-09
If you want to try to salvage your current driver install, use vim to edit text files in the console. Press 'i' when you first enter the file to enter text editing mode. When you are finished, press 'Esc' and type **:x[Enter]** to save changes.

If you want to give installing the driver another go:
```
sudo apt-get remove xorg-driver-fglrx
```

If you can't get the fglrx/Catalyst driver to work, check out the radeonHD link in my sig.

---

### Post by markbuntu on 2008-06-09
If you can get the login screen you can get the gnome desktop by clicking on the little icon on the bottom left of the login screen and choosing change session and gnome safe mode. You should be able to login and get to the desktop with that.

Then you should remove fglrx completely with synaptic and then rebooot and reinstall it. Alternatively, after you reboot, you can go to System/Administration/Hardware Drivers and choose enable for the restricted driver.

If you really really need the latest driver and how to set it up etc. go here:

[http://forum.compiz-fusion.org/showthread.php?t=6794](http://forum.compiz-fusion.org/showthread.php?t=6794)

But, if your video is working with the driver form the Ubuntu repo don't mess around with it.

Anyway, editing your xorg.conf file is not a task taken lightly as you will find out if you follow the link.

---

