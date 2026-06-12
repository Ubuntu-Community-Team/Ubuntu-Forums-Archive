---
title: "Unable to load http://192.168.1.1 in firefox"
date: 2011-07-08
forum: Networking &amp; Wireless
---

### Post by arroy_0209 on 2011-07-08
[SIZE=4]I have just switched from windows XP to ubuntu 10.04 LTS. To connect to net I use an ADSL modem.  I used these commands to set network connection:
sudo ifconfig eth0 19.168.1.2 netmask 255.255.255.0 up
sudo route add default gw 192.168.1.1 eth0
sudo route add default gw 192.168.1.1
sudo pppoeconf

After that I followed instructions as they appeared. The problem is since the I am unable to load the page [http://192.168.1.1](http://192.168.1.1) in mozilla firefox (which I could when I used windows XP). My aim is to check the status of ADSL modem while working. This is connected to my computer and my telephone by cable but if without my notice, the wireless option is enabled, then somebody close to my apartment may use this Internet connection and I will have to pay for that. How do I check this? Thanks.

[/SIZE]

---

### Post by haqking on 2011-07-08
> **arroy_0209 said:**
> [SIZE=4]I have just switched from windows XP to ubuntu 10.04 LTS. To connect to net I use an ADSL modem.  I used these commands to set network connection:
sudo ifconfig eth0 19.168.1.2 netmask 255.255.255.0 up
sudo route add default gw 192.168.1.1 eth0
sudo route add default gw 192.168.1.1
sudo pppoeconf

After that I followed instructions as they appeared. The problem is since the I am unable to load the page [http://192.168.1.1](http://192.168.1.1) in mozilla firefox (which I could when I used windows XP). My aim is to check the status of ADSL modem while working. This is connected to my computer and my telephone by cable but if without my notice, the wireless option is enabled, then somebody close to my apartment may use this Internet connection and I will have to pay for that. How do I check this? Thanks.

[/SIZE]
[FONT=Arial][SIZE=2]
well unless the above is a typo.

[/SIZE][/FONT][SIZE=4][FONT=Arial][SIZE=2][SIZE=4]19.168.1.2[/SIZE] [/SIZE][/FONT][FONT=Arial][SIZE=2]as your host address is on a different network, i am presuming you wanted it to be 192.168.1.2[/SIZE]
[/FONT]
[/SIZE]

---

### Post by headvampyre@hotmail.co.uk on 2011-07-08
Have you tried a different browser? And also try rebooting the router, i've found many routers will stop actually serving webpages for no apparent reason.

---

