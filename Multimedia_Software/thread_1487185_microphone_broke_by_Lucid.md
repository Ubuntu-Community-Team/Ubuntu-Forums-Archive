---
title: "microphone broke by Lucid"
date: 2010-05-18
forum: Multimedia Software
---

### Post by katj12480 on 2010-05-18
I have found Realtek ACL268, HDA-Intel
My microphone worked perfectly in Karmic.
I have turned everything all the way up in sound properties as well as the gnome alsa mixer.  I have verified that the microphone works on a different computer.

Please tell me if there is other information I can give you to help me.

Thanks!

---

### Post by lidex on 2010-05-20
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Also helpful is the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by wishingstar on 2010-05-20
I'm not sure what the problem is exactly, but the only way i could get my mic to ever work (i've been using ubuntu since januty) was to use the voice recorder on LiveCD BEFORE installing the system (clean install every time).

Wishing Star

---

