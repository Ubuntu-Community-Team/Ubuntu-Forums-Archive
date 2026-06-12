---
title: "How to test and check if my hybrid TV tuner works?"
date: 2009-03-23
forum: Mythbuntu
---

### Post by valentt on 2009-03-23
Hi I have Gigabyte GT-PTV-TAF-RH (hybrid tv card - analog/DVB-T) TV card that uses saa7134 module with these options: card=81 tuner=54

How can I manually test if this card works? What are the tools for scanning TV channels?

Cheers,
Valent.

---

### Post by newlinux on 2009-03-23
Install dvb-utils. It includes a "scan" utility (the command scan) that takes in a frequency table and scans it. Or for dvb-t (I'm not very familiar with non US signals) you can also use w_scan. I don't think it is in the repos, but [http://www.linuxtv.org/wiki/index.php/Scan](http://www.linuxtv.org/wiki/index.php/Scan) will give you more information.

---

### Post by newlinux on 2009-03-23
I should add, if you use scan, after you install dvb-utils you'll find the DVB-T frequency tables in:

/usr/share/doc/dvb-utils/examples/scan/dvb-t/

---

### Post by valentt on 2009-03-23
How to test the plain old analogue part, not digital DVB-T part?

Cheers,
Valent.

---

### Post by newlinux on 2009-03-23
tvtime would be my guess.

---

### Post by valentt on 2009-03-26
> **newlinux said:**
> tvtime would be my guess.

Thanks! I found tvtime and tvtime-scanner and it works!

---

