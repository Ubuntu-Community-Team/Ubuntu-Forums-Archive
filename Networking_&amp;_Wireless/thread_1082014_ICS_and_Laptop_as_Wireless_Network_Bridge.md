---
title: "ICS and Laptop as Wireless Network Bridge"
date: 2009-02-27
forum: Networking &amp; Wireless
---

### Post by dBLiSS on 2009-02-27
I have my wireless router and cable modem setup in another room and I have a room with a bunch of wired gear connected to another router. I am using old linux laptop picking up the the wireless internet signal and its ethernet port is connected to the uplink port of the other router to give connectiviy to all the gear that doesn't have a wireless ethernet connection. 

cable modem->wireless router->
 ..WIRELESS.. >-laptop->router2->desktop

This works great, but I have one issue that I hope someone can help me with. I have another laptop that connect to my network with via the wireless router, but I can not SSH or VNC into my desktop because all i can access from the wireless router is the IP of the laptop. Is there anyway the two routers can use the same IP range so i can access devices on both routers when connceted to the wireless?

Thanks!

---

### Post by superprash2003 on 2009-02-27
yes.. you could manually change the ranges of the routers.. and pcs..
say wifi router has dhcp from 192.168.1.2 - 192.168.1.10 and laptop gets ip as 192.168.1.5 .. on the other interface of laptop set ip as 192.168.1.11 and .. set router2 ip to 192.168.1.20 .. and set its dhcp range from 192.168.1.21 - 192.168.1.30 .. so desktop would get something like 192.168.1.25 .. hence they would be in the same 192.168.1.x range!!

---

