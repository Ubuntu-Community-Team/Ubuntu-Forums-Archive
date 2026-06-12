---
title: "Dual Networks"
date: 2011-01-05
forum: Networking &amp; Wireless
---

### Post by chrisx on 2011-01-05
I use Ubuntu 10.10 Server in a classroom, a computer lab whose bandwidth is provided by a local cable ISP. The ISP router is connected to the WAN port of a four-port router. The server is plugged into a LAN port on the four-port router. The workstations in the classroom are plugged into a switch, and the switch is plugged into a LAN port on the four-port router.

But the school also provides a network, which I am not currently using. However, I would like to start using it to gain access to an IP printer. I have two network cards. eth0 is plugged into the four-port router.

The other NIC, eth1, could it be plugged into an Ethernet jack in the wall? I might receive by DHCP an IP address like  10.140.10.100, with the printer on maybe 10.120.50.10. I am considering an interfaces file like this:

```

auto lo
iface lo inet loopback

# First network card (attached to NAT router, attached to cable internet)
#
auto eth0
iface eth0 inet static
address 192.168.1.254
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1

# Second network card (attached to school network wall outlet)
#
auto eth1
iface eth0 inet dhcp 

```

I want none of the network except the printer. Thanks for any insight,

Chris

---

### Post by PatchesTheCaveman on 2011-01-05
I'm not sure how to get an IP address via DHCP but remove the gateway (which will stop it from routing packets to the Internet on that connection) in /etc/interfaces.  If you can get a static IP on the school network you can configure it and leave off the *gateway* line to achieve this.

But from the command-line you can run ```
sudo ip route del default dev eth1
``` to remove the route to the Internet via *eth1*.

You can add that to your /etc/rc.local file to make it run that command on every boot if nobody can chime in with the "right" way to do that:
```
sudo bash -c "echo ip route del default dev eth1 >> /etc/rc.local"
```

---

