---
title: "Packard Bell KAV60: builtin mic produces no sound"
date: 2010-07-12
forum: Multimedia Software
---

### Post by svu on 2010-07-12
Hi ppl

There is an issue with built-in microphone on the KAV60 laptop - it produces no signal to apps. If I plug in external mike - it works fine.

lspci shows:

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)

Adding various options "model=..." for snd-hda-intel ALC272 does not help (ALC272 is returned by "aplay -l"). What else could I try?

Thanks

---

### Post by lidex on 2010-07-14
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by skot_06 on 2011-10-09
workaround described [here]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/723532") in comments works for my kav60

---

