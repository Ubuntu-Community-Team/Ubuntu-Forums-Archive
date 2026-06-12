---
title: "Video problem revisited..."
date: 2014-07-14
forum: Multimedia Software
---

### Post by Mike_Walsh on 2014-07-14
Afternoon, everybody.

I have two PCs. My main one is a ten-year old Compaq Presario desktop, and my secondary is an even older Dell laptop.

I have Ubuntu 14.04 and Zorin OS 8 running in dual-boot config on the Compaq....no problems there at all.

I've tried various distros on the Dell; Lubuntu, Zorin Core 8, and now Ubuntu. Without exception, they all work. However, during the live session, I have full-screen resolution (1024x768); upon installation, this shrinks down to a 640x480 display, stuck in the top left corner of the screen, with lots of hash and squiggly stuff occupying the rest of the screen. I've tried the 'nomodeset' option on the boot file, and various other tweaks, and nothing seems to work.

I've pretty much given up on this ever getting sorted out. However, last night, I was looking at the system info window on the Dell, and then decided to cross-check this with the info on the Compaq.

According to the Compaq's info, the Gallium 0.4 driver is located on the ATI RS480 northbridge; I know that's correct for the model. It has the Radeon Xpress 200 series graphics chip integrated on the northbridge, and since the Gallium driver works just fine, I haven't bothered downloading the AMD driver for it.

According to the Dell's info, the Gallium driver is located on 'llvmpipe' (?) What on earth IS 'llvmpipe'??

I know for a fact that the Dell has the Intel 82845 GL/GE/PE/PV graphics chipset....so why is it not showing as recognised?

Could it be that the 82845 is SO old that the kernel driver support doesn't cover it? I recall that this chipset was fitted to quite a number of laptops at the time the Dell was built, so was quite well-known; and by all accounts, it was dead reliable. I ran Win XP on this very machine for several years until recently, and of ALL the various little tantrums it's thrown over the years, not ONE of them has been graphics-related.

Would I be better off getting hold of the Intel driver for the 82845 chipset? And if so, how do you go about installing it in Linux? I'm fairly tech-savvy (or was, under XP!); I'm still learning with Linux. Messing about with drivers was never one of my favourite pastimes, and having just got the system set-up exactly the way I want it, I don't really want to mess it up again..!

Any advice would be much appreciated.

Regards,

Mike.

---

### Post by stalkingwolf on 2014-07-14
you can try going to additional drivers ( should be under preferences) and see if there is an updated driver available.  if so it is as simple as activate and reboot.

---

### Post by Vladlenin5000 on 2014-07-14
For the Intel 82845 there's an old recommendation: ```
sudo apt-get install mesa-utils
``` and reboot. I don't know if it is still valid for newer releases.

---

### Post by Mike_Walsh on 2014-07-14
Hi,guys; thanks for replying.

I've actually posed this same question on at least two other occasions in this forum over the last couple of months, and this is the first time anybody's actually offered any constructive advice; thank you very much indeed!

Stalking_Wolf; I've checked the preferences tab you're talking about, and there's nothing showing. I have looked at this tab on a few occasions prior to this, and never HAVE seen anything. It could mean that the 82845 driver is already in the kernel support, but for some reason, it's not behaving itself...

Vladlenin5000; greetings. I've noted your replies in a number of threads, and I will say that on most occasions, your advice often makes a lot of sense. 

I know from exploring the forum that other people have had this same problem, with this same chipset. One guy's solution I felt sure would work for me, since he also had the same laptop, same model, same CPU, same everything, in fact.....but his solution failed to work. :(

I'll have a look at your suggestion; I have heard of this Mesa thingy (whatever it is...I DO know it's SOMETHING to do with graphics), and will let you know how I get on.

Cheers!

Regards,

Mike.

---

### Post by Mike_Walsh on 2014-07-14
Well, now;

Vladlenin; I've tried your suggestion. It quite happily installed, but it doesn't appear to have done anything, unfortunately. I rebooted, and after the screen came back up still the same size, I went into Monitor Settings, to see if I could change that.

Previously, there was only the 640x480 setting. There is now an 'auto' option available, but this doesn't appear to make any difference.

I've downloaded and extracted the Intel Extreme Graphics driver for the 82845 (for Linux), but I can't install it! The problem is that although the desktop and taskbar are all there in miniature, the desktop icons are full size, and so are all the windows; and if I need to access any buttons at the bottom right corner of the screen (to get any process to continue), I can't.....because the only part of any given window that is visible is the top left section, and you can't make the window move to reveal what you need!

Is there a way in which this can be done via the terminal? I know which folder the package is located in, but I'm not very good with the terminal yet..!

Regards,

Mike.

---

