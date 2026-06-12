---
title: "Any extra steps for ATI in Ubuntu 7.04 (Feisty?)"
date: 2007-07-16
forum: Multimedia &amp; Video
---

### Post by hanzotutu on 2007-07-16
I made a clean install of Ubuntu 7.04 on a Dell D600 laptop with a ATI video card.

lspci -n | grep 0300
01:00.0 0300: 1002:4c66 (rev 02)
lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R250 [Mobility FireGL 9000] (rev 02)

It seems everything works well, and glxgears gives me ~850 FPS. However, I found it is very slow to browse and edit spreadsheets in docs.google.com with Firefox. Xorg takes all the CPU time while I am moving the cursor around spreadsheets. I am wondering if this problem has anything to do the card driver in Xorg. Could you please give me some advice how should I fix this problem. Thanks.

---

### Post by Daveth on 2007-07-16
have a look at
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

for the appropriate ATI driver.

---

