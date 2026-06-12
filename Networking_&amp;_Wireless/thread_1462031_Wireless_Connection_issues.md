---
title: "Wireless Connection issues???"
date: 2010-04-25
forum: Networking &amp; Wireless
---

### Post by suryaccnamcse on 2010-04-25
I am not able to connect properly with my network card wirelessly in Ubuntu (the wireless connects only after 4-5 mins of trying to connect, but once it connects it works perfectly), I used to be able to connect properly when I was using windows 7. I remember to make the wireless work properly I had to install an updated driver from Intel. 
I have downloaded this driver in .tgz but have no idea how to install it in Ubuntu 10.04 RC which I am using now as I have formatted windows 7.
Please let me know how to install the drivers, I searched and googled a lot but all the articles tell that for further support go to Ubuntu forums.

---

### Post by suryaccnamcse on 2010-04-26
I downgraded to 9.10 and the internet connects perfectly, Lucid may have some issues to be resolved before the 29th

---

### Post by P4man on 2010-04-26
I believe there is a regression in the kernel for some wifi  drivers that would be fixed in an update after release (fix came too late to make it in iirc).  So just so you know its  possible the release 10.04 wont work for you, and you need to run update to get the fix. If you need the cd to work, like when you dont have wired internet connection you may want to wait for 10.04.1 or download a daily build some time after release.

BTW, its always a good idea to report which wifi card you have exactly. If you dont know, open a terminal and type

```
lspci
```

---

### Post by suryaccnamcse on 2010-04-30
the Wifi adapter is intel pro/wireless 3945ABG. I have again installed 10.04 LTS and this time the wireless works perfectly. The Ubuntu development team has done a good job in ironing out the bugs...

---

