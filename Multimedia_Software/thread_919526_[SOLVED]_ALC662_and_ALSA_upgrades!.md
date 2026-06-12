---
title: "[SOLVED] ALC662 and ALSA upgrades!"
date: 2008-09-14
forum: Multimedia Software
---

### Post by life_s_good on 2008-09-14
I'm moving this thread from the laptops and hardware forum because it is entirely focused on the sound card at this point. Old thread was: [http://ubuntuforums.org/showthread.php?p=5776764](http://ubuntuforums.org/showthread.php?p=5776764)

I'd really like some help from anyone at this point as all I have had so far is comments about how others have this issue.

To sum it up I am running ubuntu 8.04 on an Asus F8va-b1 laptop. My sound card is an Intel HDA one with the ALC662 codec.

```
eric@ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC662 Analog [ALC662 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC662 Digital [ALC662 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

I get no sound from alsa. 

I upgraded alsa-drivers to 1.0.18rc3 but I get this error message:

```
[ 40.934391] hda_codec: Unknown model for ALC662, trying auto-probe from BIOS...
```

when I try to use any of the new drivers that were not in the default selection. How can I make it work? Do I need to remove the ubuntu packages for alsa? What else can I change and test? What can I give to show more debugging information? Thank you in advance.

---

### Post by life_s_good on 2008-09-14
Use OSS4 for now.

---

### Post by markbuntu on 2008-09-14
You can try this here, it lists your ALC 662:


[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

---

