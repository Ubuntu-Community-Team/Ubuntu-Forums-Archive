---
title: "Can I alternate between ATI and Nvidia drivers on a single ubuntu install"
date: 2009-05-25
forum: Multimedia Software
---

### Post by eyefragment on 2009-05-25
Hi all,

I am in the somewhat strange position of using an ATI graphics card while I have my laptop docked, but using an nVidia card while my laptop is on-the-go.  So far, I have been handling this by keeping two installs of ubuntu (one configured for ATI, one configured for nVidia), but this has some disadvantages (even if the home folders are the same, I need to install applications once for each OS, some preferences are not carried over, etc).  Is there any way to keep both graphics drivers installed, and toggle which one is currently active (presumably with a reboot required somewhere)?  I'm preparing to do a reinstall soon, so I can accept just about any solution.

Thanks!

---

### Post by nikhilbhardwaj on 2009-05-25
you are joking aren't you

---

### Post by eyefragment on 2009-05-25
No, I am not.  I have an external graphics card for my laptop (see [http://www.villagetronic.com/vidock/techspecs.html](http://www.villagetronic.com/vidock/techspecs.html)), since the internal card does not have a dual-link DVI port.

---

### Post by Philip550c on 2009-12-06
Did you ever find an answer to your question? Also how does the external graphics perform with linux? Does it show up as if it were your internal graphics?

---

### Post by sdowney717 on 2009-12-06
xorg.conf would control the video properties.

so you would need to replace xorg.conf for whatever card you would want to run before you reboot.
you could probably do this with an executable script file and renaming the files. the binary drivers for each card could be instaled and would not run unless referenced by xorg.conf

a more interesting approach could be to auto detect the card type and then load the appropriate xorg automatically.

---

### Post by Yellow Pasque on 2009-12-06
Both the proprietary drivers use custom versions of libGL and libglx. You would have to find a way to keep the driver installers from overwriting these files (possibly others) and then point xorg.conf to the appropriate version fro each driver.

---

### Post by efflandt on 2009-12-06
If your video devices were able to work with standard video modules, it would probably not be an issue.  I can boot regular 64-bit 9.10 installed to a USB hard drive (WD Passport) to either my laptop with built-in Intel video or my desktop with ATI Radeon AGP without issue (as long as I omit "splash" from boot parameters).  But my ATI card is supported by standard radeon kernel and X modules.

But if you really need different proprietary drivers for cutting edge hardware, you may need to do something more complicated.  Maybe you could do that by using separate users for each device with some configuration in the ~/.profile for each (if that runs automatically before X starts).  Or look into the dropdown lists in gui login (where it has "GNOME" and "Failsafe GNOME") and see if you could set up different configurations in that list (or whichever flavor of Ubuntu you are using).

---

### Post by C.S.Cameron on 2009-12-06
Switchconf, (from the repositories), used to work, (back about 8.04), for switching between xorg.conf files at startup. 
I could choose to start with or without Nvidia or ATI drivers, duel or single monitors etc.
This was helpful for plugging a bootable pendrive into different machines. 
Try as hard as I could I was not able to figure out how to keep both Nvidia and ATI drivers on the pendrive at the same time. I even tried asking in these forms without luck.

---

