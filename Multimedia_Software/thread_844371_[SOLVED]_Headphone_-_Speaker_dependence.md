---
title: "[SOLVED] Headphone - Speaker dependence"
date: 2008-06-29
forum: Multimedia Software
---

### Post by pixnaps on 2008-06-29
Hi, my headphones only work when the external speakers are ALSO going. If I mute the front, the headphones also make no sound. (Oddly, it was all working fine last night, after I tried various fixes for sound problems.)

N.B. This is when my headphones 'switch' is ticked on in AlsaMixer. When the box is unticked, the headphones don't work at all.

I have a Toshiba Satellite A135-S4527 laptop.

Other possibly relevant info:

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC861VD Analog [ALC861VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

pixnaps@rc-laptop:~$ head -n 1 /proc/asound/card0/codec*
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC861-VD

==> /proc/asound/card0/codec#1 <==
Codec: Generic 11c1 ID 1040
pixnaps@rc-laptop:~$ 

I added the alsa-base line "options snd-hda-intel model=3stack" as instructed [here]("http://ubuntuforums.org/showthread.php?t=806620&highlight=headphone+speaker"), given this info:
ALC861VD/660VD
          3stack        3-jack
          3stack-dig    3-jack with SPDIF OUT
          6stack-dig    6-jack with SPDIF OUT
          3stack-660    3-jack (for ALC660VD)
          3stack-660-digout 3-jack with SPDIF OUT (for ALC660VD)
          lenovo        Lenovo 3000 C200
          dallas        Dallas laptops
          hp            HP TX1000
          auto          auto-config reading BIOS (default)

And I followed the instructions [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/184314/comments/19"), but to no avail.

Help?

---

### Post by Pjotr123 on 2008-06-29
Try what alsamixergui can do:
[http://ubuntutip.googlepages.com/sound](http://ubuntutip.googlepages.com/sound)
(number 2 )

---

### Post by pixnaps on 2008-06-29
Yeah, that doesn't help. I've got all channels open. Note that the headphones DO work, but they fail to mute the speakers. (I see others have had the same problem [here]("http://ge.ubuntuforums.com/showthread.php?t=804986").)

---

### Post by pixnaps on 2008-06-29
Fixed! I just needed to replace my '3stack' alsa-base line with the following:
```
options snd-hda-intel position_fix=1 model=lenovo
```

---

