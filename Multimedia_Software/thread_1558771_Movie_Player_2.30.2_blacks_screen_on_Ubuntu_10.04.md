---
title: "Movie Player 2.30.2 blacks screen on Ubuntu 10.04"
date: 2010-08-22
forum: Multimedia Software
---

### Post by Jazzmaster94 on 2010-08-22
When Movie Player is started the screen blacks out for several seconds, returning my screen to normal with no change in resolution.  My system makes use of the ATI Radeon X1350 Pro with the X.org opensource "radeon" drivers.  Has anyone else experienced this glitch?

---

### Post by cpjkennedy on 2010-09-04
My set up does the same thing.  Totem goes grey for a few seconds and doesn't respond, then works for a few minutes, then repeats the problem.  Restarting the computer fixes the problem for a few days.

Also, when I try to play any video file with mplayer, it comes up "Error opening/initialising the selected video_out (-vo) device."

---

### Post by andrew.46 on 2010-09-05
Hi cpjkennedy,

> **cpjkennedy said:**
> Also, when I try to play any video file with mplayer, it comes up "Error opening/initialising the selected video_out (-vo) device."

Could you try playing a video from the commandline as follows:

```
mplayer -v *my_file*
```

substituting *my_file* for the path and name of your actual file? The terminal output will give some idea about what is going wrong...

Andrew

---

### Post by Cypress421 on 2010-09-05
Try a frontend for mplayer such as smplayer, then run it and change the output to GLX. Try one of the outputs to see which one works. Or in a Terminal use the -vo switch to choose.

---

