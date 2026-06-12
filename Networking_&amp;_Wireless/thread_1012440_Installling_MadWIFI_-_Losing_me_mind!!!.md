---
title: "Installling MadWIFI - Losing me mind!!!"
date: 2008-12-15
forum: Networking &amp; Wireless
---

### Post by stoopid_noob on 2008-12-15
I am new to Linux completely, so bare with me. HOW THE HECK DO I INSTALL THE PACKAGES FOR MADWIFI????!?!?!?! 

I am lost. I have it unpacked to my desktop, in the terminal how do I bring up that directory though? I know the steps to follow afterwords but how to I even get to that directory in the terminal? 

Thanks for help.

---

### Post by stoopid_noob on 2008-12-15
I am in the directory. I type in "Make Install" and hit Enter it brings up information concerning previous modules do I want to remove etc. I select yes it gives me an error. I select to ignore it and it says Error 1 (That it cant create a directory because permission is denied)

Is there like literally a STEP BY STEP guide to installing this thing? Instead of "Oh you should be do this and then this" ,,, "No wait you have to do this first."

---

### Post by kevdog on 2008-12-16
Isn't madwifi just part of the linux-restricted-package?

And its sudo make install, not just make install.

---

### Post by wdaniels on 2008-12-16
Do you know exactly which chipset your card has? I don't think you need to install the madwifi drivers manually for most of them now...

---

### Post by stoopid_noob on 2008-12-16
It wouldn't work out of the box. It didnt see any networks at all. I tried following all of the online WLAN stuff and with no end to the frustration I just went on to my machine in Windows and deleted the partition! Not even my wired connection would work at all. 

:confused:

I figured that it would simply see the partition and remove the partition but NOW when I turn on the computer GRUB takes over but there is no way to get around it to boot into ANYTHING now!

Any ideas as to what I can do from here? Take note that I do not have a CD drive to run Windows from. 

The error I get from GRUB is "Error 22"

---

### Post by stoopid_noob on 2008-12-16
So, I think I have found a solution. I thought I would post it for anyone else having the same issue. I will post again if it works but I see no good reason why it wouldn't.

Essentially why this happened was because GRUB is the MBR as opposed to Windows. GRUB tries to load Ubuntu from the partition, but the partition and files no longer exist so it kicks back the Error 22 message. 

To get around GRUB I think the easiest method would be to use something called Super Grub ([http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)) 

I have created a Bootable CD under a Windows partition I have on my iMac24" using Infra Recorder. I am going to go and pick up a cheap external disk drive (CD/DVD) today and run it from the AA0 via USB. 

If it works I will let everyone know.

Thanks for your help.

---

