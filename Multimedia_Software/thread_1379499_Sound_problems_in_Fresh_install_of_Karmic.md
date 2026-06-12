---
title: "Sound problems in Fresh install of Karmic"
date: 2010-01-12
forum: Multimedia Software
---

### Post by sreejith_sasi on 2010-01-12
I have been running jaunty with latest pulseaudio, alsa and nvidia drivers. With this setup, audio was working great including hdmi output. I have a HP DV5t 64-bit laptop with nvidia card.

I cleaned out my hard disk and did a fresh install of karmic koala. After that I upgraded pulseaudio, alsa and nvidia to the latest versions as before. However, i have wierd issues with sound now.

1. No sound in Rhythmbox. However when I connect my hdmi cable to TV, I hear sound through TV. Nothing through my laptop speaker.

2. Play anything in totem, I hear sound through my laptop speakers. When I connect HDMI, I cannot get it to goto my TV.

3. When I use sound recorder, I see the meter moving. Which  probably means its recording. However, when I play the recorded sound, I hear nothing. Now I am not sure if its because the mic's not working or the sound.


 aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 0/1
  Subdevice #0: subdevice #0


Added the following to /etc/modprobe.d/alsa-base.conf:
options snd-hda-intel model=hp-dv5 enable=1 index=0
options snd-hda-intel enable_msi=1

I have increased all volume bars in alsamixer. I don't understand the new Profiles in sound preference. But i'm guessing if I select HDMI output profile, the sound should get directed to hdmi output etc... is that correct.

If anyone has similar issues, please help me out.

---

