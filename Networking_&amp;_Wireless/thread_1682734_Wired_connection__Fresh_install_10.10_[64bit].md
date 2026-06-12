---
title: "Wired connection | Fresh install 10.10 [64bit]"
date: 2011-02-06
forum: Networking &amp; Wireless
---

### Post by Grova on 2011-02-06
**EDIT**:  This same solution just solved my wireless issue as well. 
BCM4318 default additional driver activated, tried to connect to home network but could not get a connection. 
Set IP manually as well as correct DNS instead of router address. 
Works every time now.


Hello all! 

I decided to once again jump back to ubuntu from Win7.
With past installations of Ubuntu i have always experienced networking issues (Most, if not all, Wireless).

This installation however, immediately gave me a problem to solve from the start, with my wired connection.
[U][B]
Hardware:[/B][/U]
-Router  Netgear WNDR3300
-NIC       Realtek RTL8111/8168B PCIEx

_**Problem:**_
eth0 will not connect

_**Solution:**_
I was able to finally get a connection through eth0 by manually assigning an IP/Subnet Mask/Default Gateway as well as 2 DNS addresses and Default Gateway (Router Address) as an alternative.

To find out the DNS addresses an ISP provides. Simply login to the router and check the router status.
Under the Internet Port status, Domain Name server addresses will be provided.

_**How? and why?:**_
Every computer on my home network has experienced a loss or absolutely no connection at times (wireless or wired). I checked to see that my other box was online. It is running win7 and periodically looses connection. In the wireless adapter properties i noticed the DNS was set to 192.168.1.1.

A router CAN act as a DNS by using its own address. An ISP however, should provide you with 1 or more of there DNS addresses. 

My problem is that my router would act as a tunnel DNS as well as DGW. 
Instead of every computer on the network pulling an address from the ISP's DNS. They would instead pull them from the router which pulled them from the ISP.

For some reason this resulted in no connection at times under Windows.
And none at all under linux.

Once the addresses were retrieved, I then set them manually under eth0 IPV4 settings.
Separating them with commas because of multiple addresses and using the DGW address as a backup in case the ISP changes DNS addresses, or one goes down.


_**Other Possible Solutions**_:
-Unplug router and modem > Plug in modem (wait to fully startup) > Plug in Router > Connect!
-Manually assign IP ( System > Preferences > Network Connections > (interface) edit > IPV4 tab > Manually
-Try a spare CAT5 
-Check to see that other computers are able to connect


---------------------------------------------------------------
Hope this will be of help to the community!


~Grova

---

