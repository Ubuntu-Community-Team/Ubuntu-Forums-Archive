---
title: "no internet connection ubuntu 8.4 hardy"
date: 2009-07-04
forum: Networking &amp; Wireless
---

### Post by ismoke101 on 2009-07-04
good day. im getting a hard time in connecting my computer to the internet. I installed ubuntu 8.4 to give it a try, but after the installation, my internet connection is not working at all. even if i restart my router, the network icon is not animating as it will use to be when detecting a connection, i cant upgrade my system at all. pls any help? here are the setting on my network setting:

[IMG]http://i152.photobucket.com/albums/s162/ismoke101/blog/Screenshot-NetworkSettings.png[/IMG]

[IMG]http://i152.photobucket.com/albums/s162/ismoke101/blog/Screenshot-NetworkSettings-1.png[/IMG]

[IMG]http://i152.photobucket.com/albums/s162/ismoke101/blog/Screenshot-NetworkSettings-2.png[/IMG]

[IMG]http://i152.photobucket.com/albums/s162/ismoke101/blog/Screenshot-NetworkSettings-3.png[/IMG]

---

### Post by HereInOz on 2009-07-04
Are you able to ping an external IP address such as 74.125.67.100

If you can, then it is a DNS issue.

---

### Post by superprash2003 on 2009-07-04
post output of **ifconfig **from the ubuntu terminal

---

### Post by Iowan on 2009-07-04
**ifconfig** (as mentioned above) will show if your machine is getting an IP address. If not, then the results of **lshw -C network** might be helpful.

---

### Post by RedSingularity on 2009-07-04
Is this a wired connection?

---

### Post by ismoke101 on 2009-07-08
hi again: sorry for the late reply, ahhm, its kinda weird, but my internet just suddenly goes online, but for only about 5 mins. and while im downloading some updates, it just stop, and my mouse just stop working. when i restart, it took me more or less 5 min before completely restart. hmmm here is my ifconfig: i attach it together with the lsh -c network

---

### Post by ismoke101 on 2009-07-10
sorry but i think the issue was that my Internet provider disable different pc using same router and even prolong torrent. thanks anyway so much

---

