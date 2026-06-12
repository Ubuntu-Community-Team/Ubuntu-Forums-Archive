---
title: "sound stopped working"
date: 2008-05-06
forum: Multimedia Software
---

### Post by gammyhand on 2008-05-06
My sound was working fine until I turned off my PC last night. I turn it on tonight and no sound anywhere. Can't see anything on mute. Is this common? Thought I would ask before I re-install.

---

### Post by gammyhand on 2008-05-18
Seriously...no-one have any ideas?

My sound worked yesterday when I turned the PC on and then again not today. I know the drivers are initialising because the speakers make a hiss when they load during boot.

---

### Post by DaVince21 on 2008-05-18
You should at least give us some details, like what sound card you're using.

To get a list of all the sound hardware on your PC, type this in a console:
```
aplay -l
```

Don't forget to Google your sound card + the word Ubuntu to find if this problem is common, too.

---

### Post by gammyhand on 2008-05-18
Thanks for replying. The aplay details are below. It is odd because this problem has never arisen before now and I have been using Ubuntu for quite a while.

card 0: nForce3 [NVidia nForce3], device 0: Intel ICH [NVidia nForce3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: nForce3 [NVidia nForce3], device 2: Intel ICH - IEC958 [NVidia nForce3 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Audigy2 [Audigy 2 ZS [SB0350]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
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
card 1: Audigy2 [Audigy 2 ZS [SB0350]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 1: Audigy2 [Audigy 2 ZS [SB0350]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Audigy2 [Audigy 2 ZS [SB0350]], device 4: p16v [p16v]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by DaVince21 on 2008-05-21
I could find this when Googling your sound card + "no sound Ubuntu":
[http://ubuntuforums.org/showthread.php?t=648829](http://ubuntuforums.org/showthread.php?t=648829)

I guess you'd better follow the FAQ it refers to, then. ;)
[http://ubuntuforums.org/showthread.php?p=4874981](http://ubuntuforums.org/showthread.php?p=4874981)

---

### Post by aeiah on 2008-05-21
are you sure ubuntu hasnt defaulted to one of your other soundcards? you seem to have an audigy and an onboard soundcard

---

### Post by DaVince21 on 2008-05-23
Ah, that's right. Try using the asoundconf tool to list the cards found (asoundconf list) and set it using asoundconf set-default-card <NAME FROM LIST>. Then restart ALSA or the PC and see if sound works (also check the audio control panel after doing this).

---

