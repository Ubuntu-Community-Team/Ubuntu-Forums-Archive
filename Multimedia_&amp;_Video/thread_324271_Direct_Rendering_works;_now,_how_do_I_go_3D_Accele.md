---
title: "Direct Rendering works; now, how do I go 3D Acceleration?"
date: 2006-12-23
forum: Multimedia &amp; Video
---

### Post by Sunnz on 2006-12-23
I have nVidia-drivers installed and Direct Rendering is turned on according to glxinfo.

However in the Cedega tests it is said that 3D Acceleration is not being enabled!!!

I thought that nVidia driver gives 3D Acceleration?

What's going on here?

---

### Post by ashmew2 on 2007-01-17
Im having exactly the same problem , didnt had to install anything on Ubuntu Christmas Edition though but 3d acceleration still doesnt work..

---

### Post by whatever on 2007-01-17
cedega's "test" is crap.

---

### Post by ashmew2 on 2007-01-24
lol okay , but i installed game using Cedega and it still says an error "NO 3d hardware foud on your system. THe game requires 3d acceleration t run"

---

### Post by Sunnz on 2007-01-24
Looks like "sudo nvidia-glx-config enable" doesn't work quite well...

You got X working again, right?

If so, post(or pm) /ect/X11/xorg.conf here, and I'll take a look at it...

---

### Post by wererabbit on 2007-01-24
I ran into this issue after I had installed Beryl on my Dapper system.  I don't remember exactly how it worked, but essentially every time I tried installing the glx driver it would conflict with the Nvidia driver and turn off 3D acceleration.  Basically, unless I installed Edgy and then configured the nvidia driver properly, Cedega will report that the OpenGL 3D acceleration wasn't installed.   It was weird. And I probably haven't explained this very well.  But that's okay, I was up until 12:30am playing WoW. :)  Oh yeah, I was able to fix this with the Automatix install after a clean install of Edgy.

---

