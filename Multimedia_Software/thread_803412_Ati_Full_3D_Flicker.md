---
title: "Ati Full 3D Flicker"
date: 2008-05-22
forum: Multimedia Software
---

### Post by Jellman on 2008-05-22
Hi there, im having a problem with my ati x1250 gfx on my laptop using ati proprietary driver 8.47.3 (via envyng). When ever i try and launch a 3d application ie glxgears or a game like WOP i get like a flicker effect on the 3d render. Alltho the speed of the render is fine (ie 3000 FPS in fgl_glxgears).

Is there any workarounds for this problem. Ive attaced an image which shows basically whats wrong.

Thanks in advance,
Scott

---

### Post by sanus|art on 2008-05-22
I had the same issue and found that this kind of behavior was triggered by wrong resolution specification.

---

### Post by Jellman on 2008-05-22
My resolution seems to be set correctly 1280x800@60hz (the same as in windows) if that helps.

---

### Post by sanus|art on 2008-05-22
I mean in the application settings.

---

### Post by Jellman on 2008-05-22
i would assume that-that isn't the problem as glxgears is a windowed application so i dont think that would apply, are you still having the same problem as me? what happens when you run fgl_glxgears from the terminal?

---

### Post by sanus|art on 2008-05-22
> **Jellman said:**
> i would assume that-that isn't the problem as glxgears is a windowed application so i dont think that would apply, are you still having the same problem as me? what happens when you run fgl_glxgears from the terminal?

I think I still having this problem in my laptop while I tried to see some videos. 
'fgl_glxgears' will not output anything for me as I don't have fglrx installed.

---

### Post by brunolabs on 2008-05-22
With the Desktop Effects on I also have that problem.
Try to disable them.

---

### Post by Melcar on 2008-05-22
Disable Desktop Effects.  This would also apply for all Xv/OpenGL renderings (movies, screensavers, games, etc.).

---

### Post by Jellman on 2008-05-23
Is there no other workarounds for this problem apart from disabling compiz, (i dont get the problem on movies, just scrnsavers, games etc). 

Is this just ati being the usual selves?

---

