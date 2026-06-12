---
title: "OpenVPN server not starting"
date: 2009-09-03
forum: Networking &amp; Wireless
---

### Post by supradave on 2009-09-03
I followed the instructions at:

[https://help.ubuntu.com/community/OpenVPN](https://help.ubuntu.com/community/OpenVPN)

and can't get it to start.

```

sudo /etc/init.d/openvpn restart
* Stopping virtual private network daemon(s)...    
*   No VPN is running.
* Starting virtual private network daemon(s)...    
*   Autostarting VPN 'server'                 [fail] 

```

Whatever the problem is, the Cannot resolve host address is bugging me.  I don't know what it's trying to resolve.

/var/log/syslog:
```

Thu Sep  3 15:07:26 2009 us=291637 OpenVPN 2.1_rc11 i486-pc-linux-gnu [SSL] [LZO2] [EPOLL] [PKCS11] built on Mar  9 2009
Thu Sep  3 15:07:26 2009 us=291945 NOTE: when bridging your LAN adapter with the TAP adapter, note that the new bridge adapter will often take on its own IP address that is different from what the LAN adapter was previously set to
Thu Sep  3 15:07:26 2009 us=320877 Diffie-Hellman initialized with 1024 bit key
Thu Sep  3 15:07:26 2009 us=340266 /usr/bin/openssl-vulnkey -q -b 1024 -m <modulus omitted>
Thu Sep  3 15:07:26 2009 us=843114 Control Channel Authentication: using 'ta.key' as a OpenVPN static key file
Thu Sep  3 15:07:26 2009 us=843243 Outgoing Control Channel Authentication: Using 160 bit message hash 'SHA1' for HMAC authentication
Thu Sep  3 15:07:26 2009 us=843279 Incoming Control Channel Authentication: Using 160 bit message hash 'SHA1' for HMAC authentication
Thu Sep  3 15:07:26 2009 us=843350 TLS-Auth MTU parms [ L:1574 D:166 EF:66 EB:0 ET:0 EL:0 ]
Thu Sep  3 15:07:26 2009 us=845267 RESOLVE: Cannot resolve host address: <your: [HOST_NOT_FOUND] The specified host is unknown.
Thu Sep  3 15:07:26 2009 us=845408 Exiting

```

Here's my /etc/network/interfaces
```

cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto br0
iface br0 inet static 
	address 192.168.254.139
	netmask 255.255.255.0
	gateway 192.168.254.1
	bridge_ports eth0

auto eth1
iface eth1 inet dhcp

iface eth0 inet manual
	up ifconfig $IFACE 0.0.0.0 up
	up ip link set $IFACE promisc on
	down ip link set $IFACE promisc off
	down ifconfig $IFACE down

```

Let me know if you need any more information.

Thanks,
Dave

---

### Post by jonobr on 2009-09-03
just a wag

but looking at the notes, the only place it mentions hostname is in editing 


/etc/openvpn/server.conf
local <your ip address> ## ip/hostname of server

What did you put in here?

Did you put in ip or hostname?
If its hostname, does it match when you type in 

hostname in the terminal window

---

### Post by supradave on 2009-09-04
You would think that I would have noticed that.  Do I feel sheepish or what?

Thanks.

---

### Post by jonobr on 2009-09-04
Was it empty?
Did you populate it and it worked?

Should I start to pat myself on the back??????

:)

---

