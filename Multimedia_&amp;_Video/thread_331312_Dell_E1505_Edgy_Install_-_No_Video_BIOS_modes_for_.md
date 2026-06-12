---
title: "Dell E1505 Edgy Install - No Video BIOS modes for chosen depth"
date: 2007-01-04
forum: Multimedia &amp; Video
---

### Post by jkalucki on 2007-01-04
I'm trying to install 6.10 Edgy Eft on a Dell E1505 laptop. 

X cannot start:
I810: No matching Device section for instance (BusID PCI:0:2:1) found
I810(0): No Video BIOS modes for chosen depth.
Screen(s) found, but not have a usable configuration.

And that's the end of the install.

I've tried safe mode, changing resolution and screen depth -- all to no avail.

I think this laptop has I810 and 945GM video.

Dapper Drake default install has the same issue, but the safe-mode for Dapper Drake seems to work fine.

?

---

### Post by jogro on 2007-01-19
I ran into the same problem with an HP Compaq nc6400, 945GM, 1440x900 native. 

The LiveCD was busy for some time and then the boot process stopped with "No Video BIOS modes....".  The CD checked ok and the safe graphics mode didn't help.

I suspect it has something to do with the fact that the i810 driver does not accept resolution settings which have no counterpart in the BIOS, but 1024x786 or 640x480 didn't work either.
I also played with the "Depth" setting in the driver section of /etc/X11/xorg.conf without success. 

Work-around: sudo vi /etc/X11/xorg.conf, search for "i810" and replace by "vesa" 
and also change the Depth setting to 24 and the corresponding Mode section to 1024x768. 
Then "startx" succesfully started X11 and the installation worked. It also booted 
afterwards taking over my improvised xorg.conf

I suppose the next step is to follow the 915resolution stuff, which I couldn't find on the LiveCD. I will report again when it flys.

N.B. This seems to be the same bug as in [https://launchpad.net/ubuntu/+source/xorg/+bug/62002](https://launchpad.net/ubuntu/+source/xorg/+bug/62002)

---

### Post by jkalucki on 2007-01-24
Perhaps these links might help:

[https://help.ubuntu.com/community/i915Driver](https://help.ubuntu.com/community/i915Driver)

[http://www.geocities.com/stomljen/](http://www.geocities.com/stomljen/)

---

