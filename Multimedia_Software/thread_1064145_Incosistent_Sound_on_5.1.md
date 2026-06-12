---
title: "Incosistent Sound on 5.1"
date: 2009-02-08
forum: Multimedia Software
---

### Post by taronski on 2009-02-08
Good evening,

After much tribulation I got my sound working on my NVIDIA on board CK804.

I couldn't get it to work properly on all speakers (though was a problem with hardware) so I was happy to live with 2 but then I noticed that based on the application some of the previously assumed dead speakers come to life...(ie on tomem I get different speakers that I get from youtube)/

I have Alsa/PulseAudio/OSS Mixer.

Any ideas of what I could do to have all speakers working?

Many thanks

Taron

---

### Post by ZMoney on 2009-02-08
How are you connecting your speakers to your sound card?  I've been working for a few days now on getting SPDIF to work and now it works for dts/ac3 but not for pcm files.

---

### Post by taronski on 2009-02-08
Hiya, using the standard 3 jacks which connect to my pc speaker system

---

### Post by taronski on 2009-02-09
Bump

---

### Post by taronski on 2009-02-14
Update: Sound now is gone altogether from both web/totem/rhytmbox

It seems that Ubuntu recognise both sound cards still no sound via speakers but no problems via analogue on totem 

taron@Beast:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
taron@Beast:~$ 

Any help to get my sound back would be greatly appreciated.

Thanks

Taron

---

