---
title: "calling all shorewall experts I need some help configuring"
date: 2009-08-30
forum: Networking &amp; Wireless
---

### Post by sefs on 2009-08-30
The machine has one interface card br0

On this machine is a openvpn, so tap0 and eth0 are bridged to br0

when a client connects via vpn to to lan it can ping the vpn server but no other machines on the lan. Ping returns unreachable

here are are the files from /etc/shorewall

Zones
```

###############################################################################
#ZONE	TYPE	OPTIONS			IN			OUT
#					OPTIONS			OPTIONS
fw	firewall
net	ipv4
loc:net	ipv4
vpn:loc ipv4

```

Interfaces
```

#ZONE	INTERFACE	BROADCAST	OPTIONS
net     br0            	detect          dhcp,tcpflags,logmartians,nosmurfs

```

Tunnels
```

#TYPE		ZONE		GATEWAY		GATEWAY ZONE

openvpn		net		0.0.0.0/0	 vpn

```

Rules
```

#ACTION		SOURCE		DEST		PROTO	DEST	SOURCE		ORIGINAL	RATE		USER/	MARK
#							PORT	PORT(S)		DEST		LIMIT		GROUP

# Reject Ping from the "bad" net zone.. and prevent your log from being flooded..

Ping/REJECT	net		$FW

# Permit all ICMP traffic FROM the firewall TO the net zone

ACCEPT		$FW		net		icmp

# Permit custom connections

SSH/ACCEPT	net		$FW
ACCEPT		net		$FW		udp	1194

```

Policy (I have no idea what is going on here so i am just adding things at random  to see if they work..
```

#SOURCE		DEST		POLICY		LOG LEVEL	LIMIT:BURST
$FW		all		ACCEPT
vpn		$FW		ACCEPT
vpn		all		ACCEPT
loc		$FW		ACCEPT
loc		all		ACCEPT
net		$FW		DROP		info
net		all		DROP		info
# The FOLLOWING POLICY MUST BE LAST
all		all		REJECT		info

```


... So after a whole day of pouring over the documentation I am no further.

---

