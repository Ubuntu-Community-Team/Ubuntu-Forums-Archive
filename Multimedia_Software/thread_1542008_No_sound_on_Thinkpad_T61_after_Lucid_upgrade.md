---
title: "No sound on Thinkpad T61 after Lucid upgrade"
date: 2010-07-29
forum: Multimedia Software
---

### Post by splitpane on 2010-07-29
Hello,

I can't get sound to work and am not sure how to trouble shoot.  The sound DOES work when first booting, and I can make it play a test beep with the sound config app.  But I cannot get sound from any other application.  One possibly relevant fact is that I see a lot of I/O errors early in the boot process, but they flash by quickly so I cannot quote them.

Can anybody provide some suggestions on how to troubleshoot?

Thanks.

---

### Post by lidex on 2010-07-30
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
```
dmesg | grep -C1 -E 'ALSA|HDA|HDMI|sound|hda.codec|hda.intel'
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

