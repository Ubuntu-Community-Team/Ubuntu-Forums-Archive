---
title: "Display Settings resetting on every boot with dual-monitors"
date: 2013-11-04
forum: Multimedia Software
---

### Post by jackhe220 on 2013-11-04
Hello people!
I upgraded to 13.10 today from 13.04 and it went pretty much perfectly, though I noticed my display settings had reset to 1920x1080 interlaced on the first monitor, and 1024x768 on the second which is completely wrong. I fixed them using the 319 NVIDIA driver, but as soon as I rebooted it went back... and has done on every boot. I tried saving my settings to an xorg, which makes the settings stick on the login but as soon as I do login they screw up again. They are supposed to be 1920x1080 progressive and 1280x1024.

Also as a side issue, as a result of the resetting the vblank monitor keeps setting to my second monitor causing screen tearing on video. If I try to put it back to the correct SHARP LCD, I have to reboot = settings screw up. I'm in an endless circle with this one.

If it's any help, I'm running x64 with a GeForce GT 340. The first monitor is connected via HDMI and second DVI. 

Thank you!

---

### Post by d4m1r on 2014-02-13
Having the same problem with Ubuntu 12.04 and dual monitors (laptop internal + external). Forgot my previously configuration and so every time I need to reset things how I like them on boot...

Did you ever find a solution for this?

---

### Post by frank18 on 2014-02-13
> **jackhe220 said:**
> Hello people!
I upgraded to 13.10 today from 13.04 and it went pretty much perfectly, though I noticed my display settings had reset to 1920x1080 interlaced on the first monitor, and 1024x768 on the second which is completely wrong. I fixed them using the 319 NVIDIA driver, but as soon as I rebooted it went back... and has done on every boot. I tried saving my settings to an xorg, which makes the settings stick on the login but as soon as I do login they screw up again. They are supposed to be 1920x1080 progressive and 1280x1024.

Also as a side issue, as a result of the resetting the vblank monitor keeps setting to my second monitor causing screen tearing on video. If I try to put it back to the correct SHARP LCD, I have to reboot = settings screw up. I'm in an endless circle with this one.

If it's any help, I'm running x64 with a GeForce GT 340. The first monitor is connected via HDMI and second DVI. 

Thank you!

I don't think you can have 1 monitor on 1024x768 and another in 1920x1080 at same time cause it only works as mirror!
if you set one monitor to 1920x1080 the other will be the same , this is if both monitor support 1920x1080,

---

