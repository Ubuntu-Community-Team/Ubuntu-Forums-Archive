---
title: "Dual ATI FireGL and FirePRO cards"
date: 2011-02-20
forum: Multimedia Software
---

### Post by thepinkster on 2011-02-20
Howdy-

In my machine I have two cards as follows:
PCI-E slot: ATI FIREGL V3400 (dualhead)
PCI slot: ATI FIREPRO 2260 (dualhead, with DisplayPort) ****this is the main card Ubuntu is using.**

I'm running Ubuntu 10.10 and have installed the ATI proprietary drivers (Catalyst is running).

What I want to do is also have the other two outputs from the V3400 display. Right now, it's either use two from the 2260 -OR- in BIOS if I set the V3400 to be default, then Ubuntu will recognize that card but never both at once (to give a total of 4 displays).

Is it even possible (in the Linux/Ubuntu driver world)? On WinXP I'm using the ATI "Unified" drivers which provides support for both GL/PRO cards and I get the 4 to work.

Thanks.

---

### Post by aphatak on 2011-05-23
Well, I have to confess - shamefadedly - that I am facing a similar problem.  I have two Radeon HD5450 PCI-e cards, with two monitors connected to each, on a multi-boot system running (a) Ubuntu 10.04.2 LTS, (b) Windows 7, and (c) another Ubuntu 10.04.2 LTS.  All four monitors work together as a single desktop on (a) and (b), but for my life I can't get it to work with (c).  Both (a) and (c) have the same proprietary ATI fglrx drivers.  Copying the xorg.conf file from (a) to (c) does not work.

lspci and lshw show both the video cards, and that the fglrx drivers are connected to them.

I feel rather stupid, because I got it working once, and then forgot how I did it.  Any clues?  Suggestions?  References to documentation?

---

### Post by aphatak on 2011-06-01
Tried it again.  What I did was -
[LIST=1]
[*]Installed Ubuntu 10.04 LTS in a separate partition, and with its own swap space.  On booting into the fresh environment, I got one screen active (which was what I expected anyway).
[*]Ran the update manager.
[*]Attempted to get into a virtual terminal with ctl-alt-F1.  I got a completely blank screen; I entered my user-ID and password anyway.  I entered 'ls -l > dir.list' on faith.  When I got back into the gnome desktop with a ctl-alt-F7, I saw the file 'dir.list' with the output of the 'ls' command.
[*]Activated the proprietary fglrx drivers, and re-booted.  Tried the virtual console again, and got a blank screen again. I tried the old trick - 'ls -l >> dir.list'.  Again, I saw the expected output when I got back to the Gnome desktop.
[*]Ran aticonfig to update xorg.conf - 'sudo aticonfig --adapter=0,1 --initial=dual-head.  Did not play any tricks here, let aticonfig set its own default configuration (which would be four separate x-screens on four monitors - no twinview, no xinerama.
[/LIST]
I was hoping to run the ATI/AMD Control Center after rebooting.  However, when I reboot, I can see all four monitors get a signal (their lights change from amber(=not connected) to blue(=connected).  All four monitors are completely blank.  I cannot see the PC having an IP address in my router, nor can I ssh into it.  The conclusion is, the OS is in a coma - not responding to anything.

I am still fighting.  I think the blank screens are telling me something, but I cannot figure out what.

Has anyone else noticed a similar problem?

---

### Post by aphatak on 2011-06-03
Another attempt.  If I enable one of the two cards, I can get the system to boot up and behave normally; it doesn't matter which card is enabled.  When I enable both, the system goes in a coma, and all I get is four blank screens.

---

### Post by miguelquiros on 2011-12-02
Hello. I have found this:

[http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver](http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver)

The workaround posted in the previous address worked for me.

Good luck!

---

