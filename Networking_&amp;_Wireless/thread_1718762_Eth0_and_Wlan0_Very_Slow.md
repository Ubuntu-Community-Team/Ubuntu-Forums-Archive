---
title: "Eth0 and Wlan0 Very Slow"
date: 2011-03-31
forum: Networking &amp; Wireless
---

### Post by rowbird on 2011-03-31
Hi all, I ran this series of commands trying to get an external wireless dongle working, and now have very slow networking on eth0 and wlan0:

sudo ifconfig wlan0 down
sudo ifconfig wlan1 up
sudo iwconfig wlan1 essid WIRELESS 
sudo dhclient wlan1

I am in real trouble now, as my networking is totally ruined. Any help would be appreciated. I am using 10.10, and older kernels behave the same. Thanks in advance

---

### Post by Majid7 on 2011-04-01
Hi.
Did you try to reset what you have done?
is it the problem?

---

### Post by rowbird on 2011-04-01
I have tried to reset, but I don't know how. I am getting connected now, but it is intermittently fast, then slow again. I would like to check some logs but I don't know which one.

---

### Post by rowbird on 2011-04-01
I think my DNS resolving is to blame. For example, it takes forever to get to speedtest.net but it will get 2.87 Mbps connection speed. I don't know what to do about it though. My router is providing the dns service, but my other computers on my home network are functioning fine.

---

