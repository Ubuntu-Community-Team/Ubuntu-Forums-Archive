---
title: "A way to assign permanent hostnames to dynamic local IP addresses in my home n/w ??"
date: 2009-03-31
forum: Networking &amp; Wireless
---

### Post by seemanta on 2009-03-31
Hi,

I think my question sounds very trivial, nevertheless I did not find any solution after searching that solved my "exact" problem.

So I have this router which is connected to the external world and I have two laptops and a desktop which connect to this router and accesses the Internet.

Everything works fine. My two laptops and the desktop gets assigned IP addresses(192.168.xxx.xxx) at power up time via DHCP. I can freely ping, ftp, ssh from all of them to each other using their IP addresses.

But my aim is to assign ***permanent ***hostnames to my two laptops and the desktop so that I can do all of the above using their hostnames and NOT using their changing IP addresses.

I want permanent hostnames despite dynamic IP addresses. That's my problem. Can this be achieved ?

Any clues/pointers would be greatly appreciated!

regards,
Seemanta

---

### Post by coutts99 on 2009-03-31
I've only ever done this using a combination of bind and dhcpd

[http://idahopcug.apcug.org/Linux/dnshowto.pdf]("http://idahopcug.apcug.org/Linux/dnshowto.pdf")

---

### Post by sisco311 on 2009-03-31
I never tried myself (I'm using static IP), but this should do the trick:
[http://www.lucidtips.com/2008/11/17/send-hostname-to-dhcp-server-on-ubuntuxubuntu/]("http://www.lucidtips.com/2008/11/17/send-hostname-to-dhcp-server-on-ubuntuxubuntu/")

---

### Post by seemanta on 2009-03-31
sisco311,
Your solution looks simpler. Will try and update the results here.

~seemanta

---

### Post by Iowan on 2009-03-31
From the Synaptic description:> Dnsmasq is a lightweight, easy to configure, DNS forwarder and DHCP
server. It is designed to provide DNS and optionally, DHCP, to a
small network. It can serve the names of local machines which are
not in the global DNS.

---

