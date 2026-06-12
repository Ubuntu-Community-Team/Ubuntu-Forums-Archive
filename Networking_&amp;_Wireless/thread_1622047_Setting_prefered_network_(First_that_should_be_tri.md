---
title: "Setting prefered network (First that should be tried)"
date: 2010-11-15
forum: Networking &amp; Wireless
---

### Post by Mobidoy on 2010-11-15
I have a Dual Band Router home, 2.4 and 5 Ghz. I can connect to the 5 Ghz with my laptop so, as there are less interferences on the 5 than on the 2.4, I would like for Ubuntu to connect on it by default. Sadly, it always connect to the 2.4 first so, I got to change it manualy. 

Is there a way to set it so it will first try the 5 and if not available, go on the 2.4 ?

Thanx :)

---

### Post by rhhoek on 2010-11-18
I am struggling with the same problem. I haven't found the right answer. I have forced the wireless-card to use the 5GHz-band with the command:

sudo iwconfig wlan0 Channel 140

At the moment I am still connected with the AP over channel 132 (Frequency:5.66 GHz)

I hope there is a way to change the wireless behaviour so, that 5GHz-band is preferred over the 2.4GHz-band.

--

regards,

Roel

---

