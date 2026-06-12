---
title: "Using Ubuntu as a Router - XBOX360 Port Forwarding"
date: 2010-10-26
forum: Networking &amp; Wireless
---

### Post by MrOzBarry on 2010-10-26
Hello Ubuntu Community,

I have Ubuntu (desktop) setup to be a router/gateway (using [this guide]("http://ubuntuforums.org/showthread.php?t=926001") thanks sammydee) with webmin.
I am having problems when I start setting up the firewall.

I get as far as setting up the filtering, and everything works well.  I startup my xbox and it will connect to live, but then the xbox tells me I need to use NAT for port forwarding, so I googled around and got the webmin wiki, and documentation for the linux firewall module.  I read it to the best of my abilities, so I start setting up port forwarding for my xbox (which has a static IP of 192.168.10.100).

MSDN says I need:

[LIST]
[*]TCP 80
[*]UDP 88
[*]UDP 3074
[*]TCP 3074
[*]UDP 53
[*]TCP 53
[/LIST]
NAT - Pre-Routing
Action To Take: Destination NAT
IPs and Ports: 192.168.10.100 : 80
Network Protocol: Equals TCP
Destination TCP/UDP Port: 80

Then I click create, and all is good.  I repeat in similar fashion, but after I get past 3074 for routing, I tested the xbox live connection, and it tells me I can't access the internet.
I am applying the new settings, too, so that's not the issue.
Upon doing that, I delete the NAT Prerouting entries, and it still says there is no internet connection.
The only way to get the internet working again is to click the reset rule, which forces me to put all the filtering rules in again.  I've done this multiple times, and I can't seem to get port forwarding working.

Am I doing something horribly wrong?
I've been frustrated with this all day.

To be honest, I was using Lubuntu yesterday, and it worked, but I had some issues with the operating system that didn't make it a viable router OS for me, but port forwarding worked flawlessly.

Thanks for any help,
-Oz

Added Details:
Once I add the port forwarding rules, sometimes the xbox says there is a DNS problem (which there isn't, according to other computers on the network), and other times it just says there is no internet connection (again, I can still connect to the internet with my computers, just not my xbox)

More Information:
The problem seems revolve around port 53 tcp/udp

---

### Post by MrOzBarry on 2010-10-26
Sorry for the double post, but I solved it.  Most of the guides did not mention that you have to set the incoming interface to the internet connection (in my case, ppp0).

Take care,
-Oz

---

