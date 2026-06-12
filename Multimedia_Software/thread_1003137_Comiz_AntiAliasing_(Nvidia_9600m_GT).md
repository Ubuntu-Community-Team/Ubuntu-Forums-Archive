---
title: "Comiz AntiAliasing (Nvidia 9600m GT)"
date: 2008-12-05
forum: Multimedia Software
---

### Post by The_Real_Bacon on 2008-12-05
```
config@VIRUS:~$ nvidia-settings -l && compiz --replace&
[1] 8635
config@VIRUS:~$ Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1680x1050) to maximum 3D texture size (8192): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
```

Driver: 177

Been looking around and I can't figure this one out. I'd really like to use aa, because I get too many jaggies using the desktop cube. Any help would be appreciated. I'm going to continue my googling. I'll post again if I end up fixing it.

---

### Post by iphonegames on 2008-12-05
lol. Check my new [iphone games](http://www.iphonegames3g.com) site for iphone and ipod touch when you have time! :)

---

### Post by psyke83 on 2008-12-05
> **The_Real_Bacon said:**
> ```
config@VIRUS:~$ nvidia-settings -l && compiz --replace&
[1] 8635
config@VIRUS:~$ Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1680x1050) to maximum 3D texture size (8192): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
```

Driver: 177

Been looking around and I can't figure this one out. I'd really like to use aa, because I get too many jaggies using the desktop cube. Any help would be appreciated. I'm going to continue my googling. I'll post again if I end up fixing it.

You can force it system-wide via nvidia-settings.

If that's not acceptable, then you can edit the compiz wrapper script and insert the environment variable in front of the "compiz.real" command.

Look here: [http://us.download.nvidia.com/XFree86/Linux-x86/177.82/README/chapter-11.html](http://us.download.nvidia.com/XFree86/Linux-x86/177.82/README/chapter-11.html)

Specifically, the variable you want to specify is __GL_FSAA_MODE - read the link above for more information and what value to choose.

---

### Post by The_Real_Bacon on 2008-12-05
hahaha, I just realized I wrote "comiz"

I was aware of those settings. I have played with them to no result.

---

