---
title: "ATI 3870HD fglrx white screen"
date: 2008-09-08
forum: Multimedia Software
---

### Post by armsteadj1 on 2008-09-08
I just recently built a new computer:

ASUS P5Q Pro Mobo
ATI 3870HD
Intel Core 2 Duo E7200
4GB Ram

The problem I am having is that I installed the ATI fglrx drivers from the Administration -> Hardware Drivers menu and am now getting a white screen when going into ubuntu. BUT if I load into fail-safe gnome everythign seems to be working perfectly. My fglrxinfo in failsafe is shows my video card and the ATI drivers are loaded. glrxinfo shows that Direct Rendering is on. So it seems as though my fail-safe gnome is running exactly as expected.. but why would it not load correctly when I am not in failsafe?

I have read a bunch about the MTRR messing this up but it seems like that error would happen in the failsafe as well since its a memory allocator... I am not exaclty sure what I should set my /proc/mtrr to if that is actually the problem I have 512MB of ram on my video card and 4GB (shows up as 3.3GB) of RAM.. 

Does anyone have any idea on how to get the normal load to run like failsafe? Thanks!!

James

---

