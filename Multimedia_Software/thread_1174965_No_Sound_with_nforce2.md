---
title: "No Sound with nforce2"
date: 2009-05-31
forum: Multimedia Software
---

### Post by ZGruk on 2009-05-31
After installing Ubuntu 8.10 I did not have any sound. After following [this]("http://ubuntuforums.org/showthread.php?t=253725") thread I was able to get the sound to work if my sound program was run as root (except for rhythmbox, it never worked). Unfortunately most of the things I listen to are on a server on the Local Area Network and I can't figure out how to access network drives as root. After fiddling around with the settings using suggestions from other threads I completely disabled sound:). I upgraded to 9.04 and reset all the settings hoping it would work. It didn't, I was able to get it to *act* like it works using the sound troubleshooting guide, but I still get nothing except a low static. When I click Test in the Sound Preferences GUI the pitch of the static changes but thats all.
I have an ASUS A7N8X-E motherboard with an NVIDIA nforce2 sound system
The results of aplay -l are:

**** List of PLAYBACK Hardware Devices ****
card 0: nForce2 [NVidia nForce2], device 0: Intel ICH [NVidia nForce2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: nForce2 [NVidia nForce2], device 2: Intel ICH - IEC958 [NVidia nForce2 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Thanks in advance
-Z

---

### Post by ZGruk on 2009-06-07
bump

---

### Post by ZGruk on 2009-07-13
Well its fixed. I'm not sure what i did. I unmuted all the switches and that fixed it.

---

