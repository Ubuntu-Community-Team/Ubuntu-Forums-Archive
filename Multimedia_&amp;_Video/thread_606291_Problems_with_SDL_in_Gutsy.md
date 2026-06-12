---
title: "Problems with SDL in Gutsy"
date: 2007-11-07
forum: Multimedia &amp; Video
---

### Post by Tinsley614 on 2007-11-07
I am running a pretty basic system: IBM ThinkPad T60, Centrino dual-core, and an Intel on board graphics card, with a gig of ram and a standard 1024 x 768 LCD laptop monitor. Any time I try and run anything with SDL, I always get an error message like this:

<username>@<username>-laptop:/usr/games$ ./trackballs
setLocale:  -> en_US.UTF-8
Welcome to Trackballs. 
Using /usr/share/games/trackballs as gamedata directory.
Could not initialize libSDL.
Error message: 'No available video device'
<username>@<username>-laptop:/usr/games$ 


If anyone could help that would be great. I'm also using the intel "experimental" video device driver. Thanks in advance!

---

### Post by tenach on 2007-11-27
I have the same issue only I am using restricted drivers for ATI.

> 
tlm@Dral:~$ glxinfo |grep render
direct rendering: Yes
OpenGL renderer string: ATI Radeon Xpress Series


Xpress 1100 by the way, but it uses the Xpress 200 download from AMD's site.  I have SDL 1.2.12 installed from the repositories.

---

### Post by Tinsley614 on 2007-11-27
I installed SDL from repositories as well, my driver is also restricted.

---

