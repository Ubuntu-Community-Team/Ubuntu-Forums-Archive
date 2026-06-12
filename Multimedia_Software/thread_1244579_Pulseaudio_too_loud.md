---
title: "Pulseaudio too loud"
date: 2009-08-19
forum: Multimedia Software
---

### Post by domagoj412 on 2009-08-19
Hello,
Today I've installed linux mint (based on ubuntu jaunty) and have problem with pulseaudio...
It is too loud and quality is not good...
But when I open "pulseaudio volume control" and decrease application volume (for example rhythmbox) to about 60% - quality is ok. The problem is that for every app I open (firefox, vlc...), I need to do the same thing...

Can I somehow configure pulseaudio to set that volume to 60% by default?

---

### Post by ajgreeny on 2009-08-19
Try reducing the PCM channel in Volume Control.  I find that with that at 100% there is some distortion, but at 80% all is OK, and the master volume channel can then be set to 100% if needed without distortion.

---

### Post by Stochastic on 2009-08-19
Moved to Multimedia & Video.

---

### Post by domagoj412 on 2009-08-20
> **ajgreeny said:**
> Try reducing the PCM channel in Volume Control.  I find that with that at 100% there is some distortion, but at 80% all is OK, and the master volume channel can then be set to 100% if needed without distortion.
Tnx. That worked! I needed to decrese it to about 45%...

---

