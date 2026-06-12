---
title: "B43 driver in monitor mode for with wireshark"
date: 2012-07-06
forum: Networking &amp; Wireless
---

### Post by xkcd1253 on 2012-07-06
Hi, I'm trying to capture packets on a network coming from other computers other than my laptop. To do this I understand that my wireless driver(b43) needs to be in monitor mode. I was able  to do that by using airomon with iw config and got mon0 in monitor mode. Now when I open wireshark, select mon0, and check the monitor mode box, it says: 
   The capabilities of the capture device "mon0" could not be obtained (That device doesn't support monitor mode).
Please check to make sure you have sufficient permissions, and that
you have the proper interface or pipe specified.

How can I fix this?

---

### Post by O2Blevel on 2012-07-06
Did you sudo wireshark?

---

### Post by xkcd1253 on 2012-07-06
Yes

---

### Post by xkcd1253 on 2012-07-06
yes

---

### Post by chuinul on 2012-11-19
Hello,

I have the same problem. Did you manage to fix it ? I read somewhere that it could be due to an old version of some library so I tried to recompile wireshark from the last version of the source but it has changed nothing...

Thanks in advance.

---

