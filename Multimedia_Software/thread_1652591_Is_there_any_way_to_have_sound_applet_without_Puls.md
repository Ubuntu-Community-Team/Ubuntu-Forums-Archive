---
title: "Is there any way to have sound applet without PulseAudio?"
date: 2010-12-25
forum: Multimedia Software
---

### Post by KutViZ on 2010-12-25
Hi everyone,
Yesterday I decided to remove pulse (mainly because Skype was unable to work with it) but suddenly the sound icon is gone. After some searching on the net I understood that it was part of pulseaudio, but now i feel a bit lost. Alsa works like a charm instead, but since I also want to use ubuntu to record sound i'm not sure if it will work, and also I have a sound source for my HDMI interface and don't know how switch if i want to.
Machine: laptop HP dv6 pavilion 3070eh

Help! :)

---

### Post by KutViZ on 2010-12-25
Ok now I can switch between devices, System->Preferences->Sound responses :KS

But still need an applet, I want to make it more comfortable...

---

### Post by KutViZ on 2010-12-25
wow it's weird I tried to install libgtk-trayicon-perl and some other stuff from synaptic, now audio hotkeys not working and sound in system->preferences is not responding again...****

---

### Post by lidex on 2010-12-25
Sorry I don't have time right now but here is a reference:
[http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html#installing](http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html#installing)

---

### Post by KutViZ on 2010-12-25
Well I ran the script of the alsa configuration but nothing has changed. Or at least it looks like that.

---

### Post by KutViZ on 2010-12-27
Solved finally! Here's the guide i used: [http://levien.zonnetjes.net/?q=oss4](http://levien.zonnetjes.net/?q=oss4)

The applet (ossxmix) is quite big but usable.

---

