---
title: "Eee Pc 900 No Sound At all"
date: 2009-05-02
forum: Multimedia Software
---

### Post by Richard9795 on 2009-05-02
I installed Ubuntu 8.04.2 LTS on my Eee pc. There are a lot of things that needed fixing, and i did (niceeepc script). Everything is working... until i listened to some music through my earphones. after a reboot, it stopped working (sound output through BOTH my earphones and the speakers). I can't tell if sound capture works because i can't hear a thing. Ubuntu Still Detects the sound card:

richard@richard-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC662 Analog [ALC662 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

... but still no sound. is there anyone out there that can assist me in this Problem? thanks (save me from going back to WINDOWS)

---

### Post by HappyFeet on 2009-05-02
Ubuntu 8.04 might not be the best version to use on a netbook. I suggest the latest (9.04). It has much better netbook support.

---

### Post by blackened on 2009-05-02
> **HappyFeet said:**
> Ubuntu 8.04 might not be the best version to use on a netbook. I suggest the latest (9.04). It has much better netbook support.

If you really want to use 8.04, then I would suggest checking out Easy Peasy ([http://www.geteasypeasy.com/]("http://www.geteasypeasy.com/")) or EEEbuntu ([http://www.eeebuntu.org/]("http://www.eeebuntu.org/")). Both have versions of 8.04 or 8.10 that have been tailored to work with many netbook models.

The standard install of 9.04 has most of the hardware drivers built into the kernel, so it should work out of the box.

---

### Post by Richard9795 on 2009-05-02
Huh, I fixed it... Just shut it down, Remove the AC, then Battery, then Put everything back. Maybe some config in thee Eee that temporarily broke sound.

---

### Post by Richard9795 on 2009-05-02
9.04 Has Known to Have Graphics Reggressions With Intel Chipsets. I tried any of the Workarounds (UXA, The Greedy option of the EXA acceleration, etc) if anyone has a solution to those problems, please tell me. Thanks!

---

