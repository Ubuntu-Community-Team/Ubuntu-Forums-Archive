---
title: "Problems using Mythtranscode and Channel Guide"
date: 2008-06-20
forum: Mythbuntu
---

### Post by ilcapo09 on 2008-06-20
Hi there, it's my first time installing Mythbuntu and I'm really happy with it so far. I'm not Linux savvy but I've been able to get it up and running.
But there are two issues that I can't seem to resolve and I haven't found any answers searching through the forums.
When I try to transcode a recording, the CPU jumps to 100% even though I set the CPU priority to Low for Jobs and I only allow one job to run at a time.
The second issue I have is with the Channel Guide. It just freezes and isn't very responsive, taking over a minute to either move from channel to channel or to exit it. I've checked top thinking that the CPU would be maxed out but it stayed at around 20% and the corner image was running smoothly.

I run an AMD 1600 LE 2.2Ghz, 1GB RAM, 2 SATA2 drives, WinTV PVR-150 and a NVIDIA 7300 GS card with S-Video output.

---

### Post by andrewc6l on 2008-06-21
I can answer your first question: if there are no other tasks competing for CPU, even a low priority task can end up taking 100% of CPU. If a higher priority task starts, it will take precedence.

I'm not sure why you see the OSD freeze. I see it too (nVidia 6200)... if you figure it out, please post the answer! There is some discussion here:
[http://ubuntuforums.org/showthread.php?t=722563&highlight=osd](http://ubuntuforums.org/showthread.php?t=722563&highlight=osd)

I've also heard that changing the playback profile to "Slim" will help with the stuttering OSD - but when I do that, my playback is unacceptably jerky, which doesn't seem right on a 3GHz machine.

---

### Post by ilcapo09 on 2008-06-21
Hey, thanks for the tip. I actually noticed that it doesn't hog the CPU and it just runs at 100% but without overtaxing the system. The temperature reads around 63 which I don't think is that high.
I'm going to check about the Channel Guide. The OSD works well in all situations except in the Guide so I'll let you know my findings.

---

### Post by ilcapo09 on 2008-06-26
Well, I did what you told me but it didn't help much. Then I switched the paint engine from OpenGL to QT and it worked a little bit better but occasionally it would stutter. The one thing I noticed is that when I'm stuck in the channel guide if I open another app from the Xfce panel and then toggle back and forth with Alt+tab the guide will start working normally... really odd.

---

### Post by Archmage on 2008-06-26
Are you using the restricted driver or the open source driver for your graphic card?

---

### Post by ilcapo09 on 2008-06-26
I'm using the proprietary driver from Nvidia.

---

### Post by DutchLoki on 2008-06-26
wat kind of file are you transcoding? sd or hd (mpeg2 or mpeg4)?

---

