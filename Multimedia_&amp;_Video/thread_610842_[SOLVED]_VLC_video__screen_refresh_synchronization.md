---
title: "[SOLVED] VLC video / screen refresh synchronization"
date: 2007-11-12
forum: Multimedia &amp; Video
---

### Post by Ux64 on 2007-11-12
Hi! 

I tried to look for threads about this subject, but I failed miserably. So here is my problem.

When playing back videos with VLC, screen frame synchronization fails. Meaning that I have top of screen from previous frame and bottom of screen from current frame. 

I went trough VLC video settings, but I coulnd't find any setting that would fix this. I guess this is FAQ kind of stuff. But I couldn't get proper answer from Finnish Ubuntu forums. So now I'm asking here.

- Thank you!

Br,
Ux64 (Ubuntu 64 bit 7.10 GG)

---

### Post by deadgobby on 2007-11-12
I am going to give shot in the dark. It may be the 64 bit kernel. The 64 kernel is work in progress and can be buggie. Have you had this problem before with different versions of Ubie? Is this your first time with Ubie? Does this happen with the 32 bit kernel?
Gobby

---

### Post by JasonF on 2007-11-12
What Video Card and drivers are you using.

For nvidia, run 'nvidia-settings' to load the settings, select X Server Video Settings and enable syncing.  Then choose Xvideo output for vlc (You'll need to select the output modules section with advanced mode enabled to make the selection).

---

### Post by Ux64 on 2007-11-12
**Thanks you about hints, this far...**

I did run nvidia-config and yes, I found out many settings that I had been kid of looking for. Especially now I got right refresh rate 60 Hz instead of 50 Hz which was suggested by screen resolution feature.

And sync to vblank was already enabled. 
[[IMG]http://picozilla.com/files/142198tscreenshotnvidiaxserversettings.jpeg[/IMG]](http://picozilla.com/en/142198/screenshotnvidiaxserversettings.png.html)

I confirmed that VLC is using Xvideo by choosing it.

[[IMG]http://picozilla.com/files/142199tscreenshotpreferences.jpeg[/IMG]](http://picozilla.com/en/142199/screenshotpreferences.png.html)

I didn't reboot. Does it require it? 

I still have same problem as I did have earlier. Vblack sync is cleary missing or failing. Also I got additional screen flicker near frame shift lines. So it does look worse than having "only" parts on screen from two separate frames.

Any more ideas?

Questions did I have these problems earlier. Actually I did, but it was my old computer and ATI adapter and 32 bit Ubuntu 7.04. Now I got new comp with Nvidia 8500GT and Q6600. So there should be enough punch to take care of video decoding.

With my old comp I knew that I were running out of CPU power with Full HD h264 videos using high bit rate. (1 hour ~2-3 gigabytes) But there problems doesn't go away if I use lower quality video feeds.

---

### Post by JasonF on 2007-11-12
You don't wan't X11 video, lower on the list should be Xvideo extension video output.  If Xvideo isn't availble or gives you problems try setting vsync for OpenGL and use vlc's OpenGL output..

---

### Post by Ux64 on 2007-11-13
**Thank you! Problem solved.**My bad that messing up X11 / Xvideo mistake, now it seems to be working fine. I don't say perfectly. I didn't have in morning enough time. But in short tests I didn't find any problems anymore.

And I also enabled OpenGL sync at the same time when I went trough my display adapter configuration.

And to VLC dudes: I wonder what's VLC's "default" mode if it's not working well. Usually it's good idea to show option X (Default) not just (default) because it won't tell what the default value is.

Generic: I find out that many default settings and configurations aren't that prefect, so all aspects take some tuning. Which may not be so fun for normal user.

---

### Post by Ux64 on 2007-11-15
Update:

It's not perfect. Some tearing still happens. I guess now it's about kernel or something.

---

### Post by JasonF on 2007-11-15
Have you restarted X since you last ran nvidia-settings?

If you have the nvidia-settings settings are lost. You could add 'nvidia-settings --load-config-only' to your session to force them to reload when you log in.

---

### Post by Ux64 on 2007-11-18
> **JasonF said:**
> Have you restarted X since you last ran nvidia-settings?


Um, yeah.

> If you have the nvidia-settings settings are lost. You could add 'nvidia-settings --load-config-only' to your session to force them to reload when you log in.

Ok, thank you very much again. Actually settings are ok when I run nvidia-settings. But got activated only after running nvidia-settings.

**Thanks. **Now I'll look for thread how to get that done automatically when I start X.

I found it when I had time to look for it. - Thanks now it's working perfectly.

---

