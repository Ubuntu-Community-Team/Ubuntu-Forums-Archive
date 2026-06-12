---
title: "Ubuntu 9.10 Dell Insprion 1521/Broadcom wireless Problems"
date: 2009-11-17
forum: Networking &amp; Wireless
---

### Post by MythernJenkins on 2009-11-17
i have tryed and tryed and i can not get the wireless to work on my dell laptop 


any help is nice

---

### Post by t0mppa on 2009-11-17
In order to get some help, you're going to have to give us a bit more information about your situation. A good start would be opening up terminal (Applications / Accessories / Terminal), running the following commands:```
lshw -C network
lspci -vnn | grep 14e4
``` and posting back with the results to show us which chip/driver you are using.

---

### Post by MythernJenkins on 2009-11-18
i cant get nothing to work now i think ubuntu crasher it keeps telling me mount of fliesystem failed 

so ill get back once i find out whats going on now

---

