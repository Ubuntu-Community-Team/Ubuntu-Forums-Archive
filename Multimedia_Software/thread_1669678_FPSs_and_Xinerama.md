---
title: "FPSs and Xinerama"
date: 2011-01-18
forum: Multimedia Software
---

### Post by kerryhall on 2011-01-18
I am running a multi monitor setup with xinerama, and everything works great except when I try to play an FPS such as OpenArena. The mouse doesn't work, it gets stuck to the screen edge. Anyone have this problem?

Thanks!

---

### Post by kerryhall on 2011-01-29
Bump

---

### Post by BicyclerBoy on 2011-01-29
I suggest stop using xinerama

Try (nvidia only) twinview not mirrored or separate X screens.
Both of these allow full video acceleration etc.

Separate X screens is not to everyone's liking..

---

### Post by kerryhall on 2011-03-11
Doesn't xinerama support full 3d acceleration too? 

Anyway, the issue is the mouse it seems.

---

### Post by kerryhall on 2011-04-13
Anyone have any info on this? Thanks! Still having issues here...

---

### Post by BicyclerBoy on 2011-04-13
Xinerama stills to be a bit old & neglected compared to twinview. 

Long shot.. but

[http://us.download.nvidia.com/XFree86/Linux-x86/173.14.09/README/chapter-13.html](http://us.download.nvidia.com/XFree86/Linux-x86/173.14.09/README/chapter-13.html)
search for "Unfortunately, the data provided by XineramaQueryScreens()"

& **"Can I play full screen games across both display devices?"**

This does look to be more relevant to twinview & dynamic twinview.
It does show a method to get one screen across multiple displays with meta mode strings.

---

### Post by kerryhall on 2011-04-18
Perhaps I will try and use twinview over xinerama.

I want just one giant desktop though, not three separate desktops. I want to be able to drag windows from desktop to desktop. Is there a way to configure twinview like that?

Thanks for the help!

---

