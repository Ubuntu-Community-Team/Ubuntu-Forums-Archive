---
title: "Very slow connection speeds, but no problems on Windows 7"
date: 2010-04-05
forum: Networking &amp; Wireless
---

### Post by gkkg on 2010-04-05
I am currently staying on a university campus in Taiwan. Internet on Ubuntu Lucid 64bit here is often painfully slow, except for connections to Taiwanese websites. I dual boot with Windows 7, and there is no problem there. For instance, I downloaded the same piece of software (Spideroak) on both Win and Ubuntu, with Ubuntu I had to try repeatedly as the download would not complete, and in the end it took several hours to download. On W7, it took 10 minutes. What is Windows and Ubuntu doing differently?

I tried disabling ipv6 for this session by running sudo sysctl -w net.ipv6.conf.all.disable_ipv6=1, as a number of posts mention improving connection speed that way, but no effect.

I know that websites from Taiwan are working well, because I am getting my Ubuntu updates from a Taiwanese mirror: updates are fast, except for packages in the 'partner' repos (presumably not loaded from the mirror) which take hours to load, if at all.

Please help, I don't want to depend on Windows for large downloads... (I don't want to depend on Windows for ANYTHING)

---

### Post by sakundiak on 2010-04-05
I used to have this problem, i tried every single thing i came across in the forums and in the end i ended up switching to a new wireless card and voila. I had a broadcom 4306 and switched out for a dlink DWL-G122 which i might add works out of the box.

---

### Post by gkkg on 2010-04-20
I just realised I get faster connection speeds running Windows XP in virtualbox!
How is this possible??

---

### Post by dineshs on 2010-04-21
Slow internet can also be due to DNS issue or MTU

---

