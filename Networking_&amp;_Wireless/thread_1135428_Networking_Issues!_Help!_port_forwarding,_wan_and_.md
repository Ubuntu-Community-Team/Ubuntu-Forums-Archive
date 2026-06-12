---
title: "Networking Issues! Help! port forwarding, wan and other jargon"
date: 2009-04-24
forum: Networking &amp; Wireless
---

### Post by L14UX_1NS1D3 on 2009-04-24
Hi all! 

I've been try to do this for some time now. I've combed through forums, website tutorials also IRC's but I'm still quite confused about certain networking setups.

I setup a server with ssh and also torrentflux (a web base torrent client). I have been able to access the server through the home network (wireless and wired).
Now this is where I hit a brick wall, I have a MR814V2 router. From there there the internet is fed through a verizon Westell 6100 modem. I setup port forwarding on the MR814 AND on the modem for the same ports ( 80 and 22).
I also registered the router to use a dynamicDNS account.

So I figured that if I forwarded port 80 on the router it would be blocked by the firewall rules running on the modem and would not be pingable. 
Second, I also forwarded port 80 on the modem so if I pinged the host name for the open port it would work.  Turns out it didn't. I found some websites that would allow me to do a ping, traceroute and dns lookup from an ip on the net but when I would ping the host name that I gave to the WAN ip it either: timed out, didn't go through or said that the certain ip was reserved. 

I was able to discover the IP of the WAN by going to [http://checkip.dyndns.org/](http://checkip.dyndns.org/) and applying the given ip that to the DNS account. But for some reason the router would update the DynDNS account with the default ip of the router 192.168.1.47 so, when ever I would attempt to ping the hostname it wouldn't work because that ip was reserved for a SUBNET!

It's strange, I also setup a DNS name for my server with a ip within the subnet of the homenetwork and I am able to reach it through that (when I'm on the home network). So I know that the dns account is somehow able to access the IPs on the network and subnet. 


I'm extremely confused with all of this, and not to mention frustrated.
Any thought, comments, ideas and ultimately solutions are eternally welcome! :P

---

