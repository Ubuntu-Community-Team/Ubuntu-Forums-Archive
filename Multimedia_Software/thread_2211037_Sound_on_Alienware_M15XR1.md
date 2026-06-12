---
title: "Sound on Alienware M15XR1"
date: 2014-03-13
forum: Multimedia Software
---

### Post by boomshiki on 2014-03-13
I freshly installed Mint 15 today and I cannot get the sound to work at all. I am running on an Alienware M15X R1 laptop

I entered the follwing into terminal.

```
head -n 1 /proc/asound/card*/codec#*
```
and my result was:
```
Codec: Realtek ALC889A
```

```
cat /proc/asound/version 
```
and my result was:
```
Advanced Linux Sound Architecture Driver Version k3.8.0-35-generic.
```

```
aplay -l
```
and my result was:
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC889A Analog [ALC889A Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC889A Digital [ALC889A Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

I searched and found that a bunch of people had this problem and entered a ine into themodprobe.d/alsa-base.conf. I tried several variations and this did not make any difference, so I reverted to an untouched version.

I found a bunch of people with my model of laptop had this problem but found solutions elsewhere and neglected to post them. 

I cannot make sense of what could be wrong

I just found that my headphone jack works when i put in headphones

---

### Post by Yellow Pasque on 2014-03-14
Try a newer distro/kernel to make sure it hasn't been fixed already. I'd suggest grabbing an Ubuntu 14.04 .iso (flavor of your choice) for testing

BTW, Mint and other OS questions belong here: [http://ubuntuforums.org/forumdisplay.php?f=401](http://ubuntuforums.org/forumdisplay.php?f=401)

---

