---
title: "NetworkManager can't establish proper connection"
date: 2009-02-12
forum: Networking &amp; Wireless
---

### Post by Kuno81 on 2009-02-12
Hi,

i installed Ubuntu 8.10 last night. I had problem with internetconnection during the installtion already...

The crazy problem:
NM indeicates the wired connection. He can establish a connection to my router, with static IP as well as DHCP.
I can ping the router and other PCs in my local network.
I can ping an URL, like [www.heise.de](www.heise.de), it will be resolved and i will get an answer to the ping.
I can use ssh to loggin at my server.
I can't surf to the Internet, even not to a url which can by resolved by ping.
If i try to loggin at my router-web-frontend by browser, the router asks for name and password (which means there is an connection definitly!!!!) and after hitting ENTER the connection breaks down!

It doesn't work with the live modus as well.

Isn't this crazy???????????????????:lolflag:

Thanks for help!
Greeting, Kuno

---

### Post by superprash2003 on 2009-02-12
what happens when you try to open [http://74.125.67.100](http://74.125.67.100)

---

### Post by Kuno81 on 2009-02-12
Doesn't work.

But i found out something new:
It happens with the current version of 8.04 (Live-CD), too. And this contains the network manager as well as version 8.10.
So i deinstalled the network-manager and setup my network enviroment in /etc/network/interfaces as usual and it worked!
So the problem is definitly caused by the network-manager!

I solved my problem for now, but on a long sight i'am still interested in a solution for the actual network-manager problem, because i would like to use the easy and fast VPN tool....

Thanks for help.
Greeting, Kuno

---

