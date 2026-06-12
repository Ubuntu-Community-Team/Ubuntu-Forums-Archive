---
title: "Can anyone help me with wireless cards?"
date: 2010-09-16
forum: Networking &amp; Wireless
---

### Post by gdavison on 2010-09-16
Basically i need a new wireless card for my desktop. It needs to have high coverage and i need to be able to get it up and running without too much hassle. I was looking at [http://tiny.cc/5l8r5](http://tiny.cc/5l8r5) but i dont know if this is easy to get running.
Im not very experienced with linux so any help is welcome.
Thanks in advance:)

---

### Post by chili555 on 2010-09-16
This device uses the rt2860sta driver; it's built-in to Ubuntu's recent kernels:```
/lib/modules/2.6.32-22-generic/kernel/drivers/staging/rt2860/rt2860sta.ko
/lib/modules/2.6.32-23-generic/kernel/drivers/staging/rt2860/rt2860sta.ko
/lib/modules/2.6.32-24-generic/kernel/drivers/staging/rt2860/rt2860sta.ko
```Some here report difficulty getting it to work at N speeds and some report it drops connections.

[http://ubuntuforums.org/showthread.php?t=1361071&page=2](http://ubuntuforums.org/showthread.php?t=1361071&page=2)


Can it be made to work? Yes. Reliably? Maybe and maybe not.

---

### Post by gdavison on 2010-09-17
Ok thanks, can you recomend any cards that are more reliable?

---

### Post by chili555 on 2010-09-18
Please check here: [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

And here: [http://www.dudek.org/wireless](http://www.dudek.org/wireless)

---

