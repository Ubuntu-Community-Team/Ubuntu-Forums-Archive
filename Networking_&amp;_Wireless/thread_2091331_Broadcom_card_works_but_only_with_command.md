---
title: "Broadcom card works but only with command"
date: 2012-12-04
forum: Networking &amp; Wireless
---

### Post by boz86 on 2012-12-04
Hi,

I've got my Broadcom 4311 card working, but only if I type

 ```
sudo modprobe b43
``` in the terminal.

I've been bouncing around trying all the alternatives I've seen here and elsewhere, and got that close. Although I wrote a script to get the wireless working (a complete one line masterpiece :D), I obviously have to enter my password.

Am I getting conflicts with other drivers? Should I remove them?

Oh yeah, how do I do that?

Thanks,
Ken

---

### Post by boz86 on 2012-12-05
Forgot to add that it stops working as soon as I reboot, then restarts once I run that command.

---

### Post by rioguia on 2012-12-05
i think i'm working on a similar problem.

[http://ubuntuforums.org/showthread.php?t=2090717](http://ubuntuforums.org/showthread.php?t=2090717)[]("Broadcom Corporation BCM4312 disabled by kernel update")

---

### Post by boz86 on 2012-12-05
> **rioguia said:**
> i think i'm working on a similar problem.
 
 Does look very similar, doesn't it?

---

### Post by bkratz on 2012-12-05
> **boz86 said:**
> Forgot to add that it stops working as soon as I reboot, then restarts once I run that command.



If you follow the steps in this page it will add the module at startup for you.

[http://ubuntuforums.org/showpost.php?p=12372358&postcount=21](http://ubuntuforums.org/showpost.php?p=12372358&postcount=21)

---

### Post by boz86 on 2012-12-06
Thanks much, that seems to have done it ):P

---

### Post by bkratz on 2012-12-06
> **boz86 said:**
> Thanks much, that seems to have done it ):P



Glad you got it, enjoy!

---

