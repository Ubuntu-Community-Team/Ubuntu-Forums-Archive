---
title: "Choppy videos in VLC after 9.10 upgrade"
date: 2010-07-14
forum: Multimedia Software
---

### Post by IkeRay on 2010-07-14
I upgraded to 9.10 Karmic from 9.04 just today and I'm having video issues...

the videos played just fine prior to update, now as long as I keep them below fullscreen its fine, but as the video gets larger it becomes choppier and choppier...videos play just fine in Win2k as well.

my computer can't handle compiz advanced settings, I changed the window manager to metacity, output to GL since X11 is worse flickering, its tolerable but nothing like it was prior to update...

system specs:
2.4ghz P4
2gig ram
onboard graphics (8mb shared)

---

### Post by IkeRay on 2010-07-14
btw, CPU never goes over 90%, FF is 10-15%, nautilus is 10%, VLC never goes over 50%
RAM is 405mb/2000mb

increasing NICE to -20 helps slightly, but there is still obvious playback problems...

---

### Post by IkeRay on 2010-07-14
I've tried editing xorg.conf:

```
Section "Device"
Driver "Intel"
Option "AccelMethod" "UXA"
VideoRam 130560
```

per ```
lspci -vv
```

that didn't do anything.

I have noticed the screen says "VLC (x11 output)" where in 9.04 it didn't say anything other than VLC, the only time it said "(X11 output)" in Jaunty was when I had 2 videos opened, and the X11 was always choppy.

---

