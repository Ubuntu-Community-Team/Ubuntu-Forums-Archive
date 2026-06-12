---
title: "How to connect adsl modem on Ubuntu 9.10"
date: 2010-04-09
forum: Networking &amp; Wireless
---

### Post by anibch on 2010-04-09
I use an atom based processor of 1.60 ghz on intel d945gclf board. My ram is a zion 1gb @ 533mhz. Hdd is from western digital 80gb @ 7200 rpm. I have a broadband(dsl) connection from bsnl dataone (a state owned telecom service provider). I connect to internet via a huawei wa1003a ethernet/usb/wireless modem which is provided by my service provider. I need a username and a password everytime i connect to internet via dial-up.
I was using windows xp service pack ii. It was nice and easy installing my modem on xp either via usb or ethernet. Both ways it was easy as i have both the drivers with me.
Only and main problem was fighting viruses. I tried many free downloadable anti-virus software to protect my maching. Initially they were fine. But after few months they stopped taking regular updates and became non-functional. I also tried symantec corporate v.10. But it has its drawbacks also. It made my machine perform like a snail.
I had previously heard about linux based operating systems. But never tried one. As i am an ameteur in using computers windows xp was suiting my needs. Recently i saw an article in the newspaper about ubuntu which is a free open source operating system. And most important to me it is virus free.
But here is a problem also. I cannot connect to internet. My ubuntu 9.10 karmic koala is not identifying my modem and a network between my modem and my machine cannot be established. Also i cannot create a dial-up option where i can give username and password.
I searched on the internet through google a little but could not help myself.
Looking forward for some help.
Thanks

---

### Post by shaka_zulu on 2010-04-09
Are you connecting it to your computer with USB or ethernet?

---

### Post by dineshs on 2010-04-12
Connect your modem via ethernet.Configure DSL using NM
[https://help.ubuntu.com/community/NetworkManager0.7](https://help.ubuntu.com/community/NetworkManager0.7) 
Right-click on the nm-applet and then click on Edit Connections.
Select the tab,DSL and ADD
Give username and password
Select connect automatically and proceed

---

### Post by StefanSeo on 2010-04-12
There is bug in Network manager about dsl connection.
Use sudo pppoeconf instead.

---

