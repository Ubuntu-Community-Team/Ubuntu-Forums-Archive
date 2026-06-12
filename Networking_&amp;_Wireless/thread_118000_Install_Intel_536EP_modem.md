---
title: "Install Intel 536EP modem"
date: 2006-01-15
forum: Networking &amp; Wireless
---

### Post by sergiodlc on 2006-01-15
Hi:

Does anyone of you know how can I install my modem drivers? I have an Intel 536EP modem. I have the sources but it fails when I follow the instructions in the readme file. Any suggestion?

Sergio

---

### Post by akiro.yamamoto on 2006-01-15
What is the error message.
Just in case....
Remember to install build-essential...
The drivers may have been designed for Gcc 3.x...not GCC 4.x.
So you could try
EXPORT gcc=3.4 or something similar..... search the forum for the exact code sequence....

---

