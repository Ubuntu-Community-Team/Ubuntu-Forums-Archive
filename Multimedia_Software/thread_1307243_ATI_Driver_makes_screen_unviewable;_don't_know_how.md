---
title: "ATI Driver makes screen unviewable; don't know how to reverse"
date: 2009-10-30
forum: Multimedia Software
---

### Post by fox.esq on 2009-10-30
I tried to install the ATI driver so I can adjust my screen resolution more readily, but now I get an unviewable screen that I can't log into and can't operate Ubuntu 9.04 with.  I've tried different methods to reverse it, such as booting in safe mode and trying the graphics fix, but it won't work.  I'm using an ATI x1650 card.  Is there a way to boot the system up so that it won't engage the new driver?  Isn't the point of 'safe mode' to be able to start up your system and access it so you can undo harmful changes and access files as opposed to just resuming normal boot? - what a short-sighted and lame setup btw! I at least need some way to access the disk to pull important files off of it.

---

### Post by AKADAP on 2009-10-31
> **fox.esq said:**
> I tried to install the ATI driver so I can adjust my screen resolution more readily, but now I get an unviewable screen that I can't log into and can't operate Ubuntu 9.04 with.  I've tried different methods to reverse it, such as booting in safe mode and trying the graphics fix, but it won't work.  I'm using an ATI x1650 card.  Is there a way to boot the system up so that it won't engage the new driver?  Isn't the point of 'safe mode' to be able to start up your system and access it so you can undo harmful changes and access files as opposed to just resuming normal boot? - what a short-sighted and lame setup btw! I at least need some way to access the disk to pull important files off of it.

You need a root login to use any of the recovery stuff. The default Ubuntu setup does not include a root login.
To get around this screwup, I have used putty on a windows box to SSH to the affected computer, login and uninstall the ATI driver. To do this change to the /usr/share/ati directory and type: sudo ./fglrx-uninstall.sh

I have had the trouble you describe (monitor shuts down, keyboard dead) both on an install of an ATI driver and an uninstall. On an uninstall, one instead navigates to where the driver install program is and runs that under sudo to reinstall the driver.

---

### Post by Joe Ker1086 on 2009-10-31
I also have a similar problem with ATI drivers. It tells me that it can run better if I install the drivers but then just throws up an error when I do. I found it worked better to actually download the ATI drivers from the website and install but this was back on jaunty.

---

### Post by Random-penguin on 2009-10-31
I agree. The latest ATI driver for Linux is a vast improvement for my system. I was getting various screen corruptions that are now fixed. The AMD site gives a good guide of how to install their drivers. I still have to turn off visual effects to get Google Earth to play nicely; but hey!

---

### Post by fox.esq on 2009-11-01
> **AKADAP said:**
> You need a root login to use any of the recovery stuff. The default Ubuntu setup does not include a root login.
To get around this screwup, I have used putty on a windows box to SSH to the affected computer, login and uninstall the ATI driver. To do this change to the /usr/share/ati directory and type: sudo ./fglrx-uninstall.sh

I have had the trouble you describe (monitor shuts down, keyboard dead) both on an install of an ATI driver and an uninstall. On an uninstall, one instead navigates to where the driver install program is and runs that under sudo to reinstall the driver.

So let me be clear on what you are directing me to do: When I boot up in safe mode I choose the root login; then when I get the command prompt I type: /usr/share/ati   Then when the next thing comes up I type: sudo ./fglrx-uninstall.sh   and that should allow me to start things up without the new ATI driver engaged and screwing things up, right?  Sorry, I've never been good at command prompt stuff, it has always befuddled me, so I generally ask for very specific, step-by-step instructions.

Thanks a bunch, btw, for your help!

---

### Post by Odemia on 2009-11-01
Running /usr/share/ati/fglrx-uninstall.sh should get rid of the fglrx package.  If you used synaptic/apt-get/aptitude (or the restricted driver installer) to intsal the fglrx driver.  You can also use "sudo apt-get remove xserver-xorg-video-fglrx" from a command line to remove it.

Once you remove it I suggest running "sudo dpkg-reconfigure xserver-xorg" in the command line or "xfix" from the recovery mode.  Both will reconfigure the system to stop trying to load the fglrx driver.

Hope that helps.

FYI:  Be careful when you say "ati driver" when you really mean "fglrx driver"/"ati's proprietary driver".  There is actually a xserver-xorg-video-ati package that pulls in the open source "radeon" driver.

---

### Post by fox.esq on 2009-11-01
I tried going into the root command via safe mode and typed in the stuff people gave me but nothing worked.  The ATI driver I'm talking about is the one you get off of the remove/add applications menu.  It's is the only one there I'm aware of.  I would love to be able to go in and look up exactly what driver I'm talking about, but I can't ergo I'm here.

Let me reiterate: I CANNOT get into Ubuntu, instructions must be geared for use in something I can pull up in safe mode.

Please give detailed instructions, e.g.:

a. what do I type in first
b. then what do I type in 
c. after that, if something else comes up, then what do I type.

Thanks!

---

### Post by AKADAP on 2009-11-01
> **fox.esq said:**
> So let me be clear on what you are directing me to do: When I boot up in safe mode I choose the root login; then when I get the command prompt I type: **[COLOR="Red"]cd[/COLOR]** /usr/share/ati   Then when the next thing comes up I type: sudo ./fglrx-uninstall.sh   and that should allow me to start things up without the new ATI driver engaged and screwing things up, right?  Sorry, I've never been good at command prompt stuff, it has always befuddled me, so I generally ask for very specific, step-by-step instructions.

Thanks a bunch, btw, for your help!

Missing part of command added in red. But yes, this worked for me, though, I did it through SSH since I did not have a root login set up at the time, so I could not log into the safe mode.

edit:
Looks like I'm giving advice to fix stuff you didn't do. What I told you to do only works if you had downloaded and installed the driver from ATIs web site.

---

### Post by fox.esq on 2009-11-01
> **AKADAP said:**
> Missing part of command added in red. But yes, this worked for me, though, I did it through SSH since I did not have a root login set up at the time, so I could not log into the safe mode.

edit:
Looks like I'm giving advice to fix stuff you didn't do. What I told you to do only works if you had downloaded and installed the driver from ATIs web site.

I'll go ahead and give it a try and see if it will do something; can't hurt... can it?

---

### Post by fox.esq on 2009-11-01
The command prompt in root did not work.  It could not find the file or directory.  It was worth a shot though.  I'm guessing I need to type something similar to what you said, except specific to the driver I installed.

If someone could find it and tell me what exactly to type etc, I would really appreciate it!

---

### Post by pme 72 on 2009-11-01
There are instructions for removing the fglrx driver here:

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

Scroll down to "Removing the proprietary fglrx driver". 

I booted into Recovery mode, got to a command prompt and ran the code listed on that page (and then rebooted):

$ sudo apt-get remove --purge xorg-driver-fglrx

You could also read:

[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)

I later ended up running the code listed under "Problem: Need to fully remove -fglrx and reinstall -ati from scratch". You may or may not find that necessary.

---

