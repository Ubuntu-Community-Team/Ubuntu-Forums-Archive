---
title: "Mythtv and static IPv6"
date: 2012-03-30
forum: Mythbuntu
---

### Post by jcmiguel on 2012-03-30
I am struggling to setup a static IPv6 backend, with multiple frontends. Prevously, I had static IPv4 on .24 mythtv (mythbuntu) boxes without any issues. I have no intention to access my boxes from outside the local lan and I found the available information on IPV6 very confusing. On top of it, the backend was upgraded to 12.04 (beta) and the changes on resolvconf were impremented (adding nameservers into /etc/network/interfaces and let resolver do its thing).
I also added the IPv6 ip addresses that were given by my router (if I use the local fd00::: it does not work), a fritzbox with IPv6 capabilities on a provide that has IPv6 as well (2002::::).
The problem is that sometimes the frontend does not find the backend and freezes until I go to another machine and ping6 the backend. Very weird behaviour. Could some IPv6 guru provide us a howto static for the 12.04 that would work well with mythtv 0.25?
Regards

---

### Post by Henk Poley on 2012-03-30
Basically what you are saying, your mythbackend comes online fully operational. But IPv6 packets are not routed to it, until you ping6 to the server from some machine on your network?

---

### Post by jcmiguel on 2012-03-30
I mythbackend is on 24/7 but it seems that the frontend does not find it after it boot(and freezes). Only after a ping6 from another machine (the frontend does not have keyboard or mouse).

---

### Post by jcmiguel on 2012-03-30
Just to help ... I have this:

#/etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0

iface eth0 inet static
	address 192.168.178.100
	netmask 255.255.255.0
	broadcast 192.168.178.255
	gateway 192.168.178.1
	# dns-* implemented by the resolvconf package, if install
	dns-search domain.local
	dns-domain domain.local
	dns-nameservers 192.168.178.1
## Start IPV6 static configuration
iface eth0 inet6 static
pre-up modprobe ipv6
#address fd00::xxx:xxx:xxx:xxx
address 2002:xxx:xxx:xxx:xxx:xxx:xxx:xxx
netmask 64
#gateway  fd00::xxx:xxx:xxx:xxx
gateway  2002:xxx:xxx:xxx:xxx:xxx:xxx:xxx
### END IPV6 configuration

###########################

Numbers were replaced above by xxx 
I also have tried with the fd00 which are local ipv6 from fritzbox, with no luck

---

