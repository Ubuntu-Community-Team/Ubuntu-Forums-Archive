---
title: "dhcp options for shared connection?"
date: 2011-12-14
forum: Networking &amp; Wireless
---

### Post by rgcosma on 2011-12-14
Hello, 
Is there any way to add a dhcp option (next-server in my case) when a connection is set as 'shared'?
I see NM starts a dnsmasq instance with parameters
/usr/sbin/dnsmasq --conf-file --no-hosts --keep-in-foreground --bind-interfaces --except-interface=lo --clear-on-reload --strict-order --listen-address=10.42.43.1 --dhcp-range=10.42.43.10,10.42.43.100,60m --dhcp-option=option:router,10.42.43.1 --dhcp-lease-max=50 --pid-file=/var/run/nm-dnsmasq-eth2.pid
and I dug through /etc/NetworkManager/system-connections and read (briefly) the [libnm sources]("http://cgit.freedesktop.org/NetworkManager/NetworkManager/tree/libnm-util") but the parameters don't seem to be specified there..

---

