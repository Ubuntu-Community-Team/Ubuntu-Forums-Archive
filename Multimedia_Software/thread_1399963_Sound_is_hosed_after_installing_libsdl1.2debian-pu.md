---
title: "Sound is hosed after installing libsdl1.2debian-pulseaudio"
date: 2010-02-06
forum: Multimedia Software
---

### Post by bburtin on 2010-02-06
I was having CPU usage problems in GMAMEUI on my Dell laptop running Karmic.  I found a thread that suggested I install libsdl1.2debian-pulseaudio to get around them.  So I did this:

```
sudo apt-get install libsdl1.2debian-pulseaudio
```

After installing PulseAudio, my CPU problems went away... and so did my sound.  Now sound doesn't work at all.  When I go to System / Preferences / Sound, I get a dialog that says "Waiting for sound system to respond".  My volume control is no longer in the taskbar.  I get no audio out when playing MP3's.

I tried the following to try to recover ALSA:

```
sudo apt-get install gstreamer0.10-alsa gnome-alsamixer
sudo apt-get purge pulseaudio gstreamer0.10-pulseaudio vlc-plugin-pulse
```

and

```
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
sudo apt-get install linux-sound-base alsa-base alsa-utils
```

but still get the same symptom.  Does anyone have a suggestion about the best way to restore my audio?  Here's the output of aplay -l, in case it's useful:

```
[~]$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

Thanks in advance,

Boris

---

### Post by bburtin on 2010-02-06
Interesting update.  Turns out that I hear audio when playing a YouTube video from Firefox.  Still no audio when playing an MP3 in Movie Player.  Maybe they're using different drivers?

---

### Post by bburtin on 2010-02-06
Aha, I missed a crucial step in the [Comprehensive Sound Problem Solutions Guide]("http://ubuntuforums.org/showthread.php?t=205449").  I ran

```
sudo apt-get install gdm ubuntu-desktop
```

and now audio is working as before.  Nothing like answering my own question in a public forum.  :-)

---

### Post by Roamer145 on 2010-04-05
Well, it seems I flubbed up and did the same thing to my box. :/ Similar issue, so I'm trying this to fix mine. ](*,)

---

### Post by Roamer145 on 2010-04-05
Sweet deliciousness, it worked! Thanks! You saved me from spending 20 hours without my music collection! I was not looking forward to a reinstall of the main OS only to get it working again. My issue was that after I had tried to install libsdl1.2debian-pulseaudio, I also edited a couple lines in the asound.conf and the default.pa. I'm thinking I may have messed up something in that, but either way, it works thanks to you! :D

---

### Post by bburtin on 2010-04-05
Great!  Glad to hear that my public rambling ended up serving a purpose.  :-)

---

### Post by Roamer145 on 2010-04-05
> **bburtin said:**
> Great!  Glad to hear that my public rambling ended up serving a purpose.  :-)

All rambling serves a purpose if it comes to a solution. :P Thanks again!

---

