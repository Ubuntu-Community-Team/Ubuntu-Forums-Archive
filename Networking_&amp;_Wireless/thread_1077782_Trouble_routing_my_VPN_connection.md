---
title: "Trouble routing my VPN connection"
date: 2009-02-22
forum: Networking &amp; Wireless
---

### Post by Dave_N on 2009-02-22
Hi, 

I am running ubuntu 8.10. I have successfully connected to my workplace via a pptp VPN. I cannot understand exactly how to set up the routing options so that I do not route via the VPN by default. I am new to ubuntu and I have found the tracepath and network tools command. 

My work vpn server is availble at a public ip address. When I connect I have several 172.x.x.x networks and other 192.10x.x.x networks available. 
Essentially, I would like my home network 192.168.1.1 to stay local, 0.0.0.0 (the internet) to go via my wireless router and not over the internet. Microsoft clients have a checkbox for this. 

Tracepath info:
Here is without the VPN:

@ubuntu8600:~$ tracepath ubuntu.com
 1:  ubuntu8600.local (192.168.1.5)                         0.154ms pmtu 1500
 1:  wirelessrouter (192.168.1.1)                          14.363ms 
 1:  wirelessrouter (192.168.1.1)                          15.322ms 
 2:  no reply
 3:  no reply
 4:  no reply
 5:  no reply
 6:  be-50-ar01.elmhurst.il.chicago.comcast.net (68.87.230.45)  27.343ms 
 7:  pos-0-1-0-0-ar01.area4.il.chicago.comcast.net (68.87.230.237)  44.011ms 
 8:  pos-0-6-0-0-cr01.chicago.il.ibone.comcast.net (68.86.90.53)  56.811ms asymm 10 
 9:  xe-9-0-0.edge1.Chicago2.Level3.net (4.71.248.33)      53.335ms asymm 12 
10:  vlan51.ebr1.Chicago2.Level3.net (4.69.138.158)        59.990ms asymm 12 
11:  ae-6.ebr1.Chicago1.Level3.net (4.69.140.189)          67.022ms asymm 13 
12:  ae-2.ebr2.NewYork1.Level3.net (4.69.132.66)           68.706ms asymm 14 
13:  ae-72-72.csw2.NewYork1.Level3.net (4.69.134.86)       71.793ms 
14:  ae-71-71.ebr1.NewYork1.Level3.net (4.69.134.69)       62.721ms 
15:  ae-41-41.ebr2.London1.Level3.net (4.69.137.65)       135.130ms 
16:  ae-1-100.ebr1.London1.Level3.net (4.69.132.117)      131.613ms 
17:  no reply
18:  ae-26-52.car2.London2.Level3.net (4.68.117.48)       150.202ms 
19:  195.50.121.2 (195.50.121.2)                          135.008ms 
20:  gw0-0-gr.canonical.com (91.189.88.10)                140.377ms asymm 21 
21:  no reply
22:  no reply

Here is with the VPN:-
ubuntu8600:~$ tracepath ubuntu.com
 1:  172.25.109.213 (172.25.109.213)                        0.273ms pmtu 1396
 1:  no reply
 2:  172.25.109.1 (172.25.109.1)                          102.490ms 
 3:  ingate._REAL_COMPANY_NAME_.com (172.25.108.2)                  123.546ms 
 4:  h_reversed_Ip..mdsnwi.tisp.static.tds.net (x.x.x.x)  106.704ms 
 5:  no reply
 6:  no reply
 7:  no reply
 8:  no reply
 9:  no reply

Any ideas on how to fix this or ask the question more intelligently?

Thanks in advance,

Dave N

---

