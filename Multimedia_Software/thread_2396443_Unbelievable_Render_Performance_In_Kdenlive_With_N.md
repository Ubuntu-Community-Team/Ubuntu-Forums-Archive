---
title: "Unbelievable Render Performance In Kdenlive With NVENC - But 1 Big Problem"
date: 2018-07-16
forum: Multimedia Software
---

### Post by immortanjohn on 2018-07-16
System: i5 6600K, 1050TI, Ubuntu 18.04, Kernel 4.16
I have successfully compiled mlt and ffmpeg with nvenc support using the official nvenc headers stripped from the Nvidia SDK.
Rendering the first minute of the 1080p Sintel version, with 4 threads specified and my nvenc profile, finishes in 10 seconds.
Sintel can be downloaded here: [https://durian.blender.org/download/](https://durian.blender.org/download/)
Nvenc Profile: (compatible with recent mlt versions who are nvenc enabled by deafult)
f=mp4 vcodec=nvenc_h264 global_quality=21 vq=21 preset=slow bf=2 ab=384k

[B]
Now here is the problem that I do not understand:[/B]
Using the latest version of kdenlive from the kdenlive-master ppa combined with the newly compiled versions of ffmpeg and mlt works perfectly, but **only** under very s**pecific circumstances**.

I have only been able to get rendering with nvenc to work properly when I use and open this specific kdenlive **save file** which I made of the first minute of the Sintel short film with the Appimage Version of Kdenlive. After launching the ppa/installed version of kdenlive and opening this save file, rendering with nvenc works flawlessly.

If I simply start a new project, adding the whole Sintel short film to the project bin, cutting the first minute and render it, nvenc simply does not work and the render time is tripled, despite having changed nothing else, including the nvenc render profile.

If I create a save file of the first minute of Sintel with the installed version and open it on the Appimage version, nvenc does not work again.

**Conclusion**: There must be something in this save file, maybe a parameter, additonal settings or any type of code not present in the default kdenlive project profiles, which enables NVENC.

I would greatly appreciate it if we could find out the source of this problem together.

**Kdenlive Appimage Save File with which NVENC works:**
[https://pastebin.com/rzjR57DJ ]("https://pastebin.com/rzjR57DJ")

**PPA/Installed Version of Kdenlive created Save File which breaks NVENC:**
[https://pastebin.com/3uQ8sP0C](https://pastebin.com/3uQ8sP0C)

---

### Post by deadflowr on 2018-07-16
*Thread moved to **Multimedia Software***

---

### Post by kazakore on 2018-07-17
> **immortanjohn said:**
> 

**PPA/Installed Version of Kdenlive created Save File which breaks NVENC:**
[https://pastebin.com/3uQ8sP0C](https://pastebin.com/3uQ8sP0C)

So the PPA version of KDenLive still works for you? I wonder why it will no longer boot on my system then...... :(

---

