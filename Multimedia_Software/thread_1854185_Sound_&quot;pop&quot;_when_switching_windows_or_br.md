---
title: "Sound &quot;pop&quot; when switching windows or browser tabs"
date: 2011-10-03
forum: Multimedia Software
---

### Post by 3602 on 2011-10-03
OK this is sort of a weird problem.

Sometimes I listen to music online while browsing. Sometimes, not always, when I change the tabs (I use the latest stable Google Chrome) or change windows (such as between Chrome and Nautilus), there is a "pop" in what I hear. This pop exists in both my earphones and my computer speakers.

The problem is less severe when using RhythmBox, but is still nonetheless present.

```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Now obviously I'm using the analog output and not the HDMI output.

So two questions. Naturally, how do I fix this (is it software or hardware)? But more importantly, would a USB-DAC solve this problem?

Thank you all very much.

---

### Post by 3602 on 2011-10-05
Bump.

---

### Post by 3602 on 2011-10-06
Bump.

---

### Post by youngmit on 2011-10-25
I am having a very similar problem. It seems that whenever there is a significant amount of screen activity (scrolling, opening new windows, resizing windows, etc.) it causes a pop in the sound. This happens even if the sound is muted. :-O

I am on a new thinkpad T420 with a fresh install of 11.10.

any ideas?

Thanks!

---

### Post by 3602 on 2011-11-25
It's the driver. Maybe try updating ALSA or whatever audio driver that you use.

---

