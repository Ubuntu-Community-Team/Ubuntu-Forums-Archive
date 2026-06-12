---
title: "Asus Xonar ST, switch resampling rate?"
date: 2010-08-02
forum: Multimedia Software
---

### Post by monkman on 2010-08-02
ubuntu i386
2.6.34-020634-generic

```
cat /proc/asound/card1/pcm0p/sub0/hw_params 
access: MMAP_INTERLEAVED
format: S16_LE
subformat: STD
channels: 2
rate: 44100 (44100/1)
period_size: 44096
buffer_size: 88200

```

when i read this correctly, my card is set to a sample rate of 44100khz, right?
it's very nice to see most "windowsdriverfeatures" came to linux like: 

headphone impedance

i only miss having control over the sampling rate, is it possible? or does alsa always resample to 48khz, no matter what soundcard is installed?

thx!

---

### Post by monkman on 2010-08-03
bump

---

### Post by monkman on 2010-08-07
Can anyone confirm, that this output means there is no resampling to 48khz while playing 44,1khz files?

thx

---

### Post by PureW on 2010-08-26
I wonder this too. I have an Asus Xonar DX (similar?) and I have the same output. Pulseaudio also crashes when I try to set another frequency...

---

