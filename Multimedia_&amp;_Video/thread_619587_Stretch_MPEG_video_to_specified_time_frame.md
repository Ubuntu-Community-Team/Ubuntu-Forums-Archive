---
title: "Stretch MPEG video to specified time frame?"
date: 2007-11-21
forum: Multimedia &amp; Video
---

### Post by Githlar on 2007-11-21
In my Windows days, I liked to use a scripting language called AVISynth for a lot of my video editing. I know in AVISynth there is a way to stretch a video to a certain length. However, I'm unsure of how to do this in Linux/Ubuntu.

Here's the deal. I'm using XVidCap to capture my screen, but for some reason I get a very high frame drop rate (around 60%). So, the resulting video is much faster and shorter than I originally planned. I'd like to stretch this video to the time which XVidCap reports by duplicating the necessary frames or any other means.

Anybody know of a program that can do this?

---

### Post by colo on 2007-11-21
mencoder can; the option is called -ofps (for "ouput frames per second"), if I recall correctly.

---

