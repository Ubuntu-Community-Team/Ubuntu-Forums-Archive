---
title: "Sound was working now it isn't"
date: 2009-11-17
forum: Multimedia Software
---

### Post by Dave.Bee on 2009-11-17
I installed Karmic as a dual boot setup with Windows XP a couple of weeks ago. Everything worked perfectly from the start... I could play music, watch video with audio, no problem.
Today however, I have no sound. If I start any application that prompts a sound, I get a loud bass click from my speakers (like a loud electrical thud sound), but nothing else. I haven't changed anything... it was working when I got home from work, then it wasn't.

I've been searching here for a couple of hours, but nothing has helped.

```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC880 Analog [ALC880 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
```

```
lspci |grep Audio
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
```

If I type speaker-test, I get the same loud electrical thud from the speakers. No other sound.

Sound is fine if I boot into Windows XP.

Help! I was all set to convert to Karmic entirely until this!

---

### Post by hellmet on 2009-11-18
Did you try restarting pulseaudio (or alsa if you don't use PA)
"sudo /etc/init.d/pulseaudio restart"

---

### Post by Dave.Bee on 2009-11-18
Thanks for your reply. Strangely, no amount of restarting the machine last night would fix it, but it is working again this morning.
Weird.

---

