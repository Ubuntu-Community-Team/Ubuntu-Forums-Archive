---
title: "XGL Absent issue with Beryl on Nvidia GeForce4 440"
date: 2007-01-29
forum: Multimedia &amp; Video
---

### Post by mikebai1990 on 2007-01-29
Hey guys,

I recently installed beryl onto my laptop, hoping to play around with the interesting features I always hear about but am unable to actually see for myself. I have my nvidia driver installed and I followed the tutorial of how to set up beryl. I have everything installed now, but when I run beryl, I have this error:

```
michael@ubuntu-michael:~$ beryl
XGL Absent, checking for NVIDIA
Nvidia Present
Relaunching beryl with __GL_YIELD="NOTHING"
XGL Absent, checking for NVIDIA
Nvidia Present
beryl: No composite extension
```

I'm quite a novice when it comes to beryl, since I have only started reading and experimenting with it. I'm not sure what I should do to fix this problem.

If there's anything else needed for you guys to help me out, I'd be more than willing... I would appreciate any comments or suggestions to solve this problem.

---

### Post by Waappu on 2007-01-30
Hi

I don't have nvidia card but have you read this guide ?
[http://ubuntuforums.org/showthread.php?t=263851](http://ubuntuforums.org/showthread.php?t=263851)

Do you have these lines in your /etc/X11/xorg.conf file?
```
 Section "Extensions"
     Option "Composite" "Enable"
 EndSection
```


Look also this
[http://wiki.beryl-project.org/wiki/Troubleshooting_nVidia](http://wiki.beryl-project.org/wiki/Troubleshooting_nVidia)

---

### Post by mikebai1990 on 2007-01-30
Waappu, I cannot thank you enough! It works after I changed the code. Before it was set to "Composite" "Disable". Thank you again, now I can play with beryl!

---

