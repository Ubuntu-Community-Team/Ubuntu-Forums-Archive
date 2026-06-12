---
title: "Ubuntu 16.04: Problems to get M-audio Ozone working."
date: 2017-07-04
forum: Multimedia Software
---

### Post by citizenkant on 2017-07-04
Hi there,
I have a little issue here that I hope I can resolve with your help. I've been working on this all along yesterday but I could not figure out what's goin on.
Google says: install madfuload, so I did. Install Jack, done, but, Jack cannot start serving and freeze the machine unless I start with:
```
 jackd -R -d alsa -d hw:0,3 
```

no sign of the keyboard anyways neither in Jack nor LMMS.

```
lsusb
```
shows it as Midiman.
```

citizenkant@citizenkant-SATELLITE-C50D-A-12R:~$ lsusb
Bus 002 Device 002: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 04f2:b3b1 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 006: ID 0930:0220 Toshiba Corp. 
Bus 003 Device 007: ID 0763:2808 Midiman 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 002: ID 041e:30dd Creative Technology, Ltd 
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

What more information can I offer? Any command?

Thanks a lot in advance.-

---

### Post by citizenkant on 2017-07-07
Not a hint?

---

### Post by TREESofRIGHTEOUSNESS on 2017-07-09
Did you install the firmware?
```

sudo apt install madfuload

```

---

### Post by RobertoRecordo on 2017-07-18
I don't have an answer, I'm here to find out if  works on Linux
Here is a success story, for what it's worth
[https://ubuntuforums.org/showthread.php?t=1475651&highlight=m-audio+ozone](https://ubuntuforums.org/showthread.php?t=1475651&highlight=m-audio+ozone)

Please post if you get it working!

---

