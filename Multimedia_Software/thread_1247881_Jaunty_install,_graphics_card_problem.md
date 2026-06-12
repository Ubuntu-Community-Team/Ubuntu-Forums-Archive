---
title: "Jaunty install, graphics card problem"
date: 2009-08-23
forum: Multimedia Software
---

### Post by CTBuckweed on 2009-08-23
I've been using Ubuntu Hardy (8.04) 64 bit for over a year. A few weeks ago, I upgraded my system to Ubuntu Jaunty (9.04) 64 bit - a cold re-install after backing up my files.

I have an AMD FX-62 with 2 GB of ram and a Sapphire Radeon X1900GT for my graphics adapter. It all worked fine with Hardy but when I booted off of the Jaunty install CD, the thing would start to load. It asked for the keyboard settings and I saw the progress bar toggling back and forth. Then the display became garbled and I was not usable to complete the install. I booted again and used the generic adapter option for the install. With that, it loaded and I installed it fine.

The thing is now, I can only go up to resolution 1600x1200 not the 1650x1050 as with Hardy which was able to do it right out of the box. Nor did even have the option of installing the flgrx 3D drivers like I did with Hardy.

I wish to setup Jaunty to recognize my VGA card capabilities and support 1680x1050 to match my wide-screen 22" monitor & maybe the 3D support too.

I'm stuck - I can't get the aspect ratio I need. The system works okay except that the video does seem slower than on Hardy. With the 4x3 aspect ratio, images look to tall & out of proportion. For now, I went back to Hardy.

Is there a way to coerce Jaunty in recognizing my VGA card correctly? HELP!

---

### Post by markbuntu on 2009-08-23
It is important to remove the fglrx driver before upgrading or you end up with the generic VESA driver instead of the ati or radeon driver. This could have been the cause of your problem. 

The fglrx driver is not available for your card with the fglrx available in Jaunty or any future driver for that matter The old fglrx drivers are not compatible with the new xserver used in Jaunty.

---

### Post by CTBuckweed on 2009-08-23
I did a totally cold install from the ground up. Nothing at all from the Hardy installation. To complete the install of Jaunty, I had to set the install option for generic VESA. After installing, in the hardware settings, I didn't have any option to change the graphics driver drivers.


> **markbuntu said:**
> It is important to remove the fglrx driver before upgrading or you end up with the generic VESA driver instead of the ati or radeon driver. This could have been the cause of your problem. 

The fglrx driver is not available for your card with the fglrx available in Jaunty or any future driver for that matter The old fglrx drivers are not compatible with the new xserver used in Jaunty.

---

### Post by markbuntu on 2009-08-24
You should read this about getting the open source ati or radeon driver working

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by midijery on 2009-08-24
I've been trying to fix this problem for a couple of days on an HP zv6000 laptop with a 200m video chip and came across a way to get the full resolution (no 3D). As root open xorg.conf and then add the entry:
Driver      "radeon"  
under the section "device" and remove the entry for "vesa" if it exist. 

I just used "sudo dolphin" and navigated to the /etc/X11 folder which  opened it with "kate" to edit the file (Which automatically makes a backup "xorg.conf~" in case it doesn't work.) Then I exit dolphin and do a ctrl+c in the terminal to exit the process.
Just be careful if your a new-by to Linux because you can do a lot of damage running dolphin as root. :)

---

### Post by CTBuckweed on 2010-02-01
All fixed now!! My video card hardware had a subtle problem with it. It finally started exhibiting problems to Windows XP (yuk). I purchased a Nvidia 9800 series (PNY VCG9800GTEE1XPB ~$100) and everything worked OK. I then upgraded to 9.10. I'm a happy camper:p

---

