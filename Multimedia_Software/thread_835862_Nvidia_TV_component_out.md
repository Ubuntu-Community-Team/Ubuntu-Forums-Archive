---
title: "Nvidia TV component out"
date: 2008-06-20
forum: Multimedia Software
---

### Post by Brian96 on 2008-06-20
I recently bought a couple of 7000 series nVidia geforce cards and have had FITS getting them to work with my TV. I finally got one to work with s-video using a workaround.

The machine I am struggling with now has a 7600 GT OC on a 32-bit Hardy system. I had a great deal of trouble using the s-video to component adapter, but I got better component cables and now it works BEAUTIFULLY in XP. However, in Hardy I get a sort of "blue scale" picture. If I unplug the blue RGB cable, I get an overly red image.

I have tinkered with every setting I know to mess with in the nvidia-settings panel. Anybody have this problem that got it to work successfully? I know this is not a hardware issue as it works fine (finally) in XP.

Thanks in advance.

---

### Post by cariboo on 2008-06-21
Give **nvtv** a try it is designed to use the s-video out on your video card. It is available in the repositories. Use System-->Administration-->Synaptic Package Manager to install it.

Jim

---

### Post by Brian96 on 2008-06-21
> **cariboo907 said:**
> Give **nvtv** a try it is designed to use the s-video out on your video card. It is available in the repositories. Use System-->Administration-->Synaptic Package Manager to install it.

Jim

Thanks. Apparently my card is not compatible with nvtv.

Has anybody else had this problem with the component out?

---

### Post by Brian96 on 2008-06-21
I found an old thread on the same issue, but I can't tell for sure whether anybody truly solved this same issue.

[http://ubuntuforums.org/showthread.php?t=450734](http://ubuntuforums.org/showthread.php?t=450734)

---

### Post by Brian96 on 2008-06-21
Okay, I got full color by going here: [ftp://download.nvidia.com/XFree86/Linux-x86/](ftp://download.nvidia.com/XFree86/Linux-x86/) and finding the folder for my driver (which is currently 169.12) and manually configuring my xorg.conf file with settings I found there.

What worked for me was adding < Option "TVStandard" "HD480i" and < Option "TVOutFormat" "COMPONENT" to the "Device" section for my video card.

However, the picture quality is very poor. I have curves at the top of the screen, and the picture is grainy. More like a composite picture than a component picture. Any ideas why that may be? 

(Also, I'm not going to mark the thread solved because of the poor quality. Defeats the purpose of using RGB connections if the picture is still crappy.)

---

