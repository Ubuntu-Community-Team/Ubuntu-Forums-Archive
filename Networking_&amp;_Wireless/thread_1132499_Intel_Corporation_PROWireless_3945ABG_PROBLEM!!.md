---
title: "Intel Corporation PRO/Wireless 3945ABG PROBLEM!!"
date: 2009-04-21
forum: Networking &amp; Wireless
---

### Post by [vu] on 2009-04-21
Hi!
I have a problem with Intel Corporation PRO/Wireless 3945ABG (Dell inspiron 1525)
It works! but, when i'm connected to a wireless network and i try to visit a web, for example ubuntuforums.org, doesn't load completly, its like he drop the conection.
In fact i use conky and i can see the wireless network transfer and it's very low (max 4 kb/s and then it's null) and obviously the page doesn't load


The result of lspci is
```
 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

```

Does anybody how can i resolve this problem ?
Thanks

---

### Post by Ryuhayabusa on 2009-04-21
do you have an ip?

ifconfig

route

---

### Post by [vu] on 2009-04-21
Now i'm not connected but when i was, dhcp give me IP
I have to verify the route but i can connect to emesene (MSN client) and works well.

---

### Post by Ryuhayabusa on 2009-04-23
try typing in a terminal

sudo lshw -C network

and then

sudo iwconfig

maybe you have very poor signal strength?

---

### Post by [vu] on 2009-04-23
thanks Ryuhayabusa for the help !
But the signal strength was around 80 -100%
Anyway , searching in the forum, a lot of people have problems with iwl3945 (intel wireless driver).
So, i'm waiting to install jaunty and see what happend.

Anyway , thanks for the support :D

---

### Post by chili555 on 2009-04-23
I just don't understand. You posted on this forum expecting help. An attentive and helpful person, Ryuhayabusa, has requested additional details twice in order to know what to suggest to help you. In neither case did you provide one detail. So how is Ryuhayabusa or anyone else supposed to help? You said:> a lot of people have problems with iwl3945 (intel wireless driver).Mine works perfectly, and has on every version of Ubuntu back to 6.04.

---

