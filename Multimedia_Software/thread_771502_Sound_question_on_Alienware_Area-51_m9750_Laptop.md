---
title: "Sound question on Alienware Area-51 m9750 Laptop"
date: 2008-04-27
forum: Multimedia Software
---

### Post by Davers! on 2008-04-27
So I installed Hardy on my Alienware Area-51 m9750, and everything is great so far (I've used Ubuntu a lot in the past), and surprisingly the video driver works like a charm.

Problem is, I can't get sound to work.

The sound mixer shows five devices:

0: HDA Intel (Alsa mixer)
1: Realtek ALC885 (OSS Mixer)
2: Playback: ALSA PCM on front:0 (ALC882 Analog) via DMA (PulseAudio Mixer)

And then 2 Capture devices.

Problem is, none of them seem to make sound come from my laptop speakers. The laptop volume knob works for changing the volume of whichever device is selected, but they all seem muted.

One of the devices is optical digital out ONLY, and should NOT play sound over the speakers, but one obviously should.

Any ideas?

Edit: Forgot to mention I'm running x64

Edit: Also, if I go to System -> Preferences -> Sound and "Test" each of the sound playback devices at 75% volume, I hear nothing from any of them.

---

### Post by PunkiBastardo on 2008-05-30
Hi,

the guide [here]("http://ubuntuforums.org/showthread.php?t=616845")solved this problem for me, but if you don't want to go through all that reading here's what you have to do in 3 easy steps to fix the sound problem on the Alienware Area-51 m9750 in Ubuntu :

1. Open up the Terminal and type:
**sudo gedit /etc/modprobe.d/alsa-base**

2. Then go to the bottom of the document and add this line:
**options snd-hda-intel model=arima**

3. Save and reboot.

After that everything should work great, in any case check the sound settings, just in case you have something muted.

---

