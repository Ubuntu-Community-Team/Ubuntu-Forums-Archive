---
title: "Mythbuntu not ready for prime time!"
date: 2009-09-03
forum: Mythbuntu
---

### Post by bluepuma on 2009-09-03
I recently bought an Acer Revo R3600 Nettop PC and evaluated a bunch of Media Center and VDR solutions.

Yesterday I tried to install Mythbuntu 9.04  from the downloaded ISO.

**1. Live Mode**

First I tried the live mode - and it failed miserably. It came up with the desktop, I tried to launch the frontend, after some clicks it told me that it couldn't connect.

The live mode needs to be intuitive and run out of the box if you want to reach a wide audience
    
**2. Installation**

Then I rebooted and tried installation to a USB-Stick. The procedure was messy, I couldn't switch from NTSC to PAL and  it didn't find my Terratec DVB-T USB-Stick.

The installation needs to be easier and standard USB hardware should be recognized (GeeXboX just supplies a bunch of firmwares with the installation)

**3. Messing with the existing system**

I installed Mythbuntu to a USB-Stick and the f*cking installation procedure altered my Windows MBR on the hard drive! WTF? And the system (GRUB) can't even start with the USB-Stick removed! WTF???

Sorry guys, but when installing to a USB-Stick **I AM EXPECTING THAT YOU DON'T MESS WITH MY HARD DRIVE!**


Good luck with your efforts, maybe MythTV gets eventually integrated in XBMX for a complete TV solution with working installation.
    
I will search for a solution to restore my Windows MBR in the mean time...
    
Cheers
bluepuma

---

### Post by Grenage on 2009-09-03
[http://www.mythbuntu.org/](http://www.mythbuntu.org/)

Maybe you should bring this up on the appropriate site...

---

### Post by bluepuma on 2009-09-03
[http://www.mythbuntu.org/support]("http://www.mythbuntu.org/") links to this forum as '[Official Mythbuntu Forum]("http://ubuntuforums.org/forumdisplay.php?f=301")'

---

### Post by Grenage on 2009-09-03
Sorry, not sure what I was thinking earlier; I probably hadn't had my coffee. ;)

I find it interesting that it touched the disk's boot record; it also sounds like it's either removed it and put a fresh one on your USB drive, or the disks aren't in the BIOS boot order at all.

I don't suppose you could go through what you did in more detail?

---

### Post by SiHa on 2009-09-03
You were installing another operating system onto the PC, so the system needs a bootloader to give you a choice of which to boot. By default, GRUB will end up on the primary partition of your primary drive (I think), cos that's where the BIOS will generally look. If you're still stuck with restoring your MBR, maybe you should post to the 'General Help' forum.

If you still want to try Mythbuntu, I believe at install you have an 'Advanced' button when you come to select partitions etc. In there you can tell it where to put the bootloader. I would think your best bet would be to put it on the stick, then change the boot order in your BIOS to boot from the stick first.

Also, I believe the Mythbuntu LiveCD will only work as a diskless frontend client to an existing MythTV setup, where it has a backend to connect to. Maybe it's not clear, I can't remember.

Finally, and not wanting to teach you to suck eggs, but when installing a new OS onto a system that already has one (that I don't want to lose), I find it safer to get the first one out of the way by the old-fashioned method of pulling the drive.

---

### Post by issih on 2009-09-03
1) Your understanding of what the live session is for is incorrect.

Myth is a client server system, designed to be able to operate in a networked environment.

The live session is meant to be used in the situation where you already have a backend set up somewhere on the network (the backend connects to the tv decoding hardware and handles recording, etc)

Throwing the live cd into any computer on the same network and starting the front end will allow it to connect to that back end and view television, recorded programs, etc..

If you want to have the whole thing (back and front ends) on one machine, that is fine, but you have to install it, not run it as a live session.

2) Hmmn, don't know what you did here, there are options to change from ntsc to pal. As for the detection of hardware, it is either just there or its not, some hardware works some doesn't...different distros get different ones right, thats just the way it is.

The myth menus are admittedly rather opaque and arcane until you get used to them...but I assure you the option you are looking for is virtually always buried somewhere in there. You were running the backend setup first right? not just running the front end?

3) My guess is that you treated the usb disk as a hard drive, and told the installer to install to it as if it was an internally connected hard drive... Ubuntu has (as long as I've known it) had this quirk, where, by default, it installs grub into the master boot record of the main hard drive on the machine, regardless of where you install the actual distribution.

You have to go into the advanced tab on the last page of the installer to change the location it places grub.

This behaviour IS a bit dodgy, I assume it is done so that people with no understanding of drives and partitions will manage to boot into ubuntu without fiddling in the bios to change the boot order, but generally I disagree with it, and the number of people having the exact issues you do over the years is astounding.

The trouble is, that if you install to a usb drive, with grub stuck on the main hard drive, then grub expects that drive to be permanent, and errors out (error 21 if I remember correctly) if it is missing.

If instead of using the installer as if the usb stick was a hard drive, you had gone into the live session and used the usb disk creator tool provided in there I hope that this would not have happened, and the usb disk would instead have grub placed on it directly, and you would have to choose to boot from the usb disk via the bios.

If in fact you made this stick using that tool I can only bang my head on the desk in frustration for you.

So in summary:

No 1 - not an issue
No 2 - shrugs, hardware happens
No 3 - Problem....not sure it will ever be fixed, as I'm not 100% sure why they do it, it seems foolish to me.

Either way though, mythbuntu takes some effort, less than it used to, but some, and certainly reading the manuals/ some guides is highly advised, as it is a complicated beastie.

Once setup though, its pretty clever

---

### Post by bluepuma on 2009-09-04
Well, I thought that I plug-in the Live-CD, change the boot order and my PVR is ready :D

And when installing to USB-stick I though it wouldn't touch the internal hard drive. I tested GeeXboX and XBMC-Live and they had exactly that behaviour: I could change boot order and boot from USB-stick, but no GRUB install to the hard drive happened.

I guess I will just give Windows 7 and the integrated media center a try...

---

### Post by larsolav on 2009-09-04
> **bluepuma said:**
> Well, I thought that I plug-in the Live-CD, change the boot order and my PVR is ready :D

But where would stuff be recorded?


> **bluepuma said:**
> 
I guess I will just give Windows 7 and the integrated media center a try...
Every platform has its place in life. The media center in Win 7 is pretty sleek, and when it officially comes out it will work with Netflix just like in Vista. Media center probably doesn't do some of the things that Myth does. For example, I doubt it has the automatic commercial skip in it, and I can't get Win 7 to play my ISOs...

---

