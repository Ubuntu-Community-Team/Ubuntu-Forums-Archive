---
title: "visual effects cannot be enabled"
date: 2009-02-18
forum: Multimedia Software
---

### Post by hgais on 2009-02-18
So I was playing with some of the compiz-fusion settings a while back, and install something that ended up turning my screen randomly black.  When I logged out, it wouldn't go away, even in safe-mode.  I ended up having to do an uninstall and reinstall of various things, but, for whatever reason, I cannot enable visual effects via System --> Preferences --> Appearance --> Visual Effects, as the latter section is completely greyed out.  Any recommendations?  I tried install xserver-xgl, but it just gives me the following: 

hgais@axios:~$ sudo apt-get install compiz xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
compiz is already the newest version.
Package xserver-xgl is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

Or that there are broken packages, but I cannot change them in Synaptic (when I look for broken packages, I come up with nothing).  Something in my system seems to be very confused, but I can't figure out what!

---

