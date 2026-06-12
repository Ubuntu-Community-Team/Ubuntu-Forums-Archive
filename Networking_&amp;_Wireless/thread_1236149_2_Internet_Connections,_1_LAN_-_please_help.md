---
title: "2 Internet Connections, 1 LAN - please help"
date: 2009-08-10
forum: Networking &amp; Wireless
---

### Post by sohan on 2009-08-10
Hi all,

I've googled but didnt find a correct solution for my issue.

I've 2 Internet Connections and want to use both connections at the same time to 1 LAN.

Present status is, I am using only one ISP with Ubuntu server(Iptables+Squid,Transparent). The other ISP is idle now and I want to use it too to boost up the Speed! Any please help me how can I use both Internet connections at the same time.

Present Connection details: 
eth0 : 192.168.1.1 ( ISP1)
eth1 : 192.168.0.1 (LAN)

Configured using with the help of [http://www.cyberciti.biz/tips/linux-setup-transparent-proxy-squid-howto.html](http://www.cyberciti.biz/tips/linux-setup-transparent-proxy-squid-howto.html)

I'll add another NIC and connect it to ISP2, but donno how to combine both connections to use. 

ISP1(1Mbps) + ISP2(1Mbps) = 2Mbps! Is it possible ?

Thank you all for your help!

Sohan

---

### Post by sohan on 2009-08-12
:( no replies

---

### Post by Iowan on 2009-08-12
I've seen a few topics on bridging or bonding two interfaces... [this]("https://help.ubuntu.com/community/UbuntuLTSP/Trunking") one seems like what you're trying.

---

