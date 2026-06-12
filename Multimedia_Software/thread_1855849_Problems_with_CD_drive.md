---
title: "Problems with CD drive"
date: 2011-10-07
forum: Multimedia Software
---

### Post by skoobyboo on 2011-10-07
I'm using XFBURN to get Linux KidX.iso onto cd for my boys but every time I open it I get the following pop up 


**No burners are currently available**
Possibly the disc(s) are in use, and cannot get accessed.

Please unmount and restart the application.

If no disc is in the drive, check that you have read and write access to the drive with the current user.


I just finished putting a DVD in and that worked, so I know that its working.
The cd I'm putting in is blank.  The cd drive isn't mounted though and I don't know how to do that.

I have the mounted devices thingee at the bottom right of my screen, /media/floppy0 has a red not mounted thing.  Which might be the problem, though I don't know how to mount it, and even then it might not be that.

I have just carried on trying to get the iso onto cd but then when I click proceed to burn, it just closes.

Can you help?

---

### Post by VinDSL on 2011-10-07
A long standing bug seems to have cropped up again:  [https://bugs.launchpad.net/ubuntu/+source/udev/+bug/283316](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/283316)

Optical drive gets hammered with requests - sometimes breaking it.

Might want to check it out, before it's too late.

---

### Post by mörgæs on 2011-10-07
Changed the title to a more descriptive one.

---

### Post by slumbergod on 2011-11-09
Would it be impertinent to ask if it will ever get fixed?

I posted a bug report about it on the second day after 11.10 came out and it still craps out. Bring back gnomebaker - at least that worked!

---

