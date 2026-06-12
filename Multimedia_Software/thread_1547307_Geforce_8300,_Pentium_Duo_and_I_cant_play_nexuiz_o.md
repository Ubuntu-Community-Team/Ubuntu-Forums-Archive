---
title: "Geforce 8300, Pentium Duo and I cant play nexuiz or Urban Terror ??"
date: 2010-08-06
forum: Multimedia Software
---

### Post by zonemikel on 2010-08-06
Ok this really throws me for a loop, i have tons of computers running and my best one cant play the oldest games. My old P3 can play these games and this computer cant. 


```
michael@ubuntu:~$ lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8300 GS (rev a1)
michael@ubuntu:~$ uname -a
Linux ubuntu 2.6.28-18-generic #60-Ubuntu SMP Fri Mar 12 04:40:52 UTC 2010 i686 GNU/Linux
processor    : 1
vendor_id    : GenuineIntel
cpu family    : 6
model        : 15
model name    : Intel(R) Core(TM)2 Duo CPU     E4400  @ 2.00GHz
stepping    : 13
cpu MHz        : 1200.000
cache size    : 2048 KB
. . . 
michael@ubuntu:~$ cat /proc/meminfo 
MemTotal:        2061584 kB
MemFree:         1421700 kB
Buffers:           24804 kB
. . . 

```So basically a 2GHz machine with 2Gigs of ram and a Geforce 8300. I'm running Ubuntu 9.04 (jaunty i think ?). 

Anyway all of the basic games dont work well, they are choppy and slow. I put them in the lowest resolution just for them to be playable. It does not make any sense to me I have the latest version of the nvidia drivers running (I used ./NVI... --update) 

```
michael@ubuntu:~$ nvidia-settings -v

nvidia-settings:  version 256.44  (buildmeister@builder97.nvidia.com)  Thu Jul
29 01:59:48 PDT 2010
  The NVIDIA X Server Settings tool.

  This program is used to configure the NVIDIA Linux graphics driver.

  Copyright (C) 2004 - 2010 NVIDIA Corporation.

```Does anyone have any idea what the hell is going on, this makes no sense to me. The only thing I can think of is a crappy video card ? but still i should be able to run these old games. 

thanks for your time, this is my last hope before trying windows to see if the games run better under windows.

---

### Post by zonemikel on 2010-08-06
*bump*

I read up on the 8300 it does not seem like that bad of a card. I think nexuiz is a buggy game on some systems, not sure about urban terror.

---

### Post by zonemikel on 2010-08-07
*bump* .... 

guess i'll install windows

---

### Post by linux18 on 2010-08-07
did you use the driver from the nvidia website?

---

### Post by zonemikel on 2010-08-07
> **linux18 said:**
> did you use the driver from the nvidia website?

Yes, I installed manually using the --update option of the driver I downloaded from the nvidia website. I did not use the ubuntu "hardware drivers" thing.

---

### Post by DarthScape on 2010-08-07
Maybe the drivers from the ubuntu repo would work better for the older card.

---

### Post by Yellow Pasque on 2010-08-07
I have an 8400GS and it runs openarena at 1680x1050 with max detail. Check glxinfo and see what glxgears gives you (install mesa-utils package).

---

