---
title: "Everything other than port 80 not working (iptables problem I think)"
date: 2009-03-16
forum: Networking &amp; Wireless
---

### Post by vlovich on 2009-03-16
I'm having some problems.  Here's my current setup that I have.

Laptop:
eth0 - LAN card.  Set to obtain a static IP of 192.168.0.1
eth1 - wifi - DHCP obtains an address 192.168.1.x

Running dnsmasq to provide DHCP for desktop & DNS server.  Resolvconf installed.

dhclient:

```
prepend domain-search "mshome";
supersede domain-name "mshome";

request subnet-mask, broadcast-address, time-offset, routers,
  domain-name, domain-name-servers, domain-search, host-name,
  netbios-name-servers, netbios-scope, interface-mtu;

```

iptables set to:
```

iptables -A FORWARD -i eth0 -o eth1 -s 192.168.0.0/24 -m state --state NEW -j ACCEPT
iptables -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A POSTROUTING -t nat -j MASQUERADE

```

Desktop:
Set to obtain a dynamic ip.

Everything works, except that the pidgin client on the laptop & desktop now fail to connect to all my connections (Google Talk, AIM, & MSN).  Pidgin is able to connect using the Facebook client & Skype is working as well.  Further testing indicates that the only working ports are low ports like 80 & 22.

Regular web connections work fine.

I'm also able to ping talk.google.com (& looking at dnsmasq's logs indicates it is properly resolving the IP addresses).  However, when I try to telnet (e.g. telnet talk.google.com 5222) the connection times out.

I can telnet into talk.google.com port 443, but setting pidgin to 443 gets a read error (even though on Google's support pages it says 443 is a valid port). 

Now I'm not 100% sure what the issue is.  For instance, I can ssh to other computers outside my connection.  I checked & ufw is disabled.  I've also tried flushing the iptables (iptables -F) & it still doesn't work.

Thanks

Update: Oh yeah, in case anyone missed it.  /etc/resolve.conf does contain 127.0.0.1 & dnsmasq does actually use the ISPs server (verified by /var/run/dnsmasq/resolv.conf).  Also, regular web browsing does work & I've verified several ways (enabling logs & viewing requests, using dig etc).

---

