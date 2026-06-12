---
title: "spdif  / digital audio question"
date: 2008-11-17
forum: Multimedia Software
---

### Post by false_apology on 2008-11-17
Hey All,

I tried posting this in the mythbuntu forums and I didn't garner much attention, so i'll give a try here. My apologies in advance for cross posting.

Anyway, I have a mythtv setup on an older Athlon 64 3000+ machine. I used the mythbuntu all-in-one CD from a few months back. 

For the audio, I wanted to use the SPDIF out output of my soundcard to output to my JVC receiver. This is actually all working fabulously in MythTv - all my recorded and live playback works great, with surround sound. However, I cannot get any audio in other programs. For example, if I wanted to watch flash video in firefox, I get nothing. If I try and play back a video file that mythtv recorded, but using VLC, I get nothing. I know it can work, because it *IS*working in mythfrontend. 

I was trying to read some tutorials but nothing has really given me a good answer. 
Here is my aplay -l

```

**** List of PLAYBACK Hardware Devices ****
card 0: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 4/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

Now, one tutorial said I had to create an /etc/asound.conf, and tell it to route all PCM to the spdif output. So I tried to do this, but it is still not working. Here is what I put in my asound.conf:

```
pcm.!default {
type hw
card 0
device 1
}
```

I tried both device 0 and device 1, neither works. If it helps, in the MythTV setup, under "Audio", my "Audio output device" is "ALSA:spdif" and the passthrough device is set to "Default". Like I said, in mythfrontend, live/recorded shows and DVDs, the spdif digial audio works great. 

The motherboard is an ASUS K8V-SE DLX. 

Can anyone point me the right direction?

Thank you

---

