---
title: "Radeon HD 6850 issues with 12.04"
date: 2012-05-22
forum: Multimedia Software
---

### Post by azile19 on 2012-05-22
I am running 64-bit 12.04 Ubuntu on a computer I just built which has a Sapphire Radeon HD 6850 graphics card.  Currently my problem is with setting the correct resolution and the location of the image on my monitor.  

When I first installed ubuntu, the boot drive looked fine, but when I loaded it for the first time, it loaded into a completely orange screen.  So, I rebooted into recovery mode.  This asked me to mount something somewhere else, then proceeded to ask why the time of last mounting was in the future and could it fix it.  Then it finished booting into recovery mode, and everything looked just fine (and centered on the screen) with the exception of the new resolution.  

I installed the ATI/AMD proprietary FGLRX graphics driver and I can boot into regular mode, but there are two problems.  First, the whole screen is shifted way left.  I can change the monitor's settings to move it back right, but not far enough.  Secondly, my monitor box says that its native resolution is 1680x1050, but for some reason this monitor seems to always tell computers that its resolution is 1920x1080.  Weirdly enough, right now the latter looks better than the former, although my guess is that when I get the screen transposed to the right place, the screen image will still be hanging off the side.

I would appreciate any help you can give me.  I can give more specific information when I try rebooting the computer again.

---

### Post by azile19 on 2012-05-22
Just for more specifics, when I boot into recovery mode I get the following:

Continuing will remount your / filesystem in read/write mode and mount any other filesystem defined in /etc/fstab.  Do you wish to continue?

Yes

/dev/sda7: Superblock last mount time is in the future.  
     (by less than a day, probably due to the hardware clock being incorrectly set) FIXED

---

### Post by debili on 2012-05-30
hello, please  did you resolve this issue? how is the card working under 12.04? i'm about to buy one but don't know if i can get it working 100%. thankyou

---

### Post by azile19 on 2012-05-30
I spent three days trying to make it work.  I installed the binary drivers manually.  I reinstalled ubuntu multiple times.  There's only so many times I want to edit an xorg.conf file, so I sent back the card and replaced it with an nvidia GeForce GTX 550Ti.  I got everything installed and running in an hour.  I am never buying radeon again.

---

