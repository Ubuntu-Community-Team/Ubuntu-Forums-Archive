---
title: "error returned with fglrxinfo"
date: 2006-12-20
forum: Multimedia &amp; Video
---

### Post by LantagoniE on 2006-12-20
Hello.

   Yesterday, i typed the command fglrxinfo in a terminal for the first time in a while and i noticed that it returned me an error.

```
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X800 Series Generic
OpenGL version string: 2.0.6011 (8.28.8)

```

   I have beryl installed, however, and it's still working perfectly.  And no other problem has been noticed in my Ubuntu system.  But i'm just curious as to what might cause this error to pop up when i type fglrxinfo.  Any ideas?  :-k

---

### Post by dkbg on 2007-01-07
I am in the same situation. I have XGL and Beryl installed and they work perfectly except for that error. I also get it when I run programs with Wine (although they work fine). Since everything works well, its not really a problem, but I really dislike seeing errors and not knowing what they mean.

Another thing is that before I installed XGL and Beryl checking for direct rendering confirmed that it was on, but after installing them, it gives me a "no". Any ideas why?

---

### Post by dkbg on 2007-01-07
Okay, I just installed the latest proprietary ATI driver (I was using the open source one) and the error no longer appears in the fglrxinfo output, but direct rendering is still reporting as "no" in glxinfo.

---

