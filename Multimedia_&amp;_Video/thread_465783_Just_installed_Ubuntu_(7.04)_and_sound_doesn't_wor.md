---
title: "Just installed Ubuntu (7.04) and sound doesn't work. it says Audigy 1 [unknown] Help!"
date: 2007-06-06
forum: Multimedia &amp; Video
---

### Post by iyangpai on 2007-06-06
ive searched but haven't found a solution

the comprehensive sound problem guide didn't help..

and the section about getting sound to work in GNOME in the ubuntuguide.org guide didn't work either.. 

it says this when I input aplay -l into terminal:

**** List of PLAYBACK Hardware Devices ****
card 0: Audigy [Audigy 1 [Unknown]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
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
card 0: Audigy [Audigy 1 [Unknown]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: Audigy [Audigy 1 [Unknown]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


can anyone help me?

---

### Post by _simon_ on 2007-06-06
You don't say exactly which card you have.

My Audigy 2 ZS is also detected as Audigy 1 unknown.

If you have the same card then all you will need to do is open Terminal.

Type:

```

alsamixer

```

Scroll all the way to the right using the arrow keys, stop on Audigy A and press the M key to turn it on.

Now all you need to do is make sure the volumes are set - MASTER, PCM, (I have surround so I also have-) FRONT, SURROUND, CENTER and LFE.

LFE is your sub if you have one.

---

### Post by iyangpai on 2007-06-06
thx for the reply

tried it bfr, and tried it just now.. still doesnt work.. any other suggestions?


edit- oh, and I also don't know exactly which card I have.. it does seem to have the surround options tho, should I hook it up to a surround system?

---

### Post by _simon_ on 2007-06-06
Any old speakers should do, have you tried raising all the volumes in alsmixer, even the ones you don't think you would need?

---

### Post by iyangpai on 2007-06-10
yes, and it still doesnt work TT_TT.

---

