---
title: "Monitor network speed and traffic"
date: 2013-06-11
forum: Networking &amp; Wireless
---

### Post by oygle on 2013-06-11
I installed netspeed , but as it's for GNOME, I guess it won't work under Kubuntu.   :(

Is there a package to show me the upload and download speed, current and historical ?

I'm running 12.04, and can't seem to work out how to install netspeed. Would **nload** be better than netspeed ?

I do have wireshark installed, but that level of monitoring is not required.

Oygle

---

### Post by Cheesemill on 2013-06-12
I use vnstat, it can give you daily, weekly and monthly totals and averages plus much more.

---

### Post by rrich1974 on 2013-06-12
vnstat is a real damn good tool. read the "man vnstat' to learn how to use it. it is a command CLI app.

---

### Post by oygle on 2013-06-12
Thanks for advising about vnstat. I have installed it, and set it up as per [How to Monitor and Log Network Traffic on Linux Using vnStat]("http://www.thegeekstuff.com/2011/11/vnstat-network-traffic-monitor/")

I hope that documentation is okay. It does seem to be monitoring received and sent, plus the speed.  :)

---

### Post by Cheesemill on 2013-06-12
If you followed the documentation that you linked to then adding 'vnstatd -d' to rc.local isn't needed. Installing vnstat using apt-get automatically sets the vnstat daemon to start at boot.

---

### Post by oygle on 2013-06-13
Okay thanks. I won't worry about adding it to /etc/rc.local (empty anyway)

---

