---
title: "Best playback resolution"
date: 2009-03-07
forum: Mythbuntu
---

### Post by itlarson on 2009-03-07
What playback resolution will give the best picture?  My TV is 1366x768 but has no provision to take input at it's native resolution.  It can take hdmi input at 1280x720, 1920x1080i and 1920x1080p.  Is the best strategy to send it video at the video's native resolution, and let the TV convert the signal? Or should I stick with a single output resolution, and let mythtv convert the signal, only to be re-converted by the TV?  I could use 1080p But VDPAU would probably be required, and some xorg fiddling, since I need the GUI to be 1280x720 for use from across the room.  I am interested to know what is theoretically the best, to use as a starting point.

---

### Post by newlinux on 2009-03-07
If you can't give it it's native resolution, chances are your TV is optimized to to properly scale 720p, 1080i, and maybe 1080p content to its native resolution since that what most everything else will give it. Beyond that, What looks best is really user dependent/TV set dependent/etc. Try them all and see what looks best to you. I've gone through the same exercise on one of my sets (1366x768 native resolution) and I settled on 720p... but I watch a lot of fast action stuff and sports.

---

### Post by itlarson on 2009-03-07
I've mostly just used 720p, but always thought 1080i stuff might be better if I changed resolutions for it.  I don't think xorg is set up quite right for this though, it gives 57hz as the highest rate.  My TV's manual says 60hz is prefered.

---

### Post by itlarson on 2009-03-07
After some playing around with settings, I notice that the 1920x1080 50hz setting in "separate playback and gui video modes" is progressive.  However my TV prefers 60hz according to the manual.  Is there a way to get 60hz to come up here?  It's no problem to get this mode from nvidia-settings.  1080p seems to use about the same amount of cpu as 720p, But the picture seems better.

---

