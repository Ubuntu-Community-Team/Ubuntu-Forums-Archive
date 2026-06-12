---
title: "Setting Gateway"
date: 2011-05-16
forum: Networking &amp; Wireless
---

### Post by delphiguy on 2011-05-16
Cheers,

I have used ubuntu a few years ago, and I really loved it... Unfortunately I have to move back to
Windows 3 yrs ago (wife cant use Ubuntu), and have totally forgotten my way around Ubuntu.

I have downloaded Ubuntu 11.04 and frankly I love the new unity interface, but thats not the point
for this topic.  Anyways, I have 2 internet connection (isp_A and isp_B), and my Ubuntu box has 2 
network cards.

I've been trying to do a load balancer from this setup but my limited knowledge of linux has 
prevented me from doing so, so the next best thing is that I've set-up my connections as follows:
Isp_A=eth0, directly connected to the internet via modem.
Isp_B=eth1, connected via router, and has access to local network this is main internet 
connection used by the household.

This setup works great, however, not perfect... since the gateway seems to always default to ISP B,
and that I have to type in this command via terminal everytime I restart my machine.
route add default gw 192.168.1.1

Which is kinda tedious, and I cant figure out how to properly setup /etc/network/interfaces as I
always seems to mess it up.

I hope that someone here is kind enough to help me with this situation... thanks in advanced.

---

### Post by lz1dsb on 2011-05-16
Regarding the configuration of the /etc/network/interfaces I think that this is what you need:
[http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/](http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/)
It provides a wealth of information how to configure it.
 
 
Cheers,
Boyan

---

### Post by delphiguy on 2011-05-16
Thanks for the link, I'll look into this.

---

