---
title: "XGL not present karmic"
date: 2010-01-30
forum: Multimedia Software
---

### Post by Da CalebMan on 2010-01-30
Hey guys, 

I have notice when I run compiz in terminal, I get this:```
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1280x1024) to maximum 3D texture size (4096): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 

```

So how do I install XGL on ubuntu Karmic? All the guides I found are way too outdated.

Please help!

---

### Post by Yellow Pasque on 2010-01-30
```
All the guides I found are way too outdated.
```
..because XGL is outdated. Don't install XGL. You don't need it if you have AIGLX (which nvidia driver does). Is there a problem you're experiencing or were you just confused by the output?

---

### Post by Da CalebMan on 2010-01-30
Ah, no wonder. Well I thought XGL would be a special boost for 3D graphics performance, seeing as all the youtube videos about compiz talk about XGL and Beryl too. Oh well.:D

THANKS!:popcorn:

---

### Post by quequotion on 2010-03-04
> **Da CalebMan said:**
> all the youtube videos about compiz talk about XGL and Beryl

Somehow the youtube videos, and a lot of other sources of information about compiz, are not even close to keeping up with development....

---

