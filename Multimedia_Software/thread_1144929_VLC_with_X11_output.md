---
title: "VLC with X11 output"
date: 2009-05-01
forum: Multimedia Software
---

### Post by Dino05 on 2009-05-01
I'm running  VLC media player on Ubuntu 8.04 until I edit my preference to use X11 output. Now my media files won't run as good as before (default configuration) and I'm unable to turn off X11 output 'cause the buttons on the VLC panel won't respond to mouse clicks. Is there other ways to turn off X11 output? I would greatly appreciate an help.

---

### Post by andrew.46 on 2009-05-03
Hi Dino05,

I will confess that I am not sure if this works for *all* versions of vlc but you could try:

```
vlc --reset-config
```

and this should return all of your vlc options to default.

Andrew

---

### Post by Dino05 on 2009-05-04
thanks for the info, as soon as I try it out I will let you know.

---

### Post by HavocXphere on 2009-05-04
OpenGL output is the smoothest in my experience.

---

