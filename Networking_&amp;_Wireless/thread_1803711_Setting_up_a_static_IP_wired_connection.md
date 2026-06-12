---
title: "Setting up a static IP wired connection"
date: 2011-07-13
forum: Networking &amp; Wireless
---

### Post by ljcrabs on 2011-07-13
Hey, I'm trying to set up my internet, which is an ethernet cable going directly into a cable modem (ubuntu 10.4).

The information I have from my ISP is:
* a static IP address
* subnet mask: 255.255.255.0
* default gateway: static IP, ending in .1
* DNS primary & secondary servers
* Modem IP: 192.168.100.1 (all it has is a checkbox for DHCP)

Now in windows XP I would just fill out this box:
[http://www.kollewin.com/EX/09-16-17/tcp_ip_config.gif](http://www.kollewin.com/EX/09-16-17/tcp_ip_config.gif)

So I filled out this in ubuntu:
[http://i40.tinypic.com/23mmoi1.png](http://i40.tinypic.com/23mmoi1.png) (example pic only)

with 
Method = Manual
Address = static IP
Netmask = subnet mask
Gateway = default gateway
DNS = DNS
Search Domains = left blank


But I can't seem to get it going. The little network monitor tool with Ping, Lookup, Finger etc. shows the connection sending and receiving a few KiB every minute, and says it is connected but when I try pinging anything or Firefox it just times out. I have tried restarting but the settings get wiped.

Any help appreciated.

---

### Post by chili555 on 2011-07-13
> The information I have from my ISP is:
* a static IP address
* subnet mask: 255.255.255.0
* default gateway: static IP, ending in .1
* DNS primary & secondary servers
* Modem IP: 192.168.100.1 (all it has is a checkbox for DHCP)So you have a modem from your ISP that has the address 192.168.100.1 and the modem hooks to the ISP and the other end of the modem has an ethernet jack that connects to your Ubuntu computer? And does the modem get a DHCP address like 84.125.whatever.whoever from the ISP?

Then I assume the Ubuntu computer attached to the modem is supposed to be 192.168.100.something?

I appreciate that you are trying to obscure personally identifiable details, and you should. However, the exact nature of some of these numbers is crucial. As well, half the modems and routers in the world have 192.168.x.y addresses, including mine!

Please help me understand more.

---

