---
title: "No sound over HDMI - Gigabyte Mobo HD2000/3000 Realtek ALC887"
date: 2014-12-14
forum: Multimedia Software
---

### Post by Stuart_Bridger on 2014-12-14
I've been trying everything to get this working - hoping someone can point me in the right direction.

Video is working fine over HDMI but I'm getting no audio output. It seems every other similar post I've seen there is a digital device showing in aplay but I'm only seeing an analogue device...

```
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ID 887 Analog [ID 887 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

This is a fresh install of Ubuntu 14.04.

---

### Post by Yellow Pasque on 2014-12-14
What GPU are you trying to use for the HDMI audio? Can you give output of lspci:
```
sudo update-pciids
lspci
```

Also, more audio info: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by Stuart_Bridger on 2014-12-15
Turns out I was being a complete muppet!

Output from my mobo is DVI and I'd just assumed that by using a DVI-HDMI cable the sound would be included.

Wow - I spent a lot of time trying to get that working! Cheap GT210 sound card on it's way from Amazon.

---

### Post by Yellow Pasque on 2014-12-15
Please mark thread solved.

---

### Post by MartyBuntu on 2014-12-15
> **Stuart_Bridger said:**
> Cheap GT210 sound card on it's way from Amazon.

If you're referring to the NVIDIA GT 210, I hope you realise...*it's not a sound card.*

---

### Post by Yellow Pasque on 2014-12-15
> **MartyBuntu said:**
> If you're referring to the NVIDIA GT 210, I hope you realise...*it's not a sound card.*

Actually, it should have a sound codec that works through HDMI....

---

