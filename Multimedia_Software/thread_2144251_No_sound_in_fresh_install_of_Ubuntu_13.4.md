---
title: "No sound in fresh install of Ubuntu 13.4"
date: 2013-05-11
forum: Multimedia Software
---

### Post by julotte on 2013-05-11
Hi everyone,

Could anyone help me with my problem? I bought a laptop without OS and installed Ubuntu 13.04 on it. Everything is fine except that there is no sound at all. I tried many things following online tuto but still no luck. Here are more details:

```

pci | grep -i audio
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)

```

```

$ aplay -l
**** Liste des Périphériques Matériels PLAYBACK ****
carte 0: PCH [HDA Intel PCH], périphérique 0: ALC269VB Analog [ALC269VB Analog]
  Sous-périphériques: 1/1
  Sous-périphérique #0: subdevice #0
carte 0: PCH [HDA Intel PCH], périphérique 3: HDMI 0 [HDMI 0]
  Sous-périphériques: 1/1
  Sous-périphérique #0: subdevice #0

```

```

grep "Codec:" /proc/asound/card*/codec*
/proc/asound/card0/codec#0:Codec: Realtek ALC269VB
/proc/asound/card0/codec#3:Codec: Intel PantherPoint HDMI

```

```

cat /proc/asound/modules
 0 snd_hda_intel

```

Thank you!

---

### Post by julotte on 2013-05-13
Hello,

Actually, I found out that when plugged-in, the headphones work properly, so I guess it means the sound card is working. So the problem seems to come from the internal speakers.

Othermore, I installed a dual boot on this laptop and I got exactly the same problem with windows 8 (no sound on speakers but works with headphones) while I installed the windows 8 sound drivers provided with the laptop.

Could this problem be something else than an hardware issue with the speakers?

Thank you for your help.

---

### Post by ipeters61 on 2013-05-13
Is this the "traditional" flavor of Ubuntu (i.e.: are you using the Unity desktop environment or another one?)?  If it's Xubuntu, I know that it has a pretty powerful volume mixer.

Also, have you looked at alsamixer?  I know using alsamixer has helped me with many audio problems.

---

