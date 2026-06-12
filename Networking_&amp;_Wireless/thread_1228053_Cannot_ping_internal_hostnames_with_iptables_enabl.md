---
title: "Cannot ping internal hostnames with iptables enabled on client, ip address ping works"
date: 2009-07-31
forum: Networking &amp; Wireless
---

### Post by scenered on 2009-07-31
In my network I have several servers. All set up with iptables and samba.
I can ping from one to another just fine using ip addresses. But it does not work using the hostnames. But when I turn off iptables on the client doing the ping it works just fine. It also works if I open up all incoming UDP ports on the client doing the ping.
For the same reason, I cannot use [FONT=Courier New]smb://servername[/FONT] from the client either when normal iptables is enabled. When I allow all incoming UDP ports, [FONT=Courier New]smb://servername[/FONT] can also be used just fine.
How can I get pinging of hostnames to work without opening up all UDP ports on the client?
Applies to ubuntu 8.04, 8.10 and 9.04 (32 bit and 64 bit, server and desktop).
From a windows PC I can ping the servers with hostnames just fine...

Pinging of external hostnames works just fine with iptables enabled.
I do not want to set up all the servers in /etc/hosts either.

Some lines from IP tables set up on all servers.
[FONT=Courier New]sudo iptables -A INPUT -s $source -p tcp -m multiport --dports 135,139,445 -j ACCEPT
sudo iptables -A INPUT -s $source -p udp -m multiport --dports 137,138 -j ACCEPT
sudo iptables -A INPUT -s $source -p icmp -m icmp --icmp-type 0 -j ACCEPT
sudo iptables -A INPUT -s $source -p icmp -m icmp --icmp-type 8 -j ACCEPT
[/FONT] 
From [FONT=Courier New]/etc/nsswitch.conf[/FONT]:
[FONT=Courier New] hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4 wins
[/FONT]
To get it to work I can add this to the client iptables doing the ping:
[FONT=Courier New]sudo iptables -A INPUT -p udp --dport 100:50000 -j ACCEPT
[/FONT] But the port used seems to be dynamic...

---

