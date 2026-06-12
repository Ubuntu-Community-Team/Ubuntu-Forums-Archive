---
title: "macbook pro install ubuntu12.10 wireless network doesn't work"
date: 2012-11-09
forum: Networking &amp; Wireless
---

### Post by sjtuEric on 2012-11-09
Hello&#65292;everyone&#12290;
my laptop is macbook pro,this week,I try to isntall ubuntu 12.10.Unluckyly,wireless network dones't work.Here is the detials:
I went to the website of broadcom and downloaded corresponding wireless driver,and after make instruction&#65292;I get ml.ko,then modprobe wl.Then I input lsmod and see wl in the list.Howere,when I input iwconfig,I can't find my wireless network card eth1.
Please help me,thank you !!!

---

### Post by wilkenw on 2013-02-06
The problem has been solved.  Be certain to install the latest version of Virtualbox (4.2.6) and wireless on the MacBook Pro will work with no problems whatsoever.  I installed 4.2.6 this morning and wireless that wouldn't work yesterday works like a champ.  Didn't have to touch any configuration variables.

---

