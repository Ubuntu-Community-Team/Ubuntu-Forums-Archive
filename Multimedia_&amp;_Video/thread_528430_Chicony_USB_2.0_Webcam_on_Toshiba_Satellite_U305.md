---
title: "Chicony USB 2.0 Webcam on Toshiba Satellite U305"
date: 2007-08-17
forum: Multimedia &amp; Video
---

### Post by ntlam on 2007-08-17
Hi everyone,

Do you know how I can get and install the driver for Chicony USB 2.0 Webcam?

Thanks

Lam

---

### Post by linuxwizard on 2007-08-18
[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

---

### Post by ntlam on 2007-08-19
I've tried with easycam then installed the driver manually but both ways did not work.
Any other suggestion please

---

### Post by linuxwizard on 2007-08-19
Have you tried lsusb command to see if it is listed as a  USB device ?
I searched for Chicony I don't see a webcam listed. I would say not supported no USB drivers.
[http://www.qbik.ch/usb/devices/search_res.php?pattern=Chicony](http://www.qbik.ch/usb/devices/search_res.php?pattern=Chicony)

---

### Post by ntlam on 2007-08-19
The result for the command: lsusb

Bus 005 Device 003: ID 04f2:b008 Chicony Electronics Co., Ltd 
....................

so it is usb...

---

### Post by ntlam on 2007-08-21
should I give up?????????????

---

### Post by ntlam on 2007-08-21
I just installed the spca5xx-source package. Now I can see myself by using Ekiga. I tried Kopete but there was just the green image.

What should I do to get it work with apps which support yahoo messenger?

---

### Post by Chemist2006 on 2007-09-04
Visit site [http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html)
In list you can find that chicony microchip is based on sn9c1xx chips driver.
You can download driver for sn9c1xx directly from here: [http://www.linux-projects.org/downlo...untu1_i386.deb](http://www.linux-projects.org/downlo...untu1_i386.deb)
This driver is written recently and actually it is new.
relative site is: [http://www.linux-projects.org/module....php?op=&cid=7](http://www.linux-projects.org/module....php?op=&cid=7)

---

### Post by ntlam on 2007-09-04
> **Chemist2006 said:**
> Visit site [http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html)
In list you can find that chicony microchip is based on sn9c1xx chips driver.
You can download driver for sn9c1xx directly from here: [http://www.linux-projects.org/downlo...untu1_i386.deb](http://www.linux-projects.org/downlo...untu1_i386.deb)
This driver is written recently and actually it is new.
relative site is: [http://www.linux-projects.org/module....php?op=&cid=7](http://www.linux-projects.org/module....php?op=&cid=7)

your last two links dont work.

---

### Post by Chemist2006 on 2007-09-06
try to find here 
[http://www.linux-projects.org/modules/mydownloads/viewcat.php?op=&cid=7](http://www.linux-projects.org/modules/mydownloads/viewcat.php?op=&cid=7)

[download]("http://www.linux-projects.org/modules/mydownloads/viewcat.php?op=&cid=7")

---

