---
title: "HP Pavillion Network Problem"
date: 2009-05-14
forum: Networking &amp; Wireless
---

### Post by bayvista on 2009-05-14
My HP Pavillion has an Ethernet Port and a WiFi Port. I can connect to my Router  and the Internet via WiFi. If I switch WiFi off and try to connect via Ethernet, I cannot get to the Internet. However, I can ping the Router and my Desktop. I can SSH to my Desktop. It's only the Internet that I can't get working. Any ideas?

---

### Post by superprash2003 on 2009-05-14
post output of ifconfig from the terminal. try bringing down the wifi interface and then connecting

---

### Post by Iowan on 2009-05-14
Might check */etc/resolv.conf*. Kinda sounds like DNS problem.

---

### Post by bayvista on 2009-05-15
Have attached resolv.conf and ifconfig output from the Laptop with both Ethernet and WiFi connected.

---

### Post by superprash2003 on 2009-05-15
i dont think you've attached the resolv.conf output.. i feel Iowan is right , it could be a DNS issue , as your eth1 is set to static and wlan0 is DHCP, so when wifi is off , eth1 isnt get DNS info from router as its set to static.. 
  to confirm this , when wifi is disconnected and only wired is connected try opening [http://74.125.45.100](http://74.125.45.100) . does google open?

---

