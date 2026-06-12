---
title: "Wireless network - picking up wrong ip number"
date: 2009-12-05
forum: Networking &amp; Wireless
---

### Post by watso on 2009-12-05
Hi I am a totally new to Linux (using Ubuntu 9.10) and have just installed it on an old laptop to try it out.
So far I am very impressed but I cannot seem to connect to my wireless network.
The Network manager seems to find the wireless network fine but I cannot connect to the internet. On checking the settings I noticed that it has not picked up a valid IP number from my router (running DHCP on a 192.168...) but has instead picked up something in the 10.42.43...range? 
Really not sure what the configuration steps are for a wireless network using Linux

---

### Post by Fast_Wyvern on 2009-12-05
Right click on the network icon  in the header bar, edit connections. Select the wireless connection and edit. You can set you IP address under IPv4 tab, set to Manual if you aren't getting DHCP from the router.

---

### Post by chili555 on 2009-12-05
> it has not picked up a valid IP number from my router (running DHCP on a 192.168...) but has instead picked up something in the 10.42.43...range?Has it connected to your neighbor's network?

---

### Post by watso on 2009-12-05
I have already tried setting the IP address manually and the network imediately disconnected. Also pretty sure I am not connecting to a neighbours router as I am using WPA-PSK and I am asked for the password before it connects. I have three other PC's in the house that are all connecting using 192.168... addresses. I have added the mac address to the router to ensure that it has access rights? 
Frankly I can't make sense of where it is picking up the 10.42.43... address from.

---

