---
title: "No sound in ubuntu Lucid. SPDIF only option"
date: 2010-04-17
forum: Multimedia Software
---

### Post by Mr_Tricorder on 2010-04-17
I just installed Ubuntu Lucid beta 2 on my desktop, and I can't seem to get the sound to work.  I have a Soundblaster Audigy 2 card and the motherboard has built-in sound, but ubuntu doesn't recognize either of them.  The only hardware option I have in my sound preferences is for SPDIF, and thats the only thing that shows up in alsamixer as well.  Does anyone have any ideas on how to fix this?

---

### Post by lidex on 2010-04-18
Reboot and disable onboard audio in bios. Then I'll need some info. Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

---

