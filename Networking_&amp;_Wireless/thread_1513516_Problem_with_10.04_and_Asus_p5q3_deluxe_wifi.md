---
title: "Problem with 10.04 and Asus p5q3 deluxe wifi"
date: 2010-06-19
forum: Networking &amp; Wireless
---

### Post by Ocular on 2010-06-19
I tried to follow along with this thread [http://ubuntuforums.org/showthread.php?t=1308436](http://ubuntuforums.org/showthread.php?t=1308436) but most of it's outdated and I could not complete his explanation. I have windows 7 on a different partition and it connects just fine, so does express gate which is linux. But for some reason ubuntu will only show the available networks and not connect :(

Intel e8200 2.66 overclocked to 3.1, P5Q3 Deluxe/WiFi-AP @n, 6 gb ram

---

### Post by telefono on 2010-09-27
same problem for me with ubuntu 10.04

---

### Post by gordintoronto on 2010-09-27
You can see the available networks? What do you do then?

---

### Post by Ocular on 2010-12-04
In Ubuntu 10.10 when I enter my destkop I connect and I am able to browse for a short period of time ( but very slow). Then I am booted off and I am unable to connect again, unless I restart my pc.

---

### Post by maxime3112 on 2010-12-12
I have the same problem than Ocular in Ubuntu 10.10 ... Need help please :)

---

### Post by chili555 on 2010-12-12
> **maxime3112 said:**
> I have the same problem than Ocular in Ubuntu 10.10 ... Need help please :)Let's see if you have the same device. Please post:```
lspci -nn
lsmod | grep rt2
```Thanks.

---

### Post by Mafiozosterror on 2010-12-21
Take a look here: [http://www.smachado.com/2010/11/how-to-make-ralink-rt2870-driver-work-on-ubuntu-10-10/](http://www.smachado.com/2010/11/how-to-make-ralink-rt2870-driver-work-on-ubuntu-10-10/)

 This saved me ;)

---

