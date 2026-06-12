---
title: "NVIDIA GeForce 6150 and nForce 430 supported?"
date: 2006-10-04
forum: Multimedia &amp; Video
---

### Post by twrock on 2006-10-04
I have a new system based on the ASUS M2NPV-VM motherboard. Although the included CD has NVIDIA drivers for both the GeForce 6150 GPU and the nForce 430 MCP, I have not been successful in getting them loaded. 

I am trying to determine if my hardware problems are a result of lack of drivers or some kind of configuration problems. My simple question is: are both of these chipsets supported in Ubuntu 6.0.6 "out of the box"? Any other pointers for me?

---

### Post by tseliot on 2006-10-04
out of the box you have the "nv" driver, i.e. the open source driver which doesn't support 3d acceleration and some cards.

You should use the "nvidia" (proprietary) driver. Try Method 1 of this guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

---

### Post by twrock on 2006-10-04
Thanks. I'll give it a try.

---

