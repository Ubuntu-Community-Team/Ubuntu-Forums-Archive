---
title: "Iptables help, I am stumped..."
date: 2009-04-20
forum: Networking &amp; Wireless
---

### Post by DocLogic on 2009-04-20
Granted likely something stupid I am over looking..
I have a "Daul Router" setup, both K6/2 boxes running Ubuntu 8.10 Server.
The first router has 3 nic's. eth0 connects to a cable modem, eth1 & eth2 are bridged giving me br0.
This box is set up for very simple forwarding/masquerade. For the most part intentionally running wide open. We'll call this wan1.
The second box has 2 nic's, eth0 is crossover cabled to port 1 of br0 on wan1. eth1 connects to my switch for the internal network. This is lan1, it carries the firewall protecting my internal network.
This is working nicely, masquerading all works, Internet connectivity is great, and using simply iptables for both.
The idea here was to create a class c DMZ between the two routers. ddclient is set up and working, I can dig the public hostname and it returns the ip of eth0 on wan1.
Now here is where I am stumped. I am not a noob to linux, though I don't really have a lot of iptables experience.
I have a third box connected to br0 on wan1 that I call nfs1, also running Ubuntu 8.10 server. It has apache2 running, and nfs for the internal net. nfs works fine, as does apache2. If I call apache2 using the lan side (eth1 of lan1). However in firefox I get "can't establish connection" if I call the host name.
I installed links in wan1 for a test, and called up port 80 on nfs1 via direct ip address, web page came right up instantly using the br0 on lan1 IP. But if I call it by FQDN (via ddns) I get "connection refused."

I have set iptables to basically accept all from/to anywhere, forwarding is on (masquerade is working), and added the following rule in a few different varients with no luck!

/sbin/iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 80 -j DNAT --to-destination 192.168.1.2

What should I be looking for?

Addendum.. As a quick test I installed boa on the first router (wan1) and called the box using my ddns domain name and no problem at all connecting to httpd when the http server is on the physical router. This eliminates blocking from ISP. SO still quite stumped on why I can not forward/redirect incoming port 80 calls to a specific static ip on the network ?!

Any help would be greatly appreciated.

Doc.

---

### Post by DocLogic on 2009-04-22
**RESOLVED!**

Dang! Chalk it up to my inexperience with iptables and a little brain flatulence.

Problem was actually an easy fix.
iptables -t nat PREROUTING -i <extif> -d <intif> --dport 80 --to <local httpd IP>
was the right idea, only going through ddns, the call would not be being made TO the internal IF. DDNS would return the IP of my external IF on wan1, so adding;

iptables -t nat PREROUTING -i <extif> -d <extip> --dport 80 --to <local httpd IP>

corrected calls coming from the outside world to my server. 
And adding;

iptables -t nat PREROUTING -i <intif> -d <extip> --dport 80 --to <local httpd IP>

corrected calls from the internal network calling the server by it's FQDN via DDNS...


Doh!

Thanks all!

---

