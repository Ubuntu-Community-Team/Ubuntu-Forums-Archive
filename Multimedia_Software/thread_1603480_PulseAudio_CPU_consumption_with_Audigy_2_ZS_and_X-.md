---
title: "PulseAudio CPU consumption with Audigy 2 ZS and X-Fi Xtreme Audio"
date: 2010-10-22
forum: Multimedia Software
---

### Post by Mrafcho001 on 2010-10-22
My problem is quite simple to explain really. Whenever I play an audio file (or video for that matter) PulseAudio uses between 20 and 50% of my CPU (Dual core AMD so like 40% to 100% of one core).  This problem does not exist on my laptop or my friends laptop. It only seems to affect my desktop.

First I had a X-Fi Xtreme Audio sound card and thought it was doing the sound processing on software since it is not a true X-Fi card, so I tried my old Audigy 2 ZS, but I still have the same problem.

I have a 7.1 surround sound speaker system and my sound settings are set to 7.1 in the sound preferences. I have noticed that the CPU usage drops a little bit if I change it to 2 channel, but it is still relatively high 10% to 30%.

I was wondering if there is any chance of getting this under control at all?

---

### Post by tommcd on 2010-10-22
> **Mrafcho001 said:**
> 
I was wondering if there is any chance of getting this under control at all?
Pulseaudio is a huge resource hog. You are not the only one complaining about this. There are a great many references to this all over this forum.

You can live without pusleaudio. I do. To get rid of pulseaudio:
```
sudo apt-get remove --purge pulseaudio gstreamer0.10-pulseaudio
```
Then run ```
gstreamer-properties
``` and set everything to alsa. If you ever want pulseaudio back just reinstall pulseaudio and gstreamer0.10-pulseaudio.
As an alternative to removing pulseaudio, here is an article that shows you how to turn pulseaudio on and off at will:
[http://www.linuxplanet.com/linuxplanet/tutorials/7130/1/](http://www.linuxplanet.com/linuxplanet/tutorials/7130/1/)

---

