---
title: "Static background in microphone"
date: 2013-01-11
forum: Multimedia Software
---

### Post by dannyboy79 on 2013-01-11
I have a VT82xx [HDA VIA VT82xx], device 0: ALC888 Analog [ALC888 Analog] and I am trying to record a commentary on my Turtle Beach X31's headset/microphone using Audacity (using a 3/32 to 1/8" adapter) but there is this static background noise when I record. Anyone know how to get rid of the static? I am using Xubuntu 12.04 which uses pulseaudio.

Any help would be appreciated.

---

### Post by FakeOutdoorsman on 2013-01-11
I know nothing of pulseaudio, but perhaps the gain is too high or the "mic boost" is set too high.

If it is room noise get a sound/noise profile. Record at least 10 seconds of just room noise. Then use this with "Effect -> Noise Removal" in Audacity to remove a good amount of the noise. It will affect the non-noise sound, but may not be noticeable or the trade-off may be worth it.

---

### Post by dannyboy79 on 2013-01-11
thanks for the suggestion, i have checked the mic boost, it's already set at 22, which is like 1/4 the way. As far as the noise removal, I could try that unforunately the only time the static occurs when I speak, if i just leave the mic recording and not talk, no static/noise is recorded. it seems to only have static when I speak. and no it's not because my mouth is too close to the mic, i haev thought of that. Its very weird, i may just have to pic up a cheap usb microphone or try a pci sound card.

---

### Post by Nevetsjc on 2013-01-12
Could it be the mic? Maybe borrow one and see if you get the same static

---

### Post by dannyboy79 on 2013-01-12
it's not the mic because I use it for gaming and everyone in my chat says my voice is clear. I don't know what it is but for now I am using the mic on the logitech c260 webcam I purchased and the commentaries are crystal clear.

---

