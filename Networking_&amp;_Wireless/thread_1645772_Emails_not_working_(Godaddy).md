---
title: "Emails not working (Godaddy)"
date: 2010-12-15
forum: Networking &amp; Wireless
---

### Post by savramesh on 2010-12-15
Everything was fine till yesterday night. I am using evolution.

Now my official emails hosted in email.secureserver.net are not working, no incoming mails and outgoing mails. My system is connected to internet through a network. Gmails are still working, i tried browsing email.secureserver.net and its not loading too.. godaddy site is also not loading. rest all sites are working fine. 

btw I just tried Tata photon + internet, and all emails seems to be working fine.. 

Why it is not working through lan internet ?

---

### Post by savramesh on 2010-12-15
it seems to be automatically resolved and working fine now..

---

### Post by StuartinFiji on 2010-12-22
I have just spent 2 hours working thru this as I REALLY wanted to give Evolution a go (Thbd is just getting too heavy IMO).

Anyway after a lot of trial and error, here is my final solution for Evolution and GoDaddy

**Incoming/Receiving Email**
Server: pop.secureserver.net:995
Security: SSL Encrytion
Authorization type: Login
[B]
Sending Email SMTP[/B]
Server Configuration: smtpout.secureserver.net:465
Security: SSL Encryption
Authentication type: Login

Works 100% of time now! :D

---

### Post by savramesh on 2010-12-22
@Staurt

Thanks for the info. Apart from connectivity issue, Evolution freezes sometimes. So i switched to Thunderbird, managed to transfer mails from evolution to thunderbird. Thuderbird is cool and smarter than evolution.

---

### Post by savramesh on 2010-12-26
The problem is back again. 

I checked the incoming and outgoing server settings, it is same as Stuart quoted above.

Gmail pop and smtp is working fine.


[IMG]http://lh3.ggpht.com/_ED7WPlYUL48/TRgNqUQtYJI/AAAAAAAAFs8/JwqPIbWfNA0/Screenshot-1.png[/IMG]

[IMG]http://lh5.ggpht.com/_ED7WPlYUL48/TRgNqfiTJtI/AAAAAAAAFtA/8YXg53OaUQc/Screenshot.png[/IMG]

[IMG]http://lh3.ggpht.com/_ED7WPlYUL48/TRgOkVeVRCI/AAAAAAAAFtI/PsD9kQhkhRg/Screenshot-3.png[/IMG]

[IMG]http://lh3.ggpht.com/_ED7WPlYUL48/TRgOkdZhRxI/AAAAAAAAFtM/w5P6Kvboo9E/Screenshot-2.png[/IMG]

---

