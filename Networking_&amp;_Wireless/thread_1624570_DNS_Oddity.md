---
title: "DNS Oddity"
date: 2010-11-17
forum: Networking &amp; Wireless
---

### Post by slinkeey on 2010-11-17
DNS Oddity

Hello,

I have an odd thing going on with DNS.

I have two machine's running Ubuntu and for some reason they do not always resolved internet addresses on  my Internet connection.  This has gone on since the Ubuntu 8.04 when I first started using Ubuntu.

Anyway, I use OpenDNS' DNS servers and I have been running perfectly.

This is what is odd.  My Windows XP Machine never has the problem.  It always resolves.  Does Windows Possibly have some Microsoft hosted DNS server hard coded in there as a backup?

Things are working fine this way so I am not looking to change.  I am just a little puzzled and finally got around to asking, "Why is this:confused:".

Jeff

---

### Post by uncaspi on 2010-11-17
I think it can had to do with the nameservers obtained from the router and ISP. Ubuntu only search 3 valid servers while windows tries many. Due to this Ubuntu works fine with OpenDNS which is valid. If this made it clearer.

---

### Post by slinkeey on 2010-11-18
Thanks for the info.

I am going to see how many DNS servers my Windows box gets assigned.

---

### Post by pricetech on 2010-11-18
The short answer to how many DNS servers windows can handle is 2.  You have to go into advanced properties to add more.

The default for Ubuntu is 2 as well, but again you can add more.

Windows doesn't have an advantage here.

---

### Post by endotherm on 2010-11-18
windows seems to use a longer timeout or subsequent retries before declaring a response NXDOMAIN. it can take up to 2 minutes for a DNS res issue to return as "not found" whereas Ubuntu's is 2 seconds. 

are your PCs recieving the DNS address from a dhcp server, or is everything statically addressed? do you have openDNS ips set manually, in each box, or are they set in a router or bind server? is the router proxying dns queries for you?

---

### Post by slinkeey on 2010-11-18
PCs Recieve DNS address from my cheapie Netgear router.

I added OpenDNS to my Ubuntu machine's by allowing DHCP except for DNS and then manually filled in the OpenDNS IP Addresses.  I did this because these two machines had issues with resolving internet adddresses.  The Windows Machine is Strict DHCP from my router.

It is not a big deal really.  OpenDNS has some nifty features.  Maybe someone can even reccomend a free service (better yet, Open Source) that has nifty features.

I just thought this would be an interesting topic.

Thanks,
Jeff

---

### Post by pricetech on 2010-11-18
If you prefer OpenDNS you can (should be able to) change what your router assigns to DHCP clients.

You didn't mention the Netgear model.

---

### Post by slinkeey on 2010-11-18
The router is proxying dns queries.

ipconfig on the Windows box yields the router's IP address for DNS.

I don't know the model of my router off hand. It pretty much hangs out in the basement and does its thing. I don't go visit it physically or logically very often.  I will look that up later.

---

### Post by endotherm on 2010-11-18
> **slinkeey said:**
> The router is proxying dns queries.

ipconfig on the Windows box yields the router's IP address for DNS.

I don't know the model of my router off hand. It pretty much hangs out in the basement and does its thing. I don't go visit it physically or logically very often.  I will look that up later.
try opening prt 53/udp inbound on your router. DNS is a connectionless protocol, so replies to your requests don't appear to be replies, but just a DNS datagram. 
when the router is the DNS proxy, it doesn't need this rule. 

give it a try and let us know how it works.

---

### Post by slinkeey on 2010-11-18
If it works with OpenDNS then wouldn't that tell me that my router is letting that traffic through?

---

### Post by endotherm on 2010-11-19
if you mean, that openDNS works for your windows hosts, then no, since the router is acting as proxy for the windows boxes (pure dhcp) but the ubuntu hosts are trying to connect directly to the remote dns server. 

or are you saying the issue is resolved? sorry if I misunderstood.

---

### Post by slinkeey on 2010-11-19
**Issue is resolved -- Just Curious**

OpenDNS Works on all of my computers.

DHCP assigned DNS via my router works all of my computers except every once in awhile it doesn't work on my ubuntu machines.  The Windows Machine Works all of the time but the windows machine is hardly ever used.

I got around this by using OpenDNS and that is fine.. I am happy with OpenDNS.

---

