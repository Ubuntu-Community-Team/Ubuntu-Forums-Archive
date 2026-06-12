---
title: "wifi connects but cannot ping router"
date: 2010-12-16
forum: Networking &amp; Wireless
---

### Post by i,bigfoot on 2010-12-16
Hi all,

I have a strange problem with my networking that I am not sure how to solve, or indeed how it came about..

My ASUS eeepc was running fine, no changes to the 10.4 netbook remix other than updates until about 2 days ago when it just wouldn't find anything on the internet, "Server not found" errors in FF. 

running an ifconfig shows me that it has obtained an ip address 
192.168.20.104 which is kind of strange as every other machine on the network has ip address of 
192.168.1.xxx

I decided this was just my computers way of telling me to upgrade to 10.10 netbook remix, however once this was done the ip address on the wireless interface remained the same. 

Currently, my wireless indicates that I am connected with a 70% strength, yet I cannot even ping my router. 

Can anyone suggest what may be worth looking at further to fix this? 

Cheers,
Troy

---

### Post by chili555 on 2010-12-16
> running an ifconfig shows me that it has obtained an ip address
192.168.20.104 which is kind of strange as every other machine on the network has ip address of
192.168.1.xxxI expect you are actually connected to your neighbor's wireless network. When you click the Network Manager icon, what network shows as connected? For example, in the attached, **GBR1** is in bold and is the network to which I am connected. Dynex and WEST5214 are networks that are available to which I am not connected.

---

### Post by i,bigfoot on 2010-12-16
Hi,

Thanks for the reply... no, i am definitely connected to my network, all the neighbours are secure (well, a couple are wpa but you get the idea)

It turns out this is probably not my netbook, but the router.  My brother has just turned up with his windows machine and was assigned an incorrect IP from the router as well.. 

further investigations elsewhere required i think.. again, thanks for the reply

cheers,
troy

---

### Post by i,bigfoot on 2010-12-16
update.. 

just upgraded firmware to billion 3700G router.. still experiencing same problem with netbook, however desktop ubuntu 10.10 is wireless'ing fine.. 

time for some head scratching.. 

cheers,
troy

---

