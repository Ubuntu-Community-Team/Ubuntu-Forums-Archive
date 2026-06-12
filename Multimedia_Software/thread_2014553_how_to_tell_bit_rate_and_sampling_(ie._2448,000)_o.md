---
title: "how to tell bit rate and sampling (ie. 24/48,000) on ALSA or Jack"
date: 2012-07-02
forum: Multimedia Software
---

### Post by lorriman on 2012-07-02
Folks, I have a new USB card, the [ODAC]("http://nwavguy.blogspot.co.uk/2012/04/odac-released.html"), and one of its virtues is running at 24bit.

On Windows Vista, however, it defaulted to 16/44. At least I could manually change that. Under Ubuntu 10.04 I can't find any way of either telling what it is running at or changing it for either ASLA or Jack.

Any clues?

---

### Post by lorriman on 2012-07-03
The nearest I've come to a solution is speaker-test. But really it isn't telling me what alsa is doing with my audio, only what it could do. Even so I have a problem since speaker-test doesn't work with hw1,0 the USB card. Neither:

speaker-test -c 2 -r 44000 -F S32_LE -D hw:1,0

or  even

speaker-test -c 2 -r 44000 -F S16_LE -D hw:1,0

gets me :

```

speaker-test 1.0.24.2

Playback device is hw:1,0
Stream parameters are 44000Hz, S16_LE, 2 channels
Using 16 octaves of pink noise
Rate 44000Hz not available for playback: Invalid argument
Setting of hwparams failed: Invalid argument

```

play -l gets me :

```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: DAC [UAC1 DAC], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

speaker-test on hw0,0 works fine: I can hear the pinknoise.

In any case, speaker-test isn;t the answer to my problem even if it did work.

---

### Post by habib0016 on 2012-07-03
Thanks for your information.

---

