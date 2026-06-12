---
title: "Can't stop Microphone playback through Speakers"
date: 2008-09-11
forum: Multimedia Software
---

### Post by im_dan on 2008-09-11
Hi I am having real problems setting up my microphone properly, I guess I am one of the lucky ones because I have working speakers and mic. The problem is I can't disable the input from the microphone playing back through my speakers. I have tried muting every output in the volume control individually but I either disable all sound or keep getting mic playback
I have attached an image with my current volume control settings, and I know some are muted, but I muted all the ones that don't affect playback.
I tried muting capture and cature 1 in the recording tab because this seemed like the most obvoius solution but it made no diffrence, still mic playback.
My machine has an onboard snd_hda_intel soundcard
```
cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC883
```
And a ATI Video card that shows up as a sound device as well
```
cat /proc/asound/card1/codec#* | grep Codec
Codec: Generic 1002 ATI R6xx HDMI
```




I have no idea how to fix this, I have tried every guide and trobleshooting tip I have found on the these fourms and whatever else google turned up, here are some details other posts had provided, I hope they can be of use.

When I go to File -> Change Device in the Volume control there are 6 devices listed they are as follows:
HDA NVidia (ALSA mixer)
HDA ATI HDMI (ALSA mixer)
Realtek ALC883 (OSS Mixer)
Playback: ALSA PCM on front:0 (ALC883 Analog) via DMA (PulseAudio Mixer)
Capture: Monitor Source of ALSA PCM on front:0 (ALC883 Analog) via DMA (PulseAudio Mixer)
Capture: ALSA PCM on front:0 (ALC883 Analog) via DMA (PulseAudio Mixer)

```
cat /proc/asound/modules
0 snd_hda_intel
1 snd_hda_intel
```

```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

---

### Post by im_dan on 2008-09-16
*bump
Please help I'm really desperate

---

### Post by markbuntu on 2008-09-17
Have you tried this thread? it has a lot of info about HDA sound chips including the ALC883

[http://ubuntuforums.org/showthread.php?t=806620](http://ubuntuforums.org/showthread.php?t=806620)

---

### Post by im_dan on 2008-09-19
I tried some of the things mentioned in that thread but still no luck. My problem is a little different to that though because I can switch between headphone and speaker output without a problem

---

### Post by im_dan on 2008-09-20
For anyone that stumbles upon this thread, I am sorry to say I didn't find a solution. I ended up buying a cheap 4 channel $20 sound card and disabled the onboard soundcard, maybe when Intrepid comes out I'll give it another shot.

---

### Post by eye208 on 2008-09-20
> **im_dan said:**
> I have attached an image with my current volume control settings, and I know some are muted, but I muted all the ones that don't affect playback.
I tried muting capture and cature 1 in the recording tab because this seemed like the most obvoius solution but it made no diffrence, still mic playback.
I looked at your attached image. It shows the "Front Mic" slider on the playback tab all the way up to max and not muted.

---

### Post by ilove2boogie on 2010-03-26
Hola,

I had this problem - although for me it only started when I was playing with the mic settings to try to get the sound to work with Skype (still working on that...)

I played with all the combinations and found one that fixed it though - if you click the mic icon and select 'volume control', then under the device menu select 'HDA Intel ASLA Mixer', various sliders show up. I found that if I leave the one called microphone on, but mute the one called 'ATAPI mic', the playback stops:-)

I guess that might just work for my specific setup, but it might help!

---

