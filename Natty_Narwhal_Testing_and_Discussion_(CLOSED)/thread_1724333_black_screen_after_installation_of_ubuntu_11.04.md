---
title: "black screen after installation of ubuntu 11.04"
date: 2011-04-08
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by usamahashimi on 2011-04-08
Hi
I have downloaded the beta version of Ubuntu 11.04 and installed it. The installation went correctly with some flickering in display during installation. But the real problem starts after installation, when I turn on my PC and select Ubuntu from GRUB, the screen flickered a lot and then went black and PC got hanged. Can anyone tell me that what may be the problem and how can I fix it?
Regards.

---

### Post by philinux on 2011-04-08
Moved to Natty forum.

---

### Post by Quackers on 2011-04-08
What graphics card are you using? When you installed 10.10 (previously) did you need to use a boot prompt (like nomodeset)?

---

### Post by usamahashimi on 2011-04-08
user@pc ~ $ lspci | grep VGA
00:10.0 VGA compatible controller: nVidia Corporation C73 [GeForce 7050 / nForce 610i] (rev a2)


Yes, I have to use 'nomodeset' in Ubuntu 10.10 but now this option is not working in Ubuntu 11.04.

---

