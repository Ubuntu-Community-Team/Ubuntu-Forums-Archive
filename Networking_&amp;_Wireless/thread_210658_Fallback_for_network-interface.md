---
title: "Fallback for network-interface"
date: 2006-07-07
forum: Networking &amp; Wireless
---

### Post by schuetze on 2006-07-07
Hey ho,

i configured my NIC to use dhcp.

If dhcp is not available, i want a fix ip-number, gateway and so on..

How can i configure this in ubuntu? I didn't found anything in the docs.

Thanks.


(
_in gentoo it is:_
config_eth0=( "dhcp" )
dhcpcd_eth0="-N -t 5"

fallback_eth0=( "192.168.7.25 netmask 255.255.255.0" )
fallback_route_eth0=( "default via 192.168.7.40" )
)

---

### Post by mgor on 2006-07-07
couldn't find anything in the docs[0] either. the closest thing i found was to use mappings, also described in [0], though the map-scheme.sh script wasen't described there, but i found a guide[1] on google.

[0] interfaces(5)
[1] [http://www.shallowsky.com/linux/networkSchemes.html](http://www.shallowsky.com/linux/networkSchemes.html)

---

