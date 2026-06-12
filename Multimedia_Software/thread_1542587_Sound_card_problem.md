---
title: "Sound card problem"
date: 2010-07-30
forum: Multimedia Software
---

### Post by kamrul.hasan on 2010-07-30
My laptop is Sony VAIO. I installed ubuntu. However i dnt get sound. My sound card is not working i think. How can i install my sound card here in ubuntu. if anyone know please tell me

---

### Post by lidex on 2010-07-30
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

