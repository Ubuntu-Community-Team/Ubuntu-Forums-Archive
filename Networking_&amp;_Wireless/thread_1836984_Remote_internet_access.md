---
title: "Remote internet access"
date: 2011-09-01
forum: Networking &amp; Wireless
---

### Post by b1tchacked on 2011-09-01
In our institute we have a lab with 24hr inter-net access and in the hostel room we r cut in the morning and all our connections are on the same LAN, is there any way i can access the internet in my lab from my room other than remote desktop access...

And we have unique ip addresses for both our rooms and lab connections..
We use a proxy server with an username/password authenciation....

I am not well aware of the terms i used sorry if i have made some mistakes...Please ask me back questions if i have not made my question clear..

---

### Post by northd_tech on 2011-09-01
Well assuming these are **all** cabled Ethernet connections, depending upon whether you have **sudo** / root access on a Linux machine in the Lab, I think you might just need to use Internet Connection Sharing on a Linux machine in the Lab.  I doubt that someone comes in and disconnects all the ethernet cables and/or powers down the ethernet switches/routers each morning- it is probably a **cron** job (or something similar) that cuts the hostel/dorm Internet access every morning.  It is probably either killing a DHCP server or blocking a "block" of IP addresses for the hostel/dorm (probably to "persuade" the students to go to class each morning rather than Facebook and surf for porn all day :o ).

If you are a student, you might want to read [COLOR=Red]**all the fine print **[/COLOR]on the internet access agreement and/or the Student Handbook/Constitution (or whatever applies)- you could possibly/probably get expelled (or worse) for messing with the network at a school/university.

All that said, here's a link about Internet Connection Sharing;

[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

[http://www.ubuntugeek.com/sharing-internet-connection-in-ubuntu.html](http://www.ubuntugeek.com/sharing-internet-connection-in-ubuntu.html)

---

### Post by b1tchacked on 2011-09-01
A hell lot of thanks for the advice and i will go through  that two links in detail find out how far has that helped me out :)

---

