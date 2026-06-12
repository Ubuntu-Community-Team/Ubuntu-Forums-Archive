---
title: "how to connect with second vpn connection"
date: 2011-03-07
forum: Networking &amp; Wireless
---

### Post by sa_ostad on 2011-03-07
i connect with one vpn connection to Internet and I want to connect to other network with second vpn connection for tunnelling and my works but when I connect with first connection other vpn connections be disable !
i can do this very easy in windows xp or 7 !
how can i solve this problem ?

---

### Post by sa_ostad on 2011-03-09
I find solution in Persian forum [http://forum.ubuntu.ir/index.php/topic,17304.0.html:](http://forum.ubuntu.ir/index.php/topic,17304.0.html:)
for start second vpn:
sudo pptpsetup --create [name] --sever [ip] --username [username] --password [password] 
sudo pon [name]
ifconfig
sudo route del default
sudo route add default ppp1


for come back:
sudo route del default
sudo route add default ppp0

for shut down connection:
sudo poff [name]

if you want use from Ethernet card use eth0 substitute ppp0.
you can use ifconfig command to complete your information.

---

