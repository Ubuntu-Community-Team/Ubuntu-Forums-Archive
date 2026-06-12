---
title: "Port redirection on aliased network card"
date: 2010-04-09
forum: Networking &amp; Wireless
---

### Post by ocwo92 on 2010-04-09
I have one network card, eth0, with IP address 192.168.2.2. I'm running a Samba server which is bound specifically to this IP.

In addition, the network card has an alias, eth0:0, with IP address 192.168.2.3. I want to run another "Samba" (Alfresco's CIFS server) server on this IP address. Because the server runs as a non-root user, it can't use the privileged ports and instead uses ports 1445, 1137, 1138, and 1139.

According to the [Alfresco documentation](http://wiki.alfresco.com/wiki/File_Server_Configuration), these ports can easily be redirected using iptables:

```
echo 1 > /proc/sys/net/ipv4/ip_forward
modprobe iptable_nat
iptables -F
iptables -t nat -F
iptables -P INPUT ACCEPT
iptables -P FORWARD ACCEPT
iptables -P OUTPUT ACCEPT
iptables -t nat -A PREROUTING -p tcp --dport 445 -j REDIRECT --to-ports 1445
iptables -t nat -A PREROUTING -p tcp --dport 139 -j REDIRECT --to-ports 1139
iptables -t nat -A PREROUTING -p udp --dport 137 -j REDIRECT --to-ports 1137
iptables -t nat -A PREROUTING -p udp --dport 138 -j REDIRECT --to-ports 1138
```
I've verified that the CIFS server is indeed listening at 1139 and other ports.

Alas, the ports apparently aren't forwareded, maybe because my configuration is slightly a bit different with the aliased network card.

I tried to enter:

```
iptables -t nat -i eth0 -d 192.168.2.3 -A PREROUTING -p tcp --dport 139 -j REDIRECT --to-ports 1139
```
in order to explicitly specify the aliased network card (iptables doesn't support aliases), but apparently the port isn't forwarded on 192.168.2.3.

Can someone help me figure out what to enter to make iptables forward port 1139 on 192.168.2.3 to port 139 on 192.168.2.3?

---

