---
title: "Belkin N150 Wireless router in Kubuntu"
date: 2011-09-23
forum: Networking &amp; Wireless
---

### Post by ColeTurner on 2011-09-23
Is it possible to set up a Belkin N150 Wireless router in Kubuntu? If sow, how?

---

### Post by chili555 on 2011-09-24
It should be easy. Hook up an ethernet cable to your computer and to any LAN port on the router. Open a terminal and do:```
sudo ifconfig 192.168.2.2 up
firefox 192.168.2.1
```You should then be in to the setup pages of the router. Please see page 8 of the manual.

---

### Post by ColeTurner on 2011-09-25
Which manual?

---

### Post by bkratz on 2011-09-25
> **ColeTurner said:**
> Which manual?


he was referring to the manual for your router. In case you don't have the manual you can download it here.

[http://en-us-support.belkin.com/app/answers/list/kw/N150%20Manual](http://en-us-support.belkin.com/app/answers/list/kw/N150%20Manual)

---

### Post by ColeTurner on 2011-09-26
As usual, you guys are awesome! Thank you. I want to run Ubuntu as a virtual machine in Windows XP. Is there any free virtualization software I can do this with?

---

### Post by chili555 on 2011-09-26
You'll probably have better luck asking in General Help and please reference virtualization in the thread title. [http://ubuntuforums.org/forumdisplay.php?f=331](http://ubuntuforums.org/forumdisplay.php?f=331)

---

