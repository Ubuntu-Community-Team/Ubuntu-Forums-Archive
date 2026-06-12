---
title: "can't get mic working"
date: 2008-10-23
forum: Multimedia Software
---

### Post by chilimac02 on 2008-10-23
I'm a noob to all things ubuntu, but I know enough to check the right boxes, etc. I just can't seem to get my laptop's built in mic to work...

i have an hp tx1320us, by HP.

---

### Post by Kalinda on 2008-10-23
You can do two things here. First the easy way:

Open KMix (the little speaker icon in your system tray); it should have mic options in the input section. Try turning up the volume for your mic and for capture, which is espeically important. Micboost might also be available under Switches, where you select your mic as your analog source and whatnot. Have you already tried that?

If that doesn't work, then:

Open Konsole (hit alt+F2 and then type "konsole"), type the following:

```
alsamixer
```

After that, press F4 to bring up the Capture section, then turn up the Capture by pressing the up arrow. Also turn up the Mic. You may have to play with it. Pressing F3 gets you back to the main page, where you can also play around.


Now, if that still doesn't work, the harder way:

You need to find out exactly which sound card you have (harder if you've got a laptop), then figure out which [ALSA]("http://en.wikipedia.org/wiki/Advanced_Linux_Sound_Architecture") driver that card uses.

Once you know your card, [go here]("http://bugtrack.alsa-project.org/main/index.php/Matrix:Main") and find your card on the ALSA sound card matrix, they are sorted by vendor.

From here, you should get a link to page for your driver which should have information about getting your mic working or if it even works at all. Some drivers lack mic support.

Good luck!

---

