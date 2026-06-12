---
title: "Why is my vlan not working?"
date: 2013-03-02
forum: Networking &amp; Wireless
---

### Post by Chrus on 2013-03-02
Trying to set up my network so I have 2 or 3 vlans so I can play around with QOS and what can be accessed and junk.

I have eth0 connected to my modem and eth1, eth2, and eth3 in bridge mode (br0). eth1 is connected to port 10 on my switch. I've got an access point in port 6 on the switch - thats set up with 2 SSID's, the plan is to have them on separate vlan's.

At the moment, I've got port 4 set to VLAN 20 TAGGED and port 10 set to VLANs 1 and 20 UNTAGGED. All other set to 1 UNTAGGED.

VLAN 1 is on 172.20.10.0
VLAN 20 is on 172.20.20.0

VLAN 1 works without any issue... However, vlan 20 has given me nothing at all.

Im sure there's something simple I'm overlooking here.

/etc/network/interfaces:
```

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 172.20.5.10
        netmask 255.255.255.0
        network 172.20.5.0
        broadcast 172.10.5.255
        gateway 172.20.5.1
        up /usr/local/firewall.sh

auto br0
iface br0 inet static
    address 172.20.10.1
    netmask 255.255.255.0
    network 172.20.10.0
    broadcast 172.20.10.255
    pre-up ifconfig eth1 down
    pre-up ifconfig eth2 down
    pre-up ifconfig eth3 down
    pre-up brctl addbr br0
    pre-up brctl addif br0 eth1
    pre-up brctl addif br0 eth2
    pre-up brctl addif br0 eth3
    pre-up ifconfig eth1 0.0.0.0
    pre-up ifconfig eth2 0.0.0.0
    pre-up ifconfig eth3 0.0.0.0
    post-down ifconfig eth1 down
    post-down ifcongig eth2 down
    post-down ifconfig eth3 down
    post-down brctl delif br0 eth1
    post-down brctl delif br0 eth2
    post-down brctl delif br0 eth3
    post-down brctl delbr br0
    up /usr/local/firewall.sh

auto br0.20
iface br0.20 inet static
    vlan-raw-device br0
    address 172.20.20.1
    netmask 255.255.255.0
    network 172.20.20.0
    broadcast 172.20.20.255
    up /usr/local/firewall.sh

#auto br0.30
#iface br0.30 inet static
#    vlan-raw-device br0
#    address 172.20.30.1
#    netmast 255.255.255.0
#    network 172.20.30.0
#    broadcast 172.20.30.255
#    up /usr/local/firewall.sh


auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider
up /usr/local/firewall.sh

```

Anyone have any ideas why this isnt working?

Happy to provide more details if needed.

Thanks.

---

### Post by Chrus on 2013-03-03
bumping

---

