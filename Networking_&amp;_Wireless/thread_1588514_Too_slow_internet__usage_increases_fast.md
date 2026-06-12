---
title: "Too slow internet / usage increases fast"
date: 2010-10-05
forum: Networking &amp; Wireless
---

### Post by Edhas on 2010-10-05
Hi,

  For the last couple of days, my net connection in Ubuntu 10 LTS has become very slow. Chrome/Firefox are taking approx 3mins to load google.com. Some days back, it shows normal updates were required (181 mb approx) and I clicked the update button and next day onward it started.

  Also, in the system monitor, continuously the incoming and outgoing bytes are increasing. If you surf 3-4 normal websites (minimal or zero graphics), my usage is showing 10mb approx. 

  So I installed a new win xp (with no audio/ graphics/ antivir) partition and is surfing net from that. Here after loading the pages, the incoming and outgoing bytes are not increasing. 

  Please assist to solve the issue. Ubuntu is my favorite OS, however to cut my internet bills, i'm in xp temporarily. I cant understand what happened. I also disabled the ipv6 and auto updates after google search. Im using DSL connection and normally use sudo pppoeconf to connect. I installed firestarter too and it was showing, both the eth0 and ppp0 were increasing (bytes). Something is eating up my bandwidth.

---

### Post by NightwishFan on 2010-10-05
Try using a traceroute to see why it is taking so long.
```
traceroute google.com
```

---

### Post by Edhas on 2010-10-05
I did tracert under win xp and ubuntu both for google.com
in xp it was showing 7 steps and in ubuntu its showing 11 steps.

---

### Post by robert_pectol on 2010-10-05
The ***tcpdump*** utility comes in handy for viewing network traffic.  Perhaps that can give you some clues.  You may need to do, "sudo apt-get install tcpdump" in a terminal if you don't already have it installed.

---

### Post by Edhas on 2010-10-05
Hi,

  I checked by closing chrome/firefox. However the incoming and outgoing bytes kept on increaning. They were not becoming static or not showing as 0kib/s. I cheked for more than 5-6 mins after closing the browsers. Are there any ways (or firewalls), such that i can grant net access to some particular websites. For my studies, i need to remain connected and in ubuntu the usage is increasing too fast.

---

### Post by Edhas on 2010-10-05
Hi All,

  Any ideas friends on how to solve the issue....

---

