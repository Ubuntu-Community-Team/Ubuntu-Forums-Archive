---
title: "can not connect to internet via wireless"
date: 2010-01-19
forum: Networking &amp; Wireless
---

### Post by serviam on 2010-01-19
Hello everyone. I am new to the forum as well as to linux of any flavor. I installed ubuntu 9.10 on my lap top. It is required in a class I am taking as well as I am trying to lean more about linux. I can not connect to the internet since I installed ubuntu. I emailed my professor, and he stated the following: "I did a little research and it looks like your laptop has a broadcom wireless adapter. From what I've read, it should be possible for you to get your [COLOR=#000]wireless adapter[/COLOR] working via Ndiswrapper. Below is a link that should get you started: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)." So theoretically, all I must do is download these files from one of the listed sites, install them on my lap top, and theoretically I should have internet, correct? I have a compaq pressario v5205wm. Also, do drivers function in the same capacity in linux as they do in Windows? I know windws has the device manager to view your hardware as well as their drivers. Where is this on linux os? Sorry for the long drawn out thread, and thanks for your cooperation.
 
-serviam

---

### Post by bkratz on 2010-01-19
> **serviam said:**
> Hello everyone. I am new to the forum as well as to linux of any flavor. I installed ubuntu 9.10 on my lap top. It is required in a class I am taking as well as I am trying to lean more about linux. I can not connect to the internet since I installed ubuntu. I emailed my professor, and he stated the following: "I did a little research and it looks like your laptop has a broadcom wireless adapter. From what I've read, it should be possible for you to get your [COLOR=#000]wireless adapter[/COLOR] working via Ndiswrapper. Below is a link that should get you started: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)." So theoretically, all I must do is download these files from one of the listed sites, install them on my lap top, and theoretically I should have internet, correct? I have a compaq pressario v5205wm. Also, do drivers function in the same capacity in linux as they do in Windows? I know windws has the device manager to view your hardware as well as their drivers. Where is this on linux os? Sorry for the long drawn out thread, and thanks for your cooperation.
 
-serviam

Well we do need to  know what the wireless card is

Go to the terminal (Applications>>Accessories>>Terminal)
and type in lspci (that is LSPCI in lowercase) and copy/paste it back here. You probably don't actually need ndiswrapper at all.

lspci will tell what your wireless is

---

