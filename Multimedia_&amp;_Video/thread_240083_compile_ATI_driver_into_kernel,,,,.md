---
title: "compile ATI driver into kernel,,,,"
date: 2006-08-20
forum: Multimedia &amp; Video
---

### Post by zjcim on 2006-08-20
i download kernel-soucre 2.6.17-6

make oldconfig & make some changes in kernel-config
```
Processor type and features  ---> 

[*] MTRR (Memory Type Range Register) support         

Device Drivers  --->  Character devices  --->

<*> /dev/agpgart (AGP Support)   
<*>   Intel 440LX/BX/GX, I8xx and E7x05 chipset support   
```

Boot up the new kernel,but cann't start x-window
it said :
```
(EE) RADEON(0): mmap mmio: Invalid argument

Fatal server error:
AddScreen/ScreenInit failed for driver 0
```

i have to change ati to vesa in xorg.conf
then it is ok

run glxgears get a high score,but still no direct rendering by glxinfo
i really got confused

---

### Post by whatever on 2006-08-20
why don't you use the ubuntu kernel?

---

### Post by zjcim on 2006-08-20
if i use default kernel default ati driver ,the "dapper freeze 1 4 times "would happen upon me 

and ati's propriatary driver fglrx don't support my video card any more

---

