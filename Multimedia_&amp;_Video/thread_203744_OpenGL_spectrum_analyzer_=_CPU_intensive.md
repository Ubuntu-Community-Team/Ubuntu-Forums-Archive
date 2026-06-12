---
title: "OpenGL spectrum analyzer = CPU intensive?"
date: 2006-06-25
forum: Multimedia &amp; Video
---

### Post by Kensey on 2006-06-25
So I was testing new visualizations to go along with amaroK, and I left the old standby OpenGL Spectrum Analyzer running for awhile.  Suddenly I looked at my menu bar and noticed the CPU temp was up around 73-74 C.  Well MP3s just aren't supposed to be that CPU-intensive to decode, so I closed OGL SA and what do you know?  The temp almost immediately dropped below 50 (currently at 43-45 C about 5-6 minutes later).

Is OpenGL stuff *that* intense on the CPU?  Or is something radically wrong here?

This is a Dell Latitude D610, with a Pentium-M 1.86 GHz CPU.

---

### Post by bikeboy on 2006-06-25
If you havn't set up hardware acceleration the OpenGL stuff will be rendered by the cpu. What sort of graphics chip does your Dell have? You may need to install the binary drivers from nvidia or ati.

---

### Post by Kensey on 2006-06-26
It's got Intel GMA900 graphics in it.

---

### Post by bikeboy on 2006-06-26
I don't know much about those intel chips but try this to see if you are getting hardware acceleration.```
glxinfo | grep rendering
```

---

### Post by Kensey on 2006-08-06
`glxinfo | grep rendering` says "direct rendering: Yes" which I assume means acceleration is active.

---

