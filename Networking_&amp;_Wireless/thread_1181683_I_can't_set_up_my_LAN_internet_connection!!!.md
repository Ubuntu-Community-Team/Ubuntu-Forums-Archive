---
title: "I can't set up my LAN internet connection!!!"
date: 2009-06-08
forum: Networking &amp; Wireless
---

### Post by pan4o16 on 2009-06-08
Hi all :)
I am new user of Ubuntu so if you gonna help me keep that in mind :) ok last night i instal Ubuntu so now i need internet! But when I make a new internet profil (with my MAC,IP and all) ubuntu autocreates new profil "Autoenthnet" or something like that and use it insteath of my correct internet profil. If I try to delete that autoprofil it is just recreating again. It will be great if you give me some  kind of step by step manual :)

---

### Post by pan4o16 on 2009-06-08
BTW every time i try to chande the autocreated profile to correct one it just create another profil and stop using the old CORRECT one :( PLS HELP ME!!!!

---

### Post by superprash2003 on 2009-06-08
do you need to specify a static ip? if so use the auto eth0 , dont create a new one..

---

### Post by Iowan on 2009-06-08
I was having trouble getting DHCP to work, so I built a connection (called it static eth0).  After "auto eth0" failed, it would run/succeed with "static eth0".  If you have another configuration you'd rather run than "auto eth0" (and/or don't want to edit "auto eth0"), you can probably uncheck the "connect automatically" box for "auto eth0" connection (and make sure your connection has it checked).
After I got DHCP working again, I renamed my static configuration "manual eth0" and unchecked the "connect automatically" box.  If DHCP fails again, I can still connect - but I must manually select the connection.

---

### Post by terrrorr on 2009-06-08
Could you please send more information about your internet connection. Here is couple questions which will help us quite lot:

1. Does your Internet connection work in other computers
2. Is it LAN-type of connection (allways on) or do you need to open it before it is possible start surfing (PPPoE client)
3. Do you need to use static IP's which are provided by your ISP.

Post also results of this command (Run it in your terminal (Applications -> Terminal))

```
sudo ifconfig
```

---

### Post by brabo on 2009-06-08
good idea terrrorr!

maybe the OP can also post the results of:

cat /etc/network/interfaces

grtz!
brabo.

---

