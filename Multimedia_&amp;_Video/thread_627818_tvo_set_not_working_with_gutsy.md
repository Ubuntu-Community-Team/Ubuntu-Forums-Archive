---
title: "tvo_set not working with gutsy"
date: 2007-11-30
forum: Multimedia &amp; Video
---

### Post by barney_1 on 2007-11-30
Hi Folks,

I upgraded to Gutsy last night and am trying to get everything working again.  I had been using the Gatos driver with the tv_out patch and have that working again.  Under Feisty I was able to use the tvo_set utility to fit the image into my tv-screen (if was off-center and too small).  I'm trying to do that now but am having no luck.  Here's what I get:

```
$ tvo_set set hpos 0
tvo_set: Unable to open display
```

Any help is greatly appreciated!

---

### Post by barney_1 on 2007-11-30
Hmmm.... seems I'm the problem.

I was trying to run from the shell (CTRL-ALT-F1).  I guess these commands need to be run from X through a terminal emulator.

FYI - I learned a new trick in using tvo_set to get your positions and sizes just right.  Use the format of inc and dec (eg: tvo_set inc hpos) until you get everything looking right, then you can run:
```
xvinfo
```

Look for the lines regarding XV_TVO_HPOS, XV_TVO_VPOS, and XV_TVO_HSIZE.  This will tell you what those values are currently set to so that you can put them into a shell script to be run when the system first boots.

---

