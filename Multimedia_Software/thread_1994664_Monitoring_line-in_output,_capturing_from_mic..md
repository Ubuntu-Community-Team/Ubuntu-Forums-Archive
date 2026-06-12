---
title: "Monitoring line-in output, capturing from mic."
date: 2012-06-03
forum: Multimedia Software
---

### Post by Nostris on 2012-06-03
Hardware:
Acer Aspire 7520, 
```
/proc/asound/card0/codec#0:Codec: Realtek ALC268 
```
laptop have 3 jacks: line-in, mic-in, output.

Software: fresh install of Ubuntu 12.04, skype

Case:
I use Skype mostly to communicate with other players while playing multiplayer games on PS3. I have connected PS3 sound via line-in to get sound back in my headphones. 
With command:
```
pactl load-module module-loopback
```
I was able to hear the sound coming from line-in on the output jack.
The problem is I can't make Skype to capture mic-input while having line-in sound redirected to the headphones. I can only select one source as a sound input for Skype via PulseAudio Volume Control but then again I am losing line-in monitoring.
Is there any possibility to do both? Or is it simply hardware limited?

---

