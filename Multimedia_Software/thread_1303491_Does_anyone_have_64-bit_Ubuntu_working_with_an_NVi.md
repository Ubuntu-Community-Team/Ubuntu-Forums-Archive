---
title: "Does anyone have 64-bit Ubuntu working with an NVidia card using DVI?"
date: 2009-10-28
forum: Multimedia Software
---

### Post by DMisigoy on 2009-10-28
If you do have 64-bit Ubuntu working with an NVidia card using DVI, could you please post your xorg.conf? Or let me know whatever else you did to get it working.

I have a GeForce 7900 GTX and have tried 3 or 4 different ways of installing the nvidia driver to no avail. Every time I restart the computer after installing the new driver my display goes blank after the Ubuntu progress bar and says no signal. I've tried adding in options in xorg.conf to force it to use DVI output by specifying DFP, but nothing seems to work and this is really the one thing killing my enjoyment of Ubuntu on my desktop.

Thanks.

---

### Post by DMisigoy on 2009-10-28
Seriously? no one is running 64 bit Ubuntu with an nvidia graphics card?

---

### Post by VastOne on 2009-10-28
I am ...9800 GT and 8500 GT

Nothing will work the way you want until the drivers are installed.

I seem o recall that 173 restricted were what you needed for that card

---

### Post by VastOne on 2009-10-28
Have you tried the restricted drivers? From the googleing I have done it appears your card should work with the latest 180 drivers in restricted.

---

### Post by running_rabbit07 on 2009-10-28
If using Ubuntu, got to System>Administration>Hardware Drivers and if any drivers are needed, they should be there. Let us know what happens.

---

### Post by SuperSonic4 on 2009-10-28
My 8500GT is running Twinview through VGA and DVI with the 185.18.36-2 driver.

Admittedly I'm running Arch but it still worked when I was on Kubuntu

---

### Post by bribera on 2009-10-28
I too installed the non-free driver. I then used the NVIDIA X Server Settings utility (under Applications -> System) to set up my X Sever Display Configuration and save an X configuration file.

---

### Post by running_rabbit07 on 2009-10-28
If there is a working, supported driver in the repository, then we should recommend it to save the OP from haveing a kernel update crash in the future, just my  opinion.

---

### Post by VastOne on 2009-10-29
> **running_rabbit07 said:**
> If there is a working, supported driver in the repository, then we should recommend it to save the OP from haveing a kernel update crash in the future, just my  opinion.

I believe that is the advice we have ll been giving, IMHO.

---

### Post by c2483 on 2009-10-29
I have a 7600gt with a lcd monitor connected via dvi and I have the exact same problem

---

### Post by VastOne on 2009-10-29
> **c2483 said:**
> I have a 7600gt with a lcd monitor connected via dvi and I have the exact same problem

Which problem? Are you not getting any nVidia drivers to load? Have you ever had any nVidia drivers load? Any restricted drivers load?

---

### Post by c2483 on 2009-10-29
I just get my monitor suspending after ubuntu starts to load and haven't found any way to fix it
using open source nouveau but not happy about it

---

### Post by niite on 2009-10-29
Yeah, I'm running dual 260M's.  Nvidia just released a certified driver for the GeForce series two days ago - you can find it here.  I doubt you'll find it in the repositories yet, you'll need to get it from nvidia.

[http://www.nvidia.com/object/linux_display_amd64_190.42.html](http://www.nvidia.com/object/linux_display_amd64_190.42.html)

---

### Post by running_rabbit07 on 2009-10-29
Or you could go to System>Administration>Hardware Drivers and use a supported driver. Be aware that if you use the manufacturer driver, you may have problems whenever there is a kernel update.

---

### Post by c2483 on 2009-10-29
I can't believe I didn't realize sooner what was wrong.  I guess the nvidia driver uses CRT by default.  My tv is also connected to my video card and it is CRT.  Monitor is DVI.  My monitor was being disabled on bootup.  All along the video card was sending the picture to my TV and I never even thought about it.  I turned on my tv and saw in the nvidia control panel that my monitor was DFP-0.  I added "UseDisplayDevice" "DFP-0"] to ["Screen"] in xorg.conf and all is great.  Hope this helps.

---

### Post by niite on 2009-10-29
> **running_rabbit07 said:**
> Or you could go to System>Administration>Hardware Drivers and use a supported driver. Be aware that if you use the manufacturer driver, you may have problems whenever there is a kernel update.

yeah problem with that, is the drivers that show up actually don't support my cards..  this one from the manufacturer is the first one that does, and that i could get working for me.

---

### Post by running_rabbit07 on 2009-10-29
> **niite said:**
> yeah problem with that, is the drivers that show up actually don't support my cards..  this one from the manufacturer is the first one that does, and that i could get working for me.
no problem, use what works. I was just recommending to try those before going to proprietary sites for drivers.

---

