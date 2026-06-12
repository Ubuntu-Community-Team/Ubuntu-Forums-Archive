---
title: "Transparent Bridging with  Web Content filter"
date: 2011-04-20
forum: Networking &amp; Wireless
---

### Post by knight19720208 on 2011-04-20
Hi everyone, sorry if my english is not so good to be clear to understand. :KS
Ok, this is my trouble... I need to have a box between the router and the ISP's end in my school. It must works like a simple sniffer that I can plug or unplug no affecting the network, in case of fail. Additionaly I think is good idea to have this box being a web content/filter for bad sites.

What I did? Well I have a clone-pc with 2 interfaces eth0, eth1. I have an Ubuntu 10.10 desktop. I downloaded squid3, dansguardian, bridge-tools, and some other fantastics utilities. Also I have followed a lot of sites that gave me ideas about my project. I'm not the only one that wants to do this project. eg. [http://www.ubuntugeek.com/how-to-setup-transparent-squid-proxy-server-in-ubuntu.html](http://www.ubuntugeek.com/how-to-setup-transparent-squid-proxy-server-in-ubuntu.html), [http://johnlewis.ie/transparent-bridging-firewalls/](http://johnlewis.ie/transparent-bridging-firewalls/), [http://imel.co.za/bandwidth](http://imel.co.za/bandwidth), etc.
It is ease to make a bridge br0, install dansguardian, squid3, BUT... here is where the issue begins...

net-clients<--->[a-switch]<---->[a-router]<--->x-[UBUNTU-B]-y<-->[ISP´s END]
10.48.0.0/23                            10.48.0.2           br0:10.48.0.3/24(Ubuntu bridged)                  IP-publics

Some of the commands:

ifconfig eth0 0.0.0.0 
ifconfig eth1 0.0.0.0 

brctl addbr br0
brctl addif br0 eth0
brctl addif br0 eth1

ifconfig br0 10.48.0.3 netmask 255.255.254.0 up
route add default gw 10.48.0.2 dev br0

#Until here, all clients can go via the br0 without problems: They can get DHCP from Win server, Internet, etc, perfectly.

Then I installed squid3 and it works on 3128 port, I see it with port-scan
I include the network 10.48.0.0/23 to be filter in transparent mode, so
http_port 3128 transparent

Then inside of dansguardian, I use the port 8080 and It points to proxy's port 3128 given for squid. Following some site instructions, I did setup the firefox network proxy to 127.0.0.1 with port 8080. This works perfectly inside the Ubuntu box, the filtering block 
bad sites!!

Now the idea is that each one of the network that tries to connectt to Internet 
must be catched by some iptable rules inside the br0 on Ubuntu and redirected them to 8080 of DG. Then this one must talk with SQ3 filtering or not the bad sites and passing traffic to Internet.

Rules like these have been used:

#ebtables -t broute -A BROUTING -p IPv4 --ip-protocol 6 \
--ip-destination-port 80 -j redirect --redirect-target ACCEPT

# iptables -t nat -A PREROUTING -i br0 -p tcp --dport 80 \
-j REDIRECT --to-port 8080

The ping to some site, eg. cisco.com continues working, however the browsing
to this same place stop inmediatly.

Th Internet browsing continues working inside the Ubuntu, so the first thing I 
see is that iptables/ebtables application/sentences are wrong, but I can't see where or why!!

Please all ideas and suggestions are welcome

Thanks:guitar:

---

### Post by saurabhagarwal on 2011-08-28
Hi,

I am trying to do the same thing and is facing the similar problem. 
If by any any chance you ware able to figure out the solution kindly help us out. 


Also there is situation where I have to install the squid box for multiple IP pools each having a different gateway.

---

