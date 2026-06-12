---
title: "Various video and sound problems"
date: 2007-06-06
forum: Multimedia &amp; Video
---

### Post by Rhapsody on 2007-06-06
I've been through a fair few problems recently (no sound, NVIDIA drivers not working) but I think I'm near the tail end of it all. I have a few problems left though.

After installing NVIDIA drivers, I had various problems with refresh rate. I solved most of these by telling KControl exactly what monitor I have (Samsung SyncMaster 793s). However, despite xorg.conf having Horizsync set to 30-71 are Vertrefresh to 50-160, KControl will only let me set the refresh rate to 72Hz in 1024x768. I know these settings should allow me to go higher, and  know all of my hardware can take up to 85Hz in the resolution. So why can't I do it?

In another strange problem, while MPlayer appears to work perfectly (playing a video file from the command line works just as I'd expect) the GMPlayer frontend acts differently, with exactly the same file playing slowly, jerkily, and without any sound. The exact error being "Could not open/initialize audio device -> No sound". I don't see how this is possible, but it's happening.

Finally, despite sound now working on this system (command line MPlayer and Amarok can confirm this for me), Flash videos and Firefox don't give any sound whatsoever.

All in all, I seem to have a nice variety of weird problems here, but I've certainly made advancements with this PC recently. I hope I'm finally nearing the end of my problems.

---

### Post by Rhapsody on 2007-06-06
I've managed to fix the refresh rate problem by using nvidia-settings, so that's fine now. The rest of the problems are still present though.

---

