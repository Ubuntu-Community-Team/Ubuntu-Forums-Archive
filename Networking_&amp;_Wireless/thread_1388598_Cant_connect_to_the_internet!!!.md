---
title: "Cant connect to the internet!!!"
date: 2010-01-23
forum: Networking &amp; Wireless
---

### Post by furqanbhai on 2010-01-23
Hi guys,



I recently upgraded Ubuntu 9.10 from 9.04 but I was unable to connect to the internet. I have a ppp connection and I used to make a DSL connection and then give the command 'sudo pon ppp0' and the net got connected but in Karmic Koala it just doesnt click. I switched back to 8.04 and its working fine with 'Roaming mode enabled'. There is no problem with my connection. And also if it gave some problems then I used to delete all the connections I made and then reboot and then 9.04 would make a connection by itself but 9.10 doesnt. I installed 9.10 within windows using wubi. Please help as to how should I connect to internet in 9.10? I am attaching the ppp0 file so u may suggest the right connection for me if I am wrong.





noipdefault
defaultroute
replacedefaultroute
hide-password
persist
usepeerdns

plugin rp-pppoe.so eth0
user "sfurqan"

---

### Post by asearle on 2010-01-23
Are you able to ping any sites?  e.g. 

ping [www.google.com](www.google.com)

Regards,
Alan

---

### Post by furqanbhai on 2010-01-23
I did that.... I mean, I tried opening google.com but didnt worked out.... should I copy ppp0 file of 8.04 to 9.10 /etc/ppp/peers/ ????? what do u say?

---

### Post by asearle on 2010-01-23
did you type 

ping [www.google.com](www.google.com) 

into a terminal.  That should tell you if you are receiving data from outside.

Or did you try from the browser?

Testing from a terminal window is a better indication.

---

### Post by furqanbhai on 2010-01-23
I tried opening it from browser. But the icon was flashing that Wired Connection is disconnected.

---

