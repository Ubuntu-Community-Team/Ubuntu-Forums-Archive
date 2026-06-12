---
title: "can't set firewall"
date: 2012-07-14
forum: Networking &amp; Wireless
---

### Post by bhomas on 2012-07-14
I used this command

iptables -A OUTPUT -p tcp -s 192.168.1.0-192.168.1.255 --sport 5432 -d 0/0 --dport 1024:65535 -m state --state ESTABLISHED -j ACCEPT

to open up firewall in my VirtualBox running Ubuntu. This worked in another instance before.

now I get a 
iptables v1.4.12: host/network `192.168.1.0-192.168.1.255' not found

I ping the host system by ip
ping 192.168.1.103, and it responded.

Why would iptables command fail?

---

### Post by Kirk Schnable on 2012-07-14
I've never seen the network portion of a command formatted like that.

Instead of what you did:
```
iptables -A OUTPUT -p tcp -s 192.168.1.0-192.168.1.255 --sport 5432 -d 0/0 --dport 1024:65535 -m state --state ESTABLISHED -j ACCEPT
```

Try:
```
iptables -A OUTPUT -p tcp -s 192.168.1.0/24 --sport 5432 -d 0/0 --dport 1024:65535 -m state --state ESTABLISHED -j ACCEPT
```

Kirk

---

