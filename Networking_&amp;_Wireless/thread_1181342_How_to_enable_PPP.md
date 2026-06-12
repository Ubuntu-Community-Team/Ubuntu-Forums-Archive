---
title: "How to enable PPP ?"
date: 2009-06-07
forum: Networking &amp; Wireless
---

### Post by mikecanada on 2009-06-07
Using Ubuntu 9.04 with hardware internal dial up modem that won,t connect.

It says "ppp not enabled " at the end of the connection log and drops out.

How do I enable ppp ? I have googled this to avoid wasting peoples time to no avail,any help out here ?

Thanks Mike

---

### Post by superprash2003 on 2009-06-08
hope this helps [http://www.ubuntugeek.com/setting-up-dial-up-connection-in-ubuntu.html](http://www.ubuntugeek.com/setting-up-dial-up-connection-in-ubuntu.html)

---

### Post by mikecanada on 2009-06-08
Wonderfull, I will give it a try tonight.I find it strange that a borrowed air card works so easy and the dial up method which has been around forever is so darn difficult. Thanks Mike

---

### Post by mikecanada on 2009-06-13
Okay so I followed the link and did the pppconfig thing and then from the terminal did sudo gnome-ppp to bring up the dialer.The error messages how ever remains the same still " ppp not enabled" So I still need to enable ppp to finish the connection process.

Doe anyone have any more ideas please? Thanks Mike


link [http://www.ubuntugeek.com/setting-up-dial-up-connection-in-ubuntu.html](http://www.ubuntugeek.com/setting-up-dial-up-connection-in-ubuntu.html)

---

### Post by mikecanada on 2009-06-17
If I could log in as sudo could I open PPPD to enable the ppp ?

---

### Post by cariboo on 2009-06-17
You have to have the pppd daemon running before ppp will work.

---

### Post by mikecanada on 2009-06-17
Okay so what is involved to do that? Thanks

---

