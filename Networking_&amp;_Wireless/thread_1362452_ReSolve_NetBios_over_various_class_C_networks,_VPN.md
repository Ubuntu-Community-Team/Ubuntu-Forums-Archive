---
title: "ReSolve NetBios over various class C networks, VPN"
date: 2009-12-23
forum: Networking &amp; Wireless
---

### Post by juan234 on 2009-12-23
Dear all,
I am trying to resolve netbios names over VPN on many class C networks.  It works for me on my network which is 192.168.7.xxx.  If I try to resolve a machine on 192.168.0.xxx or 192.168.2 etc it doesnt work.  nslookup and ping work...Any ideas? 


winbind with the following /etc/nsswitch.conf

passwd:         compat
group:          compat
shadow:         compat

hosts:          files wins mdns4_minimal [NOTFOUND=return] dns mdns4
networks:       files

samba.conf is

[global]
realm = mydomain.com
netbios name = Samba24
server string = Samba file and print server
workgroup = WORKGROUP
security = ads
hosts allow = 192.168.0 192.168.7 192.168.2 192.168.9 127.
interfaces = 127.0.0.1/8 192.168.0.0/24 192.168.7.0/24 192.168.2.0/24 192.168.9.0/24
bind interfaces only = yes
remote announce = 192.168.7.255
remote browse sync = 192.168.7.255

---

