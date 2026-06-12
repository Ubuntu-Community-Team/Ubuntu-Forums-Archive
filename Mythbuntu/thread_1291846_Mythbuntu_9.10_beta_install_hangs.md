---
title: "Mythbuntu 9.10 beta install hangs"
date: 2009-10-15
forum: Mythbuntu
---

### Post by laffinet on 2009-10-15
Hi !

I thought I'll try installing mythbuntu 9.10 but I just can't get the installation to work.

I get to the selection screen (Live, install etc.), if I select live environment or install I get this:
- splash screen with status bar going back and forth
- splash screen with status bar progressing (to about one 3rd)
- boot (or similar messages)
- black screen (TV is displaying no signal)

That's it, the CD drive (or USB stick) is accessed for a few seconds longer, then nothing. 

I've downloaded the iso (9.10 beta, i386 desktop version) via torrent. Checksum is correct. First tried install via usb stick, created with unetbootin.
That didn't work so I burned a CD and tried again, same problem.
Checked the CD for defects, all good.
Tried low graphics mode, again, same problem.
Tried booting into live environment. Same problem.

Any ideas ?

---

### Post by GuiGuy on 2009-10-15
> **laffinet said:**
> Hi !

I thought I'll try installing mythbuntu 9.10 but I just can't get the installation to work.

Any ideas ?

If you're running an AMD AM2 CPU and trying to install the 64bit version, try turning AHCI off. Especially if it's an ASUS mobo.

Hope this helps.

---

### Post by superm1 on 2009-10-15
I'd recommend the daily-live to see if the problem still exists.

[http://cdimages.ubuntu.com/mythbuntu/daily-live/](http://cdimages.ubuntu.com/mythbuntu/daily-live/)

If it does, please file a bug! :)

---

### Post by AKADAP on 2009-10-15
I have seen this behavior on both ATI and NVIDEA based systems. I got around it both times by selecting the video safe mode during the install, then installing the proprietary drivers after the install completed.

---

### Post by laffinet on 2009-10-15
> **GuiGuy said:**
> If you're running an AMD AM2 CPU and trying to install the 64bit version, try turning AHCI off. Especially if it's an ASUS mobo.

Hope this helps.

Yes it's an Asus mobo, but I used the 32 bit version.


> video safe mode 

Do you mean "low graphics mode" ? If so I tried that, same problem.

> I'd recommend the daily-live to see if the problem still exists.

[http://cdimages.ubuntu.com/mythbuntu/daily-live/](http://cdimages.ubuntu.com/mythbuntu/daily-live/)

If it does, please file a bug!

Will try that and file a bug report if the problem persists

---

### Post by superm1 on 2009-10-16
Safe graphics mode was broken at beta.  It's been fixed in daily images.

---

### Post by SiHa on 2009-10-18
Well.

I've just tried two daily images - 20091017, which I downloaded yesterday and 'Current' which I grabbed today.

Yesterdays, I could get as far as the pulsing mythbuntu icon, then it would hang. Tried at least six times, had to clear my CMOS after a couple just to get it to POST, twice, I got the PC speaker endlessly beeping at me mid-install, and had to reach for the Big Red Button. Also HDMI output screwy, from afer the pulsing logo.

Trying today's, I selected 'Install Mythbuntu', but instead got the LiveCD desktop. When trying to run the installer from there, it just exited straight away, and I got a crash report a few minutes later.

Went back to the beta, and it installed first time, so I don't think it's the hardware.

Think I might wait a few days for the RC

---

### Post by superm1 on 2009-10-18
Can you please file that crash report you found?  That's very odd that you are having so much trouble.  I *just* did an install with 2008-10-18 ISO myself without any troubles...

---

### Post by laffinet on 2009-10-18
> **SiHa said:**
> Well.

I've just tried two daily images - 20091017, which I downloaded yesterday and 'Current' which I grabbed today.

Yesterdays, I could get as far as the pulsing mythbuntu icon, then it would hang. Tried at least six times, had to clear my CMOS after a couple just to get it to POST, twice, I got the PC speaker endlessly beeping at me mid-install, and had to reach for the Big Red Button. Also HDMI output screwy, from afer the pulsing logo.

Trying today's, I selected 'Install Mythbuntu', but instead got the LiveCD desktop. When trying to run the installer from there, it just exited straight away, and I got a crash report a few minutes later.

Went back to the beta, and it installed first time, so I don't think it's the hardware.

Think I might wait a few days for the RC

I tried with a daily image from 16/10/09.

Started in safe graphics mode and installed. Install went fine, but I've never been able to boot that installation (installed to a USB hard drive): always asks me to "insert" a bootable drive.

So I thought I reinstall but now have the same symptoms you mention:
Install goes to liveCD environment, trying to install from there just crashes.

Since I'm on a download quota I will wait until the official version comes out :(

---

### Post by superm1 on 2009-10-18
> **laffinet said:**
> I tried with a daily image from 16/10/09.

Started in safe graphics mode and installed. Install went fine, but I've never been able to boot that installation (installed to a USB hard drive): always asks me to "insert" a bootable drive.

So I thought I reinstall but now have the same symptoms you mention:
Install goes to liveCD environment, trying to install from there just crashes.

Since I'm on a download quota I will wait until the official version comes out :(
Can you please file your crash report so we can investigate?

Also, please make sure you check the CD for errors.  The checker is in the CD boot menus.

---

