---
title: "Sound in analog jack headphones is heavily low when fully plugged into PC"
date: 2014-08-24
forum: Multimedia Software
---

### Post by tuner90 on 2014-08-24
Hi!

Here's link to results of running [[COLOR=#008000]_ALSA Information Script v 0.4.63_[/COLOR]]("http://www.alsa-project.org/db/?f=76c6e9fe61d184c7bd4d50a8f5577f346e3a20ec").

When my headphones are plugged into PC front panel, there's almost no sound - only some low volume (when I turn up the volume to 100%) and few of channels are muted while playing music.
When I half (un)plug from/into panel, sound works normally. But such solution is total stopgap.

I'm searching through google almost 2nd day, but still nothing found that could help me.
But so far I understood that it's something with ALSA, Pulseaudio and ALC888 driver (intel hda chip).

What I've got to do?

Thx.

---

### Post by Yellow Pasque on 2014-08-24
First suggestion is to get rid of the old kernel you're running:
```
Kernel release:    3.5.0-42-generic
```

Once you're booted into the Trusty kernel (3.13.x), get the updated ALSA info.

---

### Post by tuner90 on 2014-08-25
Here you have it -> [[COLOR=#008000]_!!Script ran on: Mon Aug 25 13:57:33 UTC 2014_[/COLOR]](http://www.alsa-project.org/db/?f=24f2c4626e6e4e14ffd0c1c366fc2af96d39d237).

---

### Post by tuner90 on 2014-08-25
Now I didn't have any sound. So did [[COLOR=#008000]_this_[/COLOR]](http://askubuntu.com/a/457631/320051) and now have again heavily low sound when jack plugged in.

---

### Post by tuner90 on 2014-08-25
Now I didn't have any sound. So did [[COLOR=#008000]_this_[/COLOR]]("http://askubuntu.com/a/457631/320051") and now have again heavily low sound when jack plugged in. Here's [[COLOR=#000000]!!Script ran on: Mon Aug 25 17:01:24 UTC 2014[/COLOR]](http://www.alsa-project.org/db/?f=2a1e8ddc44bc2f02b366618bc10f705d2ee765f0).

---

### Post by Yellow Pasque on 2014-08-25
If you remove the "options snd_hda_intel model=6stack-dig" from /etc/modprobe.d/alsa-base.conf, does it help?

---

### Post by tuner90 on 2014-08-26
Commented out this line and typed **sudo alsa force-reload.** Now sound was heavily low while jack fully plugged in - again when wanted to listen to music, had to half-unplug it.
But after reboot, there's completely no sound. So again had to reload alsa and sound appears, but with low volume if jack's plugged in.

---

### Post by tuner90 on 2014-08-27
Sorry for that, but Bump!

---

### Post by Yellow Pasque on 2014-08-27
I would look at testing another OS (like FreeBSD or even try another Linux distro) to rule out a physical issue with the jack.

You may also find some useful info here: [http://unix.stackexchange.com/questions/25776/detecting-headphone-connection-disconnection-in-linux](http://unix.stackexchange.com/questions/25776/detecting-headphone-connection-disconnection-in-linux)

---

### Post by tuner90 on 2014-08-28
Ok, thanks. I'll check this.

---

### Post by tuner90 on 2014-08-28
After some manipulations using PulseAudio Volume Control, now I have this sound, also when have jack fully plugged in.
Had to set profile to Analog Stereo Duplex in Configurations tab, and then in Output Device choose Headphones and manipulate the Front Left/Right sliders.
But before upgrade to 14.04 (when using 12.04), everything's was fine.
Don't know why this happened.

---

