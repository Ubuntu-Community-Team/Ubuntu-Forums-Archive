---
title: "yet another &quot;wireless works but ...&quot;"
date: 2006-06-14
forum: Networking &amp; Wireless
---

### Post by emperon on 2006-06-14
Hello, 
I am using an HP nx7010 laptop and my wireless connection works perfect except there's one thing I couldn't figure out.

Hp nx7010 has a button that can enable or disable wireless (and bluetooth) connection. Now that if wireless is turned on and then I boot into Ubuntu, everything works perfect but if wireless is turned off and I boot, this time although my connection is detected (the green bar is full at the top panel) but I can not ping my modem nor connect to internet. Only after deactivate and activate my connection , I am able to connect.

Any suggestions to fix this issue ?

---

### Post by ????? on 2006-06-14
What card are you using?


EDIT: hey, we have the same amount of beans! ;)

---

### Post by emperon on 2006-06-14
It's PRO/Wireless 2200BG

---

### Post by emperon on 2006-06-22
Alternatively this issue is fixed by **sudo ifconfig eth1 up**

But why do I have to write this when I turn on my connection? Why this is not necessary in windows ?

---

