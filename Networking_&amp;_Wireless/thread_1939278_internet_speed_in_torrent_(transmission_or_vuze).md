---
title: "internet speed in torrent (transmission or vuze)"
date: 2012-03-11
forum: Networking &amp; Wireless
---

### Post by dhrayofhope on 2012-03-11
I have a 512Kbps connection. when I was downloading by direct link i m getting  almost 60kbps avg speed.but when I was downloading through torrent it gives very less speed 10kbps approx.for same torrent at start it downloads @near about 60, but after that it stucked on 10 -15. and the speed also varies in different clients. in Vuze it around 20 and in transmission it's 50 for the same torrent. where as in windows at the same time it gives over 60. I have read about port forwarding in torrent - downloads, but hardly have some knowledge in that. Firstly I thought it was because of the net-connection, but it is not. and also the seeds are over 60 in that torrent, I have tested.

Please share me some info regarding port forwarding -- and how it is need in only torrent - downloads --- and not in direct link downloads. 

Thanks in Adv.

---

### Post by Vishal Agarwal on 2012-03-11
what is th output of your firewall

> 
sudo iptables -L -vn 
sudo iptables -t nat -L -vn


---

### Post by dhrayofhope on 2012-03-11
here is the output.

---

