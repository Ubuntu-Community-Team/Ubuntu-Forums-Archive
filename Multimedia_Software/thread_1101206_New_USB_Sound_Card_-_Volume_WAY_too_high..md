---
title: "New USB Sound Card - Volume WAY too high."
date: 2009-03-20
forum: Multimedia Software
---

### Post by guywithcable on 2009-03-20
I've just installed a SIIG SoundWave 7.1, a USB sound card. The box says it has a Built-In Amplifier, but there are no controls on the device. It works well, but the volume is ridiculously high. It's blasting everything. Right now "Master" is at 10% and "PCM" is at 9%. It sounds like when my old card was at 90%. The only channel that shows up in the Gnome volume control is PCM, and I used
```
amixer set Master 10%
```to set the Master channel. It seems that either one can be set, but they each cancel the other out when you set them. As in, if I set PCM to 10% while Master is 100%, then set Master to 50%, the volume goes up (to 50% I assume).

My speakers have there own amplifier and a subwoofer.

Is there any way to lower the volume (maybe at the hardware level)?

---

### Post by mastermindg on 2009-03-20
There should be multiple sliders to adjust in Volume Control. I've got Master,PCM,Front,Surround,Clear,and LFE. I would try adjusting the other sliders under Volume Control.

---

### Post by guywithcable on 2009-03-20
Haha, there was a switch called "Loudness" that was hidden until I went to preferences under the Volume Control. Wow.

Anyway, I have a new problem now. The PCM channel isn't very good for volume control. It makes my left speaker go out at low volumes. Is there any way to have the volume slider control the Master channel, even though it's not shown in Volume Control?

---

### Post by guywithcable on 2009-03-20
> **guywithcable said:**
> Anyway, I have a new problem now. The PCM channel isn't very good for volume control. It makes my left speaker go out at low volumes. Is there any way to have the volume slider control the Master channel, even though it's not shown in Volume Control?

Never mind. Found it under another device. :)

It's still really loud though. Any other suggestions?

---

### Post by guywithcable on 2009-03-20
> **mastermindg said:**
> There should be multiple sliders to adjust in Volume Control. I've got Master,PCM,Front,Surround,Clear,and LFE. I would try adjusting the other sliders under Volume Control.

There's just PCM under this device.

---

