---
title: "Sounds is just static..."
date: 2010-06-12
forum: Multimedia Software
---

### Post by Drags111 on 2010-06-12
I just installed 10.04 on my hd, and now when I try to play any music or any sound tries to play, I only get static. I have a rocketfish soundcard, and I tried to set it up in the sound preferences. I went through every profile possible, but all just static... Any help would be great. Thanks.

---

### Post by lidex on 2010-06-13
Is this the first try of linux using that soundcard?
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

