---
title: "iptables nat loopback uPnP"
date: 2013-01-24
forum: Networking &amp; Wireless
---

### Post by CalvinZA on 2013-01-24
Good day,

This computer is used as a network firewall and WAN router.

eth0:10.0.0.1
ppp0: dynamically assigned 
ppp0 ipv4 addr is pointed to by alias.dynDNS.provider.xyz

i.e dynDNS.provider.xyz:1234 should direct to an IP who has port:1234 forwarded using uPnP (linux-igd) on the local network.
Which iptable rules would allow redirection to the correct recipient when requesting from behind the NAT?

Routing and uPnP are both working as required.

Thank you

/etc/iptablesScript.sh
```
iptables -A FORWARD -o ppp0 -i eth0 -s 10.0.0.0/8 -m conntrack --ctstate NEW -j ACCEPT
iptables -A FORWARD -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
iptables -t nat -F POSTROUTING
iptables -t nat -A POSTROUTING -o ppp0 -j MASQUERADE

```

/etc/upnpd.conf
```

iptables_location = "/sbin/iptables"

debug_mode = 2

create_forward_rules = yes

forward_rules_append = no

forward_chain_name = FORWARD

prerouting_chain_name = PREROUTING 

upstream_bitrate = 512000

downstream_bitrate = 512000

duration = 0

description_document_name = gatedesc.xml

xml_document_path = /etc/linuxigd

listenport = 0

paranoid = 0

upnp_log_level = UPNP_CRITICAL

```

---

