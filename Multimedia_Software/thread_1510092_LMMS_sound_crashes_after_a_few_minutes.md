---
title: "LMMS sound crashes after a few minutes"
date: 2010-06-15
forum: Multimedia Software
---

### Post by Sandertje on 2010-06-15
Hi

I'm having a problem with LMMS. Unlike some posts in the forum, my LMMS does output sound, but after a few minutes it crashes. The program itself will just happily go on, but any sound crashes. I hear a glitch, en thereafter no more sound. The only way to fix it is restarting LMMS, which is quite a pain in the *** if you have to do that every 5 minutes :P. The problem occurs to me every time I use LMMS, so it is consistent. It seems to me that it crashes faster when I have a bar that includes somekind of chord; a single tone it can handle, but when there's bi- tri- or multiple tones, it just crashes nearly instantly. I've tried both Alsa and PulseAudio, and both have the same problems. And it's not my overall sound that's crashing: Rhytmbox and Youtube will just continue to play sound ;-).

---

### Post by cchhrriiss121212 on 2010-06-15
Sounds like you are doing too much audio processing for your sound card. You can try increasing the buffer size/latency in preferences or try using a real time kernel which is modified for low latency audio.

---

### Post by Sandertje on 2010-06-15
Buffer size was indeed set to almost nothing (192 frames). I've set it to about a quarter of the slider (3584 frames). I hope that helps. Do you think that's adequate enough for my sound card??:

```
 sander@sander-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by cchhrriiss121212 on 2010-06-15
It depends how much things you are doing at once with audio, but as I said an rt kernel will make a difference. With that you could expect around a 10ms latency for simple projects even with on board audio.

---

