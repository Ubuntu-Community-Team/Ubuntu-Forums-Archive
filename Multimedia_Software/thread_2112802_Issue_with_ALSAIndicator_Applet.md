---
title: "Issue with ALSA/Indicator Applet"
date: 2013-02-05
forum: Multimedia Software
---

### Post by Fireye00 on 2013-02-05
I've been having issues with the Gnome Indicator, and can't quite track down a decent fix.  The Indicator Applet (And by extension, the Control Panel --> Sound menus) appear to be doing something odd with the Output Volume.

When the output volume slider in the applet is at 100%, alsamixer shows Master and Speaker at 100%.  At around 20-30% Output Volume in the Applet, alsamixer shows 0% for Master, and 100% for Speaker.    At around 10-15% Output Volume in the applet, alsamixer shows 50% for the Speaker channel.

Because of this, when I set the Output Volume in the applet to greater than 30%, there is no effect on the volume.  The result is, that all of my volume is compressed into that ~30% on the Applet's Output Volume slider.

Manually setting the Speaker volume to 50% via alsamixer works fine, however when I alter the Master volume in alsamixer it has no effect on output volume.

I'd really like to get the full range of volume via the Applet back, can anyone give me some pointers on how to do that?

So far, I've tried doing the following, which didn't hurt, but didn't help:
```
sudo apt-get remove --purge alsa-base
sudo apt-get remove --purge pulseaudio
sudo apt-get install alsa-base
sudo apt-get install pulseaudio
sudo apt-get install gnome-alsamixer
sudo apt-get install indicator-sound
sudo alsa force-reload
```


Edit: Running 12.04 LTS Desktop

---

