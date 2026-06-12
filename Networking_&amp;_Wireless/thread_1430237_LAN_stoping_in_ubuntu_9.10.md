---
title: "LAN stoping in ubuntu 9.10"
date: 2010-03-15
forum: Networking &amp; Wireless
---

### Post by sshatery on 2010-03-15
i was installed ubuntu 9.10 just yesterday and after that i have didnt any problem and i was connected to the internet without any problem but after the first restart both of my wired network and wireless network was stoped and i was couldnt connect to the internet. i dont know was is the problem and i was cheked everything but all of them are ok. i didnt had this problem when i was used ubuntu 9.10 on live usb. i have got some screen shot from my problem and put it in here to realize you about my problem.
please help me to resolve the problem very soon.

[IMG]http://img2.tinypic.info/files/ai9gc6gsysz83qr59578.jpg[/IMG]
[IMG]http://img2.tinypic.info/files/kcu950dffdj8qnub5n2l.jpg[/IMG]
[IMG]http://img2.tinypic.info/files/rvjqxq87kfaxwdplhe9p.jpg[/IMG]

---

### Post by Iowan on 2010-03-15
If you have interface(s) defined in */etc/network/interfaces*, it will (or used to) make NM ignore them. Perhaps that's what you want - but try commenting out the definitions and rebooting to see if NM behaves differently.

---

