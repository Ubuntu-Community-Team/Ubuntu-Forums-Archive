---
title: "nVidia FX5200 and LCD Syncing"
date: 2008-06-03
forum: Multimedia Software
---

### Post by CNLiberal on 2008-06-03
I used to have MythDora 4.0 installed.  I never did any updates.  Then one day, out of the blue, my monitor started losing sync.  Every few seconds it would blink.  Then, I installed MythBuntu and was having difficulty with the nVidia drivers.  They wouldn't load.  So I left them off.  This morning, new drivers came out, I loaded them up and they seem to work.  However, the syncing issue is back.  How can I fix this?  What logs can I post to help solve this issue?  Thanks for your help!

Jim

---

### Post by Pjotr123 on 2008-06-03
You could give this a try:
[http://ubuntutip.googlepages.com/bugsinubuntu](http://ubuntutip.googlepages.com/bugsinubuntu)
(number 2)

---

### Post by CNLiberal on 2008-06-04
Thank you for your reply.  I've run through the steps you suggested.  It doesn't seem to have done any good.  Whenever I run 'glxgears' the screen sync issue gets VERY bad.  Here is the result of 'glxgear'.

joltman@mythbackend:~$ glxgears -display :0
303 frames in 5.0 seconds = 60.402 FPS
301 frames in 5.0 seconds = 60.021 FPS
301 frames in 5.0 seconds = 60.021 FPS
301 frames in 5.0 seconds = 60.021 FPS
301 frames in 5.0 seconds = 60.007 FPS

This doesn't seem like a lot for an FX5200 card.  Plus the screen flicker issue is a mystery.  Where can I look for errors?  I enabled "Sync to VBLank" in nvidia-settings and it didn't make any difference.  This only happens when I use the nvidia drivers.  Thanks!

Jim

---

### Post by CNLiberal on 2008-06-07
OK, still no new information.  I was hoping that someone could help me in figuring this out.  Am I making my problem clear?  It seems that the LCD blinks off for a moment then comes back on. I can't see a pattern to this.  Whenever I start 'glxgears' the screen goes totally black.  The screen goes black like it's not plugged into a source.  I don't know where the log for something like this is kept.  Does anyone know where I can start on this problem?

---

