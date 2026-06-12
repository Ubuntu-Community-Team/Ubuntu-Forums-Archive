---
title: "Problems with Pulse seeing Audigy over top of USB Mic"
date: 2010-06-04
forum: Multimedia Software
---

### Post by GaryUK on 2010-06-04
Hi,

I seem to have a problem in that when my USB logitech microphone is attached to my PC, Pulse cannot seem to see my Creative Audigy 2 card. I grant you that I could remove the Mic but the fact is, I should not have to and would rather not as I use it for Skype on Windows. My machine is a Dell 8400 with dual boot XP/Lucid and it would be an absolute pain to have to continually remove the Mic just for Ubuntu.

Here's the usual details that seem to be requested:

```
garyd@Home:~$ uname -a
Linux Home 2.6.32-22-generic #35-Ubuntu SMP Tue Jun 1 14:17:36 UTC 2010 i686 GNU/Linux
garyd@Home:~$ cat /proc/asound/modules
 0 snd_emu10k1
 1 snd_usb_audio
garyd@Home:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on Jun  4 2010 for kernel 2.6.32-22-generic (SMP).
garyd@Home:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Audigy2 [SB Audigy 2 [SB0350b]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 31/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 0: Audigy2 [SB Audigy 2 [SB0350b]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: Audigy2 [SB Audigy 2 [SB0350b]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Audigy2 [SB Audigy 2 [SB0350b]], device 4: p16v [p16v]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
garyd@Home:~$ head -n 1 /proc/asound/card*/codec#*
head: cannot open `/proc/asound/card*/codec#*' for reading: No such file or directory

```

And here is the link to the ALSA info script that I have run:

```
http://www.alsa-project.org/db/?f=cb5211f117ab3ebb607df216a6db202443a36620
```

What I get is no sound in anything except amarok (and then it is very choppy and distorted). However, if I hot-plug a USB plantronics headset, I can hear the music through the headset and it also has an active Mic. In addition, the plantronics equipment shows up in the Pulse playback alongside the Logitech mic (and takes precedence).

I cannot help but think that I need some way to prevent Pulse loading the Mic and that taking precedence over the Audigy card (which, by the way, is not selectable as it does not show in the Pulse volume app).

Anyone got any bright ideas??

Thanks in Advance for your help!!

---

