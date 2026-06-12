---
title: "WNA1000 usb adapter problems"
date: 2010-05-23
forum: Networking &amp; Wireless
---

### Post by brandon_ on 2010-05-23
I am running lucid 10.04. unfortunately, I cannot get my wireless adapter to work. i must use wireless since the router is a not in the same room and running cat5 isn't an option. i have tried installing compat-wireless, ndiswrapper and it still doesn't work.

details of lsusb:
bus 002 device 001 id 0846:9040 Netgear, inc
(others omitted)

details of iwconfig:
lo no wireless extensions
eth0 no wireless extensions

i don't know what to do. any help at all would be greatly appreciated.

---

### Post by Slave2Metal on 2010-05-23
This adapter is a royal pain in linux.  If you can return it, do so and research the ones that do work.  It's just too new to be supported.

---

### Post by brandon_ on 2010-05-23
this is the second adapter i have bought. the other one was not supported at all. i have heard of people getting it to work. i have never experienced such frustration. supposedly, this adapter has been supported in mainline kernel since 2.6.30. ([http://linux-wless.passys.nl/query_chipset.php?chipset=Atheros](http://linux-wless.passys.nl/query_chipset.php?chipset=Atheros))

i am going to try to do a clean reinstall since i might have broken something trying to fix the other adapter.

---

### Post by Slave2Metal on 2010-05-23
I'm definitely interested in the steps if your successful.  I've tried ndiswrapper and the compat wireless files with no success.  I wish you luck.

---

### Post by brandon_ on 2010-05-23
i think i am just going to try a different adapter. i am looking at the wg111us any suggestions would be greatly appreciated. see [http://ubuntuforums.org/showthread.php?t=1491682](http://ubuntuforums.org/showthread.php?t=1491682)

---

### Post by brandon_ on 2010-05-24
wel the wg111 worked right out of the box. :)

---

