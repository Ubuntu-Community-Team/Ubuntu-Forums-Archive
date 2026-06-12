---
title: "OpenVPN and a (semi)-persistent tap interface"
date: 2009-02-11
forum: Networking &amp; Wireless
---

### Post by soundhole on 2009-02-11
Hi.  This is my first post, so some hazing is to be expected. #-o

I have managed to configure OpenVPN in bridging mode on 8.04 Server such that it works really well when I start it from the command line.  It looks like it should restore the VPN when the machine reboots, but it doesn't.  In fact, if I reboot, then type:

```
% ifdown -a
% ifup -a
```

...then it *does* work again.  In response to ifdown, the message says that tap0 is not bound to br0 (& confirmed beforehand with brctl).  As part of setting the network up, I thought that I had created a persistent tap0 with:

% openvpn --mktun --dev tap0

but it doesn't seem to stick.  Here is my /etc/network/interfaces:

```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet manual

# The secondary network interface
auto eth1
iface eth1 inet manual

# The virtual network interface for OpenVPN
auto tap0
iface tap0 inet manual

# The bridge interface
auto br0
iface br0 inet dhcp
  bridge_ports eth0 eth1 tap0
  bridge_fd 9
  bridge_hello 2
  bridge_maxage 12
  bridge_stp on
```

and my version of openvpn.conf:

```
proto tcp
port 1194
dev tap0
ca /etc/easy-rsa/keys/ca.crt
cert /etc/easy-rsa/keys/VPN-Server.crt
key /etc/easy-rsa/keys/VPN-Server.key
dh /etc/easy-rsa/keys/dh2048.pem
ifconfig-pool-persist ipp.txt
server-bridge 192.168.1.15 255.255.255.0 192.168.1.101 192.168.1.119
comp-lzo
persist-key
persist-tun
status openvpn-status.log
verb 3
```

I've looked at the init.d scripts and the udev setup, and everything looks like it points back to ifupdown, which works, but only after the system is up.  Any ideas?

Thanks,

Ken

---

### Post by soundhole on 2009-02-12
I got it.  I created two files:

**/etc/network/if-pre-up.d/openvpn-create-tun0**
```
#!/bin/bash
#
# Create tap0 virtual network interface for OpenVPN
#
# Put this file in /etc/network/pre-up.d
#

openvpn --mktun --dev tap0
```
**/etc/network/if-post-down.d/openvpn-remove-tap0**
```
#!/bin/bash
#
# Create tap0 virtual network interface for OpenVPN
#
# Put this file in /etc/network/post-down.d
#

openvpn --rmtun --dev tap0

```

Now, after a reboot, the remote clients can see everything on the subnet, including the three VMs running under VirtualBox!

---

