---
title: "Monitor Internet Bandwidth"
date: 2009-12-05
forum: Networking &amp; Wireless
---

### Post by leehamer on 2009-12-05
Hi,

I have recently been having issues where I am been billed for bandwidth (gone over my monthly allowance) But this has even been happening when my router is not even plugged in!! :o

Is there a bandwidth monitor application I can install to monitor how much my computer uses?

---

### Post by Yoann Juet on 2009-12-05
There's plenty of applications. One of my favorite is ifstat.

Install it,

#apt-get install ifstat

and then get instant bandwidth use,

#ifstat -b -S

---

