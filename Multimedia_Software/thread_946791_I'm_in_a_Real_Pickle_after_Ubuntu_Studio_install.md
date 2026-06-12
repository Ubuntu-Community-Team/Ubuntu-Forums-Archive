---
title: "I'm in a Real Pickle after Ubuntu Studio install"
date: 2008-10-13
forum: Multimedia Software
---

### Post by Blather_X on 2008-10-13
Firstly I (was) running HH 8.04 on a 64bit system.  After installing UbuntuStudio specifically for the 64bit systems, Linux wont load!  

The error screen states: *"Failed to start the X Server"  API Mismatch  - Failed to initialize the NVIDIA Kernel module" Fatal Error - No Screens Found.*

*"Restart GDM after it is configured"*

And that's as far as it goes.

Here's the rub.  I'm still fairly new at this but what I was thinking was, If I could get into grub and then the command line I should be able to start working on this problem from there.  Well... that's the (other) problem.  In the "Detailed Error Log"   "*The core "keyboard" AND "pointing device" weren't specfied explicitly in the layout"* So I cant "esc" to enter grub and then the command line.  In fact I dont have keyboard functionality until "after" the error messages have completely loaded!  YIKES!

Im just stabbing in the dark here, but is there a way to gain root using the "Live CD"?  Or am I completely nuked?  

Well, I've been learning about Linux by "breaking" it (albeit a little at a time) and then fixing it.  Looks like I've really put a "stomping" to it this time!

Does anyone have an idea on how to get me started on this?  

Blather

---

### Post by markbuntu on 2008-10-13
It is a bad idea to get ubuntu studio if you are using drivers from nvidia or ati and do not remove them before you install the ubuntustudio packages but you know that now. The problem is that the ubuntustudio kernel cannot load the driver kernel modules so it fails. Dont' feel so bad though, it happened to me too.

This is how I fixed it.
What I did was boot into safe mode with the rt kernel from ubuntustudio and edit xorg.conf and changed the "driver" to VESA, got rid of all the driver "option" lines etc and rebooted. Then I could login in gnome safe mode and dpkg the driver kernel modules into the kernel, rebooted and it worked, lol.

This may work for you, it may not. If you did not save the kernel modules somewhere you need to get them again.

---

### Post by Blather_X on 2008-10-13
That's what I was trying to do, but I don't even have keyboard access until "after the error screen, and then it's too late to do anything but reboot.  

I cant [esc] into safe mode... no keyboard!

What a pi$$er!

Blather

[EDIT:]

That's why I was asking about accessing sudo/root from the "live cd".

---

### Post by markbuntu on 2008-10-13
Well, you can use the live cd for that I hear. I have never had to resort to it but it can be done. You don't happen to have usb keyboard and mouse do you?
A "regular" keyboard would work at boot if you could dig one up.

---

### Post by Blather_X on 2008-10-13
No USB,  It's a "wired" keyboard and mouse.  But as I said before, it is unresponsive until "after" the error message screens have loaded.  

The "countdown" in grub just keeps counting down, no matter how many times or how hard I mash the [esc] key.  

I'm about ready to burn some toenail clippings and do a "shakey" dance! But we'll have to save the "chicken" for later!

---

### Post by markbuntu on 2008-10-14
Hmmm, grub should not be doing that to you. You can use the live cd to get into your file system. There are some threads around here that will tell you how to do that. Try a search.

---

