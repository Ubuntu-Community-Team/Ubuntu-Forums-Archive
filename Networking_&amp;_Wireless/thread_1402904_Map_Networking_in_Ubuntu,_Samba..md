---
title: "Map Networking in Ubuntu, Samba."
date: 2010-02-09
forum: Networking &amp; Wireless
---

### Post by EizoSiege on 2010-02-09
Hi, I have Ubuntu on one of my laptops. Whenever I want to watch some movies, I use ALT+F2 and then: "smb://computername/movies". Now there will appear an icon on the desktop so that I can just press that icon to come back to that folder easily. What I'm wondering is if I can make it sutch that everytime I restart the computer it is on the desktop? So that I don't have to type in the thing everytime.



Charlie.

---

### Post by Iowan on 2010-02-09
[Here]("http://ubuntuforums.org/showthread.php?t=288534") is a How-To for mounting CIFS shares.

---

### Post by johnson.d on 2010-02-11
You can make the samba mount permanent by adding the following line to the /etc/fstab file

//<server>/<share> /<mount point> cifs user=<username>,password=<password> 0 0

---

