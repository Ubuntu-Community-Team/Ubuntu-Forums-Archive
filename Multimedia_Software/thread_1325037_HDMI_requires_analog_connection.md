---
title: "HDMI requires analog connection?"
date: 2009-11-13
forum: Multimedia Software
---

### Post by Villainous on 2009-11-13
I have an Ubuntu 9.10 64-bit install on an HTPC setup.  I used my analog monitor to get the system setup and running, and all was great.  I unhooked the analog monitor, put it back on the PC where it was intended to be, and now when I reboot, I have to plug in the analog cable to a monitor to get my system to boot.

Is there a reason that it needs the analog to be connected to boot?  The system doesn't use the analog monitor at all, I have disabled it both via the ATI software and via the Display Manager in Ubuntu's preferences menu.

My System:
Dell GX620
Pentium D 2.8ghz HT proc
2 GB RAM
ATI Radeon 4350 HD

I haven't tried changing any conf files yet, not sure where to start on that, anyways... so any help would be appreciated.

---

### Post by TimTang on 2009-11-17
Sorry I can't help you but I have a similar problem. I haven't been able to use Ubuntu for about 8 months now because I'm using a HDMI monitor. The monitor just goes blank as soon as ubuntu kick in. It's sad because I like ubuntu but our love affair was short lived when I can't see anything.

I was hoping this had been solved by now but I downloaded 9.10 and even just running from the CD doesn't work. With 8.04 I at LEAST get a 640x480 screen to look at (not that it's any good for anything but PONG!).

I just hope they sort this out. I spent weeks trying to sort this out but it's pretty difficult when you can't SEE anything. I would think that video functionality would be one of the highest priorities but I guess not.

I hate windows, but any version from 2000 on works immediately (no pissing around) so why can't ubuntu?

---

### Post by markbuntu on 2009-11-17
Well, hdmi is not supported by the generic failsafe VESA driver, which is what ubuntu boots with. You guys should file a bug report explaining your situation. The xorg devs might not have counted on this situation since the vast majority of hdmi is used as an adjunct, not a primary monitor.

---

### Post by xzero1 on 2009-11-17
> I haven't tried changing any conf files yet, not sure where to start on that, anyways... so any help would be appreciated.

The first thing I would do is check out your xorg logs. Maybe that will give you a clue where to start.

---

### Post by sdowney717 on 2009-11-17
this is likely to become more of a problem in the future. people will want to use their TV as a pc-media center and hook it up using HDMI.
If i had an HDMI TV downstairs, that is how I would want to use it.

[http://news.bbc.co.uk/2/hi/technology/8272003.stm](http://news.bbc.co.uk/2/hi/technology/8272003.stm)

intel, etc says 90% of all future IP traffic will be TV video based!

---

### Post by xzero1 on 2009-11-17
> **sdowney717 said:**
> this is likely to become more of a problem in the future. people will want to use their TV as a pc-media center and hook it up using HDMI.
If i had an HDMI TV downstairs, that is how I would want to use it.

[http://news.bbc.co.uk/2/hi/technology/8272003.stm](http://news.bbc.co.uk/2/hi/technology/8272003.stm)

intel, etc says 90% of all future IP traffic will be TV video based!

I would say the future will be some kind of wireless connection or possibly modulation of the electrical wiring. WHO WANTS WIRES!

---

