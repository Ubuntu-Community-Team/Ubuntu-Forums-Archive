---
title: "Problem with PPPoE through router EDIMAX in Ubuntu 9.10"
date: 2010-02-21
forum: Networking &amp; Wireless
---

### Post by DemoNMorph on 2010-02-21
Hy everyone!
I have 2 PC's : a desktop and an notebook(IBM).On my desktop i have Windows 7 and Ubuntu 9.10,and on my notebook(IBM) is Windows XP SP3...
Both of the PC's are conected to internet over an PPPoE conection in Windows thorugh my router(EDIMAX).

My desktop has the following : 
IP adress : 192.168.2.100
Subnet mask : 255.255.255.0
Default gateway : 192.168.2.1
Preferred DNS server : 192.168.2.1

My notebook has the following : 
IP adress : 192.168.2.101
Subnet mask : 255.255.255.0
Default gateway : 192.168.2.1
Preferred DNS server : 192.168.2.1

When i boot to Ubuntu 9.10 i dont have internet...but if i restart the PC and enter in Windows 7 there is internet,and is the same connection,the same adresess...
How can i make the connection in Ubuntu 9.10 with the same adress,i mean like is in Windows 7?:confused:

---

### Post by Charly85551 on 2010-02-23
Hi DemoNMorph,
first of all the IP-address is given by the DHCP-server within your router and is related to your computer's network card (directly linked to the MAC-address of the network card!). So unless you change from a wired card to a wireless card it will always be the same.
The other point which is a bit confusing in your question is the fact that you talk about a PPPoE connection when you are working with a router. Normally you should have a standard network set-up with your router and the router is handling the PPPoE protocol in the connection to the internet. I have Ubuntu 9.10 on my media player directly talking to my router as well as my desktop PC and it works just fine.:smile:
May be having a look into your ifconfig on Ubuntu could be helpful.
cheers
charly

---

### Post by Fiable.biz on 2010-10-14
Charly,

to do that, what router do you use? Is any router able to do this? Is it necessary to configure it? Does your internet provider provides you with a fix public IP?
We are in a big LAN (of the size of the town), with one private IPv4 address dynamically allocated by Telecom Mongolia, our ADSL provider, through PPPoE. We're looking for a solution to get a sub-local network, just for our office. I thought of turning an Ubuntu PC into a router, but I can't find enough information about this. (See my thread
"[Setting Ubuntu as a router with PPPoE connection, dynamic private IP]("http://ubuntuforums.org/showthread.php?t=1593922&highlight=router+PPPoE")".)
Maybe a hardware router would be better, but the only one I found for sale in this town has its instruction manual in Chinese only and, of course, the seller can't help.

---

