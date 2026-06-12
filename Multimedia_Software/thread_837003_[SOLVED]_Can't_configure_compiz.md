---
title: "[SOLVED] Can't configure compiz"
date: 2008-06-22
forum: Multimedia Software
---

### Post by sofasurfer on 2008-06-22
I installed compiz.
I think all is well. Here is my "compiz" output:

```
Checking for Xgl: not present. 
Detected PCI ID for VGA: 02:00.0 0300: 10de:01d3 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1680x1050) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

```

Here is my "./compiz-check" output:

```
 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation G72 [GeForce 7300 SE] (rev a1)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

```

My problem is that I do not have a "System > Preferences > Advanced Desktop Effects Settings" entry. How do I aquire this nessessary option?

---

### Post by sofasurfer on 2008-06-22
O dang!! I figured it out. I installed "Compiz configuration settings manager". Bingo.

I sure wish there was a way to delete a post when we post stupid or needless messages and decide we wish we didn't do that.

---

### Post by HyperHacker on 2008-06-22
Best thing to do would be mark the thread as solved, which IIRC is under thread tools at the top, and just forget it ever happened.

---

