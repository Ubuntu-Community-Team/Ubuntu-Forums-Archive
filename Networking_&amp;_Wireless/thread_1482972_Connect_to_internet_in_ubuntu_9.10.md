---
title: "Connect to internet in ubuntu 9.10"
date: 2010-05-14
forum: Networking &amp; Wireless
---

### Post by chankey on 2010-05-14
Hi guys!

I have sony-vaio laptop. It comes with window 7. I installed ubuntu 9.10 in it. I am not able to use internet services in it. I tried **ifconfig** and it is not showing the eth device. It is only showing **lo**. I think the eth service is off. How to turn it on? 

Also I want to know that will my laptop support Redhat / fedora?
Can I install them in my laptop?

Laptop configuration: 
Sony vaio - E series
Intel core i-3 2.13 ghz
RAM- 3 GB
HDD- 320 GB

---

### Post by K.Mandla on 2010-05-14
Moved to Networking and Wireless.

---

### Post by kimberlite on 2010-05-14
Try ```
ifconfig -a
``` in a terminal window. If you see "eth0", you should issue: ```
ifup eth0
``` Also you may want to have a look at:
[http://ubuntuforums.org/showthread.php?t=327417]("http://ubuntuforums.org/showthread.php?t=327417")

---

### Post by Iowan on 2010-05-14
**lshw -C network** will show more information about your networking interfaces - including alias and driver.

---

