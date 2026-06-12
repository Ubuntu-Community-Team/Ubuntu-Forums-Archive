---
title: "Can't open many websites"
date: 2013-09-03
forum: Networking &amp; Wireless
---

### Post by liquidstone on 2013-09-03
I'm using DSL connection (PPPoE) with Network Manager, and when i try to open some websites like: opera.com, speedtest.net, imgur.com it won't open at all. That's only when i use the Network Manager. But when i make use pppoeconf to make connection, no problems. It seems that the problem is in Network Manager. 
I even made a video: [https://www.youtube.com/watch?v=h1PIs_QXLKs](https://www.youtube.com/watch?v=h1PIs_QXLKs)

---

### Post by houstonbofh on 2013-09-03
This is most likely a MTU issue.  If you manually set the MTU to something lower, it may fix it.

---

### Post by liquidstone on 2013-09-03
How to change the MTU manually, i tried in the dsl settings it won't work. ifconfig shows me different MTU

---

### Post by liquidstone on 2013-09-03
solved: nano /etc/NetworkManager/system-connections//DSL\ connection\ 1 and changed it there. MTU changing in Network manager is broken, bug

---

### Post by houstonbofh on 2013-09-04
If it now works, please mark your thread as solved.

---

### Post by itsankur on 2014-01-12
Hi 
I'm also having exactly the same problem. But could not understand what you did with MTU.
Please help.

---

### Post by houstonbofh on 2014-01-13
Did you look at the file he mentioned above?

---

