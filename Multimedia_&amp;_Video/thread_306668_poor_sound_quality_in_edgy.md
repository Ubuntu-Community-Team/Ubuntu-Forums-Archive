---
title: "poor sound quality in edgy"
date: 2006-11-25
forum: Multimedia &amp; Video
---

### Post by agentx on 2006-11-25
How can I improve the sound quality for a nfoce4 motherboard. The sound card is onboard and it's a Realtek AC'97. It's being recognized by edgy but the quality is poor, especially when I raise the volume. 
Also how come aplay reports 2 cards when there should be only one? This is what is being displayed when I type aplay -l.

**** List of PLAYBACK Hardware Devices ****
card 0: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by Dr. Nick on 2006-11-25
I think I have the same realtek ac '97 and yes the sound does get distorted when you max out the volume in software or the OS.

What I have done is lower the volume to 70ish percent in all my apps and just turn the speakers up some to offset it.

---

### Post by patslap on 2006-12-18
> **Dr. Nick said:**
> I think I have the same realtek ac '97 and yes the sound does get distorted when you max out the volume in software or the OS.

What I have done is lower the volume to 70ish percent in all my apps and just turn the speakers up some to offset it.

I had the same problem in Kubuntu. I was playing around with KMix levels and have been getting sound distortion (sound like both the bass and treble drivers on speakers have blown) no matter how low I turned the volume. 

I kept the master volume at 100% but reduced the PCM volume to around 75% and this has resolved the problem - clean sound again.

Seems that raising PCM levels too high creates sound distortion.

---

### Post by randytuggle on 2006-12-22
What I found worked the best for me was to set the PCM at about 60% or so - and then eliminate the PCM volume control from the volum controls by using the edit section of the volume controls. That keeps the PCM from floating up and down (high and low) during the use of many sound apps.

---

### Post by skyrice on 2007-05-10
Hey guys. I'm running Debian 4.0 with the same NVidia chipset and had the same distorted sound problem. Thanks for the fix though, setting the PCM lower in the mixer made the sound normal again. Also, the second 'card' that the person above is seeing is the SPDIF optical output I believe. It's not another card, but another 'device' on the card.

---

