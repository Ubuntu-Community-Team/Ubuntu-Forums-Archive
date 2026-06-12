---
title: "Extremely low fps with ati radeon"
date: 2006-09-22
forum: Multimedia &amp; Video
---

### Post by WalmartSniperLX on 2006-09-22
My system is:

AMD Sempron 64 3100+ (this is the K8 chip) @ stock 1.8ghz
1gb corsair performance ram 
256mb ddr2 Ati Radeon x1600pro

And I notice that my frame rate/performance is really slow in linux graphically. I have the newest ati driver 8.29.6. Is there a certain configuration that I can do with aticonfig to speed it up. And btw yes its installed correctly, I checked with fglrxinfo. Output is as follows:

[I]display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1600 Series Generic
OpenGL version string: 2.0.6065 (8.29.6)
 [/I]

Any suggestions?

---

### Post by whatever on 2006-09-23
the fglrx driver _is_ slow.
you can expect about half of the performance the windows driver offers.

---

### Post by WalmartSniperLX on 2006-09-23
are there any alternatives to the fglrx drivers?

---

### Post by whatever on 2006-09-23
no, for your X1600 there is no alternative.

---

### Post by mygom on 2006-10-01
Umm what about my X550? (Shows as X300\X550) Is there an alternative to fglrx for me?
Using any of the 3 latest versions of fglrx i get REALLY low performance (~250 fps using glxgears), so I downgraded to version 8.26.18 and now i get ~2800 fps using glxgears, but still I understand that it is much lower than i should be getting...

---

