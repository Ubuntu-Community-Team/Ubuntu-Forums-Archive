---
title: "Another nvidia 180 high CPU issue..."
date: 2009-04-28
forum: Multimedia Software
---

### Post by fortytwo on 2009-04-28
Hey guys,
I've searched around and was overwhelmed by the amount of posts in relation to the nvidia drivers, but most of them seem to be reporting success or slightly different issues.

I just installed Intrepid on my media center and I'm having issues playing back HD files.  I've tried both the 177 and 180 nvidia drivers and found the same problem on both.  VLC stutters like mad and the CPU spikes way up.  

Although I (unfortunately) don't recall which nvidia driver I was using in Hardy, I was able to play back HD files without any problem.

I thought perhaps the problem may be reelated to H.264, but I'm not sure.  I'm going to see if I have any non-H.264 HD files.  Normal videos appear play fine, and while just in the desktop I don't have any problems.

Here's my xorg.conf:

```
Section "Monitor"
    Identifier  "Configured Monitor"
EndSection

Section "Screen"
    Identifier  "Default Screen"
    Monitor     "Configured Monitor"
    Device      "Configured Video Device"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier  "Configured Video Device"
    Driver  "nvidia"
    Option  "NoLogo"    "True"
EndSection
```



Any ideas/suggestions would be great, I'm getting behind on my movies! :)

---

