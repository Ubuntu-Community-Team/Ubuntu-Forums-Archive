---
title: "little help; no outside connections after iptables enabled..."
date: 2013-05-12
forum: Networking &amp; Wireless
---

### Post by freeballer on 2013-05-12
I'm "getting back" into linux, after a number of years away. I have basically installed xubuntu v13.04 Raring Ringtail onto this netbook. I've also done my best to secure it and running services (ssh, lighttpd, proftpd).. But one thing is kicking my butt, and that's iptables.

i created my iptables using an online "generator", because it was simple. Afterwards I can ssh into the netbook, even connect to web server. It will resolve dns, but will not establish any connection to the outside world; pings, traceroute, apt-get.......

```
#!/bin/sh

# iptables script generated 2013-05-12
# http://www.mista.nu/iptables

IPT="/sbin/iptables"

# Flush old rules, old custom tables
$IPT --flush
$IPT --delete-chain

# Set default policies for all three default chains
$IPT -P INPUT DROP
$IPT -P FORWARD DROP
$IPT -P OUTPUT DROP

# Enable free use of loopback interfaces
$IPT -A INPUT -i lo -j ACCEPT
$IPT -A OUTPUT -o lo -j ACCEPT

# All TCP sessions should begin with SYN
$IPT -A INPUT -p tcp ! --syn -m state --state NEW -s 0.0.0.0/0 -j DROP

# Accept inbound TCP packets
$IPT -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
$IPT -A INPUT -p tcp --dport 21 -m state --state NEW -s 0.0.0.0/0 -j ACCEPT
$IPT -A INPUT -p tcp --dport 22 -m state --state NEW -s 0.0.0.0/0 -j ACCEPT
$IPT -A INPUT -p tcp --dport 80 -m state --state NEW -s 0.0.0.0/0 -j ACCEPT
$IPT -A INPUT -p tcp --dport 443 -m state --state NEW -s 0.0.0.0/0 -j ACCEPT
$IPT -A INPUT -p tcp --dport 10000 -m state --state NEW -s 0.0.0.0/0 -j ACCEPT

# Allow inbound access to Samba shares
$IPT -A INPUT -p udp -m udp --dport 137 -s 192.168.1.0/24 -j ACCEPT
$IPT -A INPUT -p udp -m udp --dport 138 -s 192.168.1.0/24 -j ACCEPT
$IPT -A INPUT -m state --state NEW -m tcp -p tcp --dport 139 -s 192.168.1.0/24 -j ACCEPT
$IPT -A INPUT -m state --state NEW -m tcp -p tcp --dport 445 -s 192.168.1.0/24 -j ACCEPT

# Accept outbound packets
$IPT -I OUTPUT 1 -m state --state RELATED,ESTABLISHED -j ACCEPT
$IPT -A OUTPUT -p udp --dport 53 -m state --state NEW -j ACCEPT
```

I need to flush the iptables rules and reboot in order for it to work...

I'll be using **transmission-daemon** *(9091)*, **sabnzbplus** *(9090)*, **lighttpd** *(80,443)*, **sshd** *(22)*, 
**pro-ftpd** *(22)*, **webmin** *(10000)*, **samba** *(137-139,445,901)*

If these tables are sufficient, and I get outbound connections fixed, I should be able to get the other daemons connected (transmission, sabnzbplus) and any other new ones.

I'd like to limit access to my samba, through iptables. The ip address is dhcp but controlled by router, it always gets **192.168.1.10x** & the other pcs are **x.x.x.100-120**

I'd really appreciate the help. I've been tinkering with this linux box for a few days now and I'm getting a bit fustrated. I'd like to keep it secured, if I can.

Thanks for viewing/visiting
Geo

---

### Post by The Cog on 2013-05-12
The only type of outgoing connection you are allowing is udp domain-name resolution. Unless you want to be picky about the type of connections you allow out from your computer, I would suggest that you change the default policy for outgoing packets to ACCEPT.

I don't see a rule allowing incoming connections to transmission-daemon (9091). I suggest you add that to your list of accepted inbound connections. Transmission will work much better if people can connect to it.

To limit the callers to samba, change your 443 line to something like this:
```
$IPT -A INPUT -p tcp --dport 443 -m state --state NEW -m iprange --src-range 192.168.1.100-192.168.1.120 -j ACCEPT
```

I would suggest that you don't allow telnet (21) in unless you really have to, and if so then also limit the IP addresses that can access that.

I also suggest that you limit the addresses that can access webmin.

---

### Post by freeballer on 2013-05-12
> **The Cog said:**
> The only type of outgoing connection you are allowing is udp domain-name resolution. Unless you want to be picky about the type of connections you allow out from your computer, I would suggest that you change the default policy for outgoing packets to ACCEPT.

TY TY I was getting so fustrated. At this stage I'm not worried that much about outgoing connections.

> **The Cog said:**
> I don't see a rule allowing incoming connections to transmission-daemon (9091). I suggest you add that to your list of accepted inbound connections. Transmission will work much better if people can connect to it.

I deliberately left out some daemons because I wanted to check the "vital" daemons, services and connections first.
Its my next step; I'm setting up and "securing" sabnzbdplus and transmission-daemon right now.

> **The Cog said:**
> To limit the callers to samba, change your 443 line to something like this:
```
$IPT -A INPUT -p tcp --dport 443 -m state --state NEW -m iprange --src-range 192.168.1.100-192.168.1.120 -j ACCEPT
```

I've changed my rules, to exactly that. ty for the recomendation.

> **The Cog said:**
> I also suggest that you limit the addresses that can access webmin.

i didn't change it there because webmin has its own ip filters. They are currently set to only allow local network, and localhost.

---

