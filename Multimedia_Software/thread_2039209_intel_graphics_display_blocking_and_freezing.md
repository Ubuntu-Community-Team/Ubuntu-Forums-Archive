---
title: "intel graphics display blocking and freezing"
date: 2012-08-08
forum: Multimedia Software
---

### Post by BetterSense on 2012-08-08
My Ubuntu system is doing a strange video-blocking thing. It’s hard to describe, but it’s as if small sections of the display become mirrored a few hundred pixels to the right. I attached some pictures. The screen does not lock up immediately, and if you move windows around through the bad sections, the motion is exhibited in the mirrored sections as well. It just makes it really hard to do work because you lose bits of the display. But eventually there will become more and more blocks until the system locks up. I can’t switch to a text terminal with Ctrl+Alt+F3, but alt+SysR+B will reboot. 

This problem started suddenly after about 6 months of uptime. It’s possible that I upgraded my kernel, but I don’t remember doing it. 

I think this has something to do with my onboard intel graphics and some video driver or kernel mode setting. I have googled but it’s really hard to find info when I don’t know what the problem actually is. Can anyone help guess what this is so that I can find a solution?

---

### Post by BetterSense on 2012-08-08
I just confirmed that this happens on 2.6.35-31 and 2.6.35-22. 

Are there any system logs I can check to find out exactly why it's crashing?

---

