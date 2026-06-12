---
title: "Network bridge with VLANs"
date: 2011-11-06
forum: Networking &amp; Wireless
---

### Post by @Tony on 2011-11-06
All,

I'm having some issues configuring VLANs with bridging.  When there is no bridge defined everything works as it should.  As soon as I create a bridge the VLAN interface stops working.

Here is my working /etc/network/interfaces file without the bridge defined (IPs replaced with 0.0.0.0):

auto eth0
iface eth0 inet manual
        up ifconfig eth0 up

auto eth0.252
iface eth0.252 inet static
        address 0.0.0.0
        netmask 255.255.255.0
        gateway 0.0.0.0
        broadcast 0.0.0.255

auto eth1
iface eth1 inet manual
        up ifconfg eth1 up

auto eth1.254
iface eth1.254 inet static
        address 0.0.0.0
        netmask 255.255.255.0
        broadcast 0.0.0.255

Here is the non-working /etc/network/interfaces file with the bridge:

auto eth0
iface eth0 inet manual
        up ifconfig eth0 up

auto eth0.252
iface eth0.252 inet static
        address 0.0.0.0
        netmask 255.255.255.0
        gateway 0.0.0.0
        broadcast 0.0.0.255

auto eth1
iface eth1 inet manual
        up ifconfg eth1 up

auto eth1.254
iface eth1.254 inet static
        address 0.0.0.0
        netmask 255.255.255.0
        broadcast 0.0.0.255

auto br0
iface br0 inet manual
        bridge_ports eth1
        bridge_fd 9
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off

I am trying to use br0 to allow Virtual Machines access to the untagged network (eth1) while maintaining the host system's access to the 254 VLAN (eth1.254)

Any help would be greatly appreciated.  Thanks in advance.

---

### Post by datajack on 2012-01-17
Did you ever get to the bottom of this?

I have a similar problem and just had a brainwave whilst sketching out a post asking for help.



I had noticed that traffic outbound from the VLAN interface worked fine and could be observed on the network with the correct tag, just that incoming traffic was not finding it's way to the VLAN interface.

I have found that I can create a VLAN interface from the bridge device which seems to work. So in your case, try creating br0.254 instead of eth0.254.

---

### Post by @Tony on 2012-01-17
I haven't figured out this issue so far, I'll try creating VLAN interfaces on the bridges.  Thanks for the suggestion.  I've just been using macvtap interfaces which seems to work well enough.

---

