---
title: "[SOLVED] VLC crashes ubuntu"
date: 2008-08-28
forum: Multimedia Software
---

### Post by MasterSander on 2008-08-28
When I play a video file with vlc, it sometimes crashes my computer (I can still move my mouse, but I can't click anything and no keyboard shortcuts work), the only thing that works is a reboot, which is ofc rather annoying. Anyone else got this problem, or can help?

---

### Post by markbuntu on 2008-08-28
Try changing the output preference to Xv in the video section. Some of the choices there will crash your system depending on your video card. You just need to find the ones that work for you.

---

### Post by Crafty Kisses on 2008-08-28
When you open VLC, post the results of > top

---

### Post by MasterSander on 2008-08-29
> **Codename said:**
> When you open VLC, post the results of > top

There's nothing unusual about vlc when I just start it, and when it freezes I can't use top anymore since I can't do anything (not even command line)

---

### Post by MasterSander on 2008-08-30
> **markbuntu said:**
> Try changing the output preference to Xv in the video section. Some of the choices there will crash your system depending on your video card. You just need to find the ones that work for you.

Tried this as well, but also crashed, I'll try changing it to OpenGL now

---

### Post by MasterSander on 2008-08-30
> **MasterSander said:**
> Tried this as well, but also crashed, I'll try changing it to OpenGL now

OpenGL worked! Although if I right-click the menu appears and then dissappears instantly, I'll try some other engines as well.

---

