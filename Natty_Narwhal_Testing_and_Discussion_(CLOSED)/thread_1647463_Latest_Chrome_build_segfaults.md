---
title: "Latest Chrome build segfaults"
date: 2010-12-17
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by wnelson on 2010-12-17
I get this for the first time in a real long time.

After dist-upgrade

Chromium 10.0.614.0 Built on Ubuntu 11.04

chromium-browse[1865]: segfault at 34 ip b5883d53 sp ad330b00 error 6 in chromium-browser[b4c28000+2cd3000]

---

### Post by Harry33 on 2010-12-17
The latest Chromium released is version 8.0.552.224.
In ubuntu natty the latest it this package (the same):
chromium-browser 8.0.552.224~r68599-0ubuntu1

---

### Post by Mononofu on 2010-12-17
I have the exact same problem, let's hope it will be fixed fast.

---

### Post by castrojo on 2010-12-17
Did you guys install the pdf viewer from chrome perhaps?

[http://askubuntu.com/questions/17986/chromium-stopped-working](http://askubuntu.com/questions/17986/chromium-stopped-working)

---

### Post by wnelson on 2010-12-17
I have no libpdf.so in /usr/lib/chromium-browser/

---

### Post by wnelson on 2010-12-18
I ran chrome with chromium-browser --temp-profile and it starts up. There must be a plugin, extension, etc. causing problems.
I am going to see which one?

---

### Post by wnelson on 2010-12-18
I disabled sync and it worked fine. chromium-browser --disable-sync

---

### Post by wnelson on 2010-12-18
10.0.615.0 (69622) Built on Ubuntu 11.04

Fixed

---

