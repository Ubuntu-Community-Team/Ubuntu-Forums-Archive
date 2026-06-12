---
title: "HH upgrade fixed sound, HH clean install broke it again."
date: 2008-05-01
forum: Multimedia Software
---

### Post by pixelate on 2008-05-01
I've had Ubuntu installed on my system for several months now, first Fawn, then upgraded to Gibbon when it went to LTS.  All along I have been unable to get audio.  My card seems to be recognized just fine (it's an Audigy ex Platinum), shell command **aplay -l** returns the following:

[FONT="Courier New"]**** List of PLAYBACK Hardware Devices ****
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
[/FONT]

I have also checked that my user account is in the audio group, as per the Comprehensive Guide's instructions.

The weird thing is, when I open **alsamixer**, I get all the expected sliders, except the majority don't have any box where the "MM" (mute) indicator should be at all.

OK, weirder thing-- after months of being resigned to no sound, I *upgraded* to Hardy a couple of days ago and suddenly sound was working upon the first restart.

I decided to do a clean install shortly afterwards as some unrelated issues were popping up, and unfortunately the sound is again gone and all of my troubleshooting steps return the same results as described above.

Any suggestions would be greatly appreciated.

---

### Post by pixelate on 2008-05-01
Saw a request in [another post]("http://ubuntuforums.org/showpost.php?p=4848327&postcount=4") that first said to get soundcard info using "**lspci | grep Audio**".  This command returns absolutely nothing for me in the terminal.  Not sure if that helps or means anything.

[Compiling ALSA on my machine]("http://ubuntuforums.org/showpost.php?p=4810371&postcount=6") also did not help.

---

