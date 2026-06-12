---
title: "Karmic - since upgrade, admin user has sound, other doesn't"
date: 2009-11-24
forum: Multimedia Software
---

### Post by plink on 2009-11-24
Just upgraded to 9.10 from 9.04, where sound was OK.  Sound is fine for my account, which is default account for sudo functions.  Other account (dotty) is getting no sound. For that account System...Pref..Sound...Hardware... shows no device.  For my account, device shows up.

Below is output for aplay using dotty id:
dotty@pete-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CK8 [NVidia CK8], device 0: Intel ICH [NVidia CK8]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: CK8 [NVidia CK8], device 2: Intel ICH - IEC958 [NVidia CK8 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

User dotty is in /etc/group for audio.

Any ideas?

--pete

---

### Post by mack75 on 2009-11-24
Hi:

The easy way, move your .gnome2 and .gnome2_private .gconf and .gconfd directories and log in again.

Obviously you will lose last gnome configurations.

---

