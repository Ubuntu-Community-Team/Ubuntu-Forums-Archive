---
title: "newbie - no sound - don't know what to do"
date: 2007-05-06
forum: Multimedia &amp; Video
---

### Post by mkramer on 2007-05-06
Edit:** RESOLVED** using this post [http://ubuntuforums.org/showthread.php?t=434911&highlight=no+sound](http://ubuntuforums.org/showthread.php?t=434911&highlight=no+sound)
---
Ok I got the codec support for my M4A files.   Now I can play them, and Rhythmbox starts to play them.  However, no sound comes out.  The system volume, rhythmbox volume, and speaker volumes are all at an audible level.  I honestly don't even know how to check to see if my sound card is recognized by the system.  I don't know what kind of sound card I have, but it's an older sound blaster.  Where do I go from here?

edit: some system information

```
mason@mason-desktop:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.14rc1 (Tue Jan 09 09:56:17 2007 UTC)
```

```
mason@mason-desktop:~/install_flash_player_9_linux$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Audigy [Audigy 1 [SB0090]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 32/32
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
card 0: Audigy [Audigy 1 [SB0090]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: Audigy [Audigy 1 [SB0090]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: V8233Pre [VIA 8233-Pre], device 0: VIA 8233-Pre [VIA 8233-Pre]
  Subdevices: 4/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 1: V8233Pre [VIA 8233-Pre], device 1: VIA 8233-Pre [VIA 8233-Pre]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

