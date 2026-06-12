---
title: "Dot1q module"
date: 2012-09-26
forum: Networking &amp; Wireless
---

### Post by Nuul on 2012-09-26
I'm setting up a GNS3 lab at work on Ubuntu Server 12.04 x64.  I have a few questions on how the dot1q module works along with the /etc/network/interfaces file.

What I'm trying to accomplish:
[LIST]
[*]The trunk interface and all it's sub interfaces (eth6) should not have an IP - just a layer 2 interface.
[*]The interface i use for SSH (eth2) to connect to the box shouldn't be trunking.
[*]The MTU on the trunk interface should be 1536.  This gives me enough overhead to do qinq.
[/LIST]

The problem I'm having is that when using 'inet static' in /etc/network/interfaces it doesn't seem to like that I'm not specifying an IP address.  Yes, I could always set this use a 127.0.0.8/8 address but I'm trying to keep it a layer 2 only interface if possible.  Also, the MTU size doesn't seem to stick, but I'm pretty sure this is because it errors out when there is no ip assigned.  As for the dot1q module, it is only loaded when I speficy a sub interface, correct?  For example, I have an eth6.99 interface that should be trunking but I don't want eth2 to be doing so.  

/etc/network/interfaces
```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth2
iface eth2 inet dhcp

#Trunk interface to Lab Switches
auto eth6
iface eth6 inet static
mtu 1536

#VLAN 99 on eth6
auto eth6.99
iface eth6.99 inet static
mtu 1536
```

/etc/modules
```
#/etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.
loop
lp
rtc
#Load 802.1q module for breakout switch
8021q
```

---

### Post by Nuul on 2012-10-01
I found the answer.

I was right that when using 'static' in /etc/network/interfaces you MUST specify an IP address.  The trick is to set it to 'manual'

/etc/network/interfaces
```
# The primary network interface
auto eth2
iface eth2 inet dhcp

#dot1q interface
auto eth6
iface eth6 inet manual
```

What I needed to do was add another script to do the heavy lifting for all my sub interfaces attached to eth6.

/home/nuul/GNS3/VLANup.sh (this has to be run with elevated privileges obviously)
```
# Bring up the physical interface
ifconfig eth6 up
ifconfig eth6 mtu 7000

# Add subs
ip link add link eth6 name eth6.101 type vlan id 101
ip link add link eth6 name eth6.102 type vlan id 102

# Bring up subs
ifconfig eth6.101 up
ifconfig eth6.102 up

# Set MTU on subs
ifconfig eth6.101 mtu 1536
ifconfig eth6.102 mtu 1536

```

---

