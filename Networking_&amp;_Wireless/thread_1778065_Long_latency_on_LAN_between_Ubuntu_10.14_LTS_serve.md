---
title: "Long latency on LAN between Ubuntu 10.14 LTS servers"
date: 2011-06-08
forum: Networking &amp; Wireless
---

### Post by jakubmaler on 2011-06-08
Hi, we are setuping high-performance web farm with 4 ubuntu servers (all 10.14 LTS 64bit, i5Core CPU, 16GB Ram). One server is "database" server with mysql installed, three servers are "webservers" with tomcat installed. All three webservers have public IP and are connected directly to internet by eth0 (onboard network card) and are connected to switch that is connected to database server by eth1 (pci network card). All servers has stardard instalation with no special modules/programes installed.

Web servers are already under load, but only on about 10 requests/minute. After several hours in production, strange thing happened - one of the web servers (each time another one, so it is happening to all of them but not at once) starts to have pings to database (that is connected directly on LAN) = 100ms (other two servers still has like 0,02ms). Pings stay high until we do /etc/init.d/networking restart, after that it is fixed and pins are again low again. Another strange think is, that when we let ping running for some time, it is slowly dropping from 100ms to 1 ms and then again jumps to 100ms (exactly to 100ms always) and again starts dropping - so it is cycling over and over again (one cycle takes about 2 minutes).

We were trying reconfigure network, play with switch (the same situation was happening even without switch when there was only one webserver and one database server directly connected), disable IPv6 but nothing helped. The only thing that we discovered is that it has to be caused by network configuration.

Do you have any idea what can cause it? We went through systems logs but found nothing suspicious (at least according to our understanding).

Thanks a lot, Jakub

---

### Post by jakubmaler on 2011-06-08
Additional information:
we are using network card from this motherboard as eth0 : MSI P67A-C45 (B3)
we are using this network card as eth1 : D-Link DGE-528T 10/100/1000Mb/s Gigabit Ethernet, PCI

+ Correction: server system is Ubuntu LTS 10.04  (not 10.14 as i wrote in my previous post - that version does not exist)

---

### Post by dirty_harry on 2011-06-08
monitoring network/database:


[LIST]
[*]for mysql: **mytop; innotop**
[*]for network: **iptraf; ntop**
[/LIST]

I have no real experience troubleshooting a database-server. And I found it difficult to understand your setup; maybe "dia" would be helpful here?!
I would double check server-hardware, network, settings etcetera.

---

### Post by jakubmaler on 2011-06-09
We find out, that problem is most probably connected with USB 3.0 which is on motherboard and probably is not supported by installed kernel - update to latest kernel version seems that solved the problem

---

