---
title: "Rainbow/pixel splatter screen"
date: 2010-07-11
forum: Multimedia Software
---

### Post by TheRealZ on 2010-07-11
Hello Ubuntu Forums.

My installation of Ubuntu 10.04 have a weird bug, that makes Ubuntu crash at random times with a rainbow/pixel splatter screen (I don't know how else I can express it), when I work in Ubuntu.

I don't know how to troubleshoot or reproduce the bug, because of the random intervals between the different crashes.
I tried to run a stress test with FurMark (through Wine), and after 4 minutes, and I get the closes thing I can come to a reproduce.

It is possible to boot Ubuntu with recovery mode and into FailSafeX, and work without any crashes.

I'll post my Xorg logs, and computer hardware specification, if you need anything else, then please tell me. :)

Computer Specifications:
Intel(R) Pentium(R) 4 CPU 3.20GHz
Nvidia GeForce FX 5900XT - with driver version 173.14.22
2 x Seagate 149 GB Sata Harddisks.

Edit:
I forgot to mention, that when I get the rainbow/pixel splatter screen, I lose connection to my monitor, when I reboot my computer, and will not get any signal from my graphics card no matter how many times  I reboot my computer.

I have to take the power off my computer and monitor, to get the connection back.

---

### Post by TheRealZ on 2010-07-17
Hey everyone.

I think, I have solved the problem.

After a little research on nvnews, I found this very good thread about stability problems with the nvidia linux driver: [http://www.nvnews.net/vbulletin/showthread.php?t=58498](http://www.nvnews.net/vbulletin/showthread.php?t=58498).

In the thread, I found a part about agp cards, and added as written the NvAGP option with the "0" parameter to my Xorg.conf file:
```

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    Option	   "NVAGP"	"0"
EndSection

```

I've been running my system in a week, and I haven't had a crash ever since. I even could run FurMark in 30 minutes with no crashes during the test period.
(I quit the program myself)

In conclusion, I see this problem as solved, and hope this post will help others with the same or similar problem. :D

---

