---
title: "Ubuntu Router + Bridging Interfaces"
date: 2010-08-17
forum: Networking &amp; Wireless
---

### Post by Go3Team on 2010-08-17
Hello,

I'm setting up a computer I have lying around to act as my new router.  

eth0 - connects to cable modem

eth1, eth2 - should act like a switch - either interface should be seen as the gateway ie 192.168.1.1

I've tried bridge-utils, and it's not working as I thought it would, using plenty of How tos to get it working.  

Am I looking at it the wrong way, and do I need something other than bridge-utils?

Thanks.

---

### Post by redmk2 on 2010-08-17
> **Go3Team said:**
> Hello,

I'm setting up a computer I have lying around to act as my new router.  

eth0 - connects to cable modem

eth1, eth2 - should act like a switch - either interface should be seen as the gateway ie 192.168.1.1
You really can't use a NIC as a switch port.  No two NIC's (interfaces) can't have the same IP address.  A typical Ubuntu multi-homed host (multiple NIC's) will not allow multiple NIC's on the same subnet. > 

I've tried bridge-utils, and it's not working as I thought it would, using plenty of How tos to get it working. 

There is no need to bridge NIC's in the *same * Subnet.  They already can see each other via ARP.  Bridging allows NIC's with IP addresses in ***different ***subnets to be associated by MAC address.  I don't see how this would help you 

>  

Am I looking at it the wrong way, and do I need something other than bridge-utils?

I think you are looking at it incorrectly.> 

Thanks.

I believe what you are trying to do is connect multiple hosts to a router (gateway).  The best way is to use 2 NIC's and a true switch.  The router can be setup [**_this way_**]("https://help.ubuntu.com/community/Router").

Essentially you provide a NIC for the WAN side and a NIC for the LAN side (the default gateway interface).  Then you forward the packets.  If you are using private addressing you will also need to provide NAT'ing.  All of this is Layer 3 stuff (IP addressing).  The switch you connect provides the Layer 2 connectivity for the LAN (ethernet).  A Linksys router has all of these components  in one box.  It has both a switch (chip) and routing (chip +OS).

---

### Post by Go3Team on 2010-08-18
> **redmk2 said:**
> You really can't use a NIC as a switch port.  No two NIC's (interfaces) can't have the same IP address.  A typical Ubuntu multi-homed host (multiple NIC's) will not allow multiple NIC's on the same subnet. 
There is no need to bridge NIC's in the *same * Subnet.  They already can see each other via ARP.  Bridging allows NIC's with IP addresses in ***different ***subnets to be associated by MAC address.  I don't see how this would help you 

Essentially you provide a NIC for the WAN side and a NIC for the LAN side (the default gateway interface).  Then you forward the packets.  If you are using private addressing you will also need to provide NAT'ing.  All of this is Layer 3 stuff (IP addressing).  The switch you connect provides the Layer 2 connectivity for the LAN (ethernet).  A Linksys router has all of these components  in one box.  It has both a switch (chip) and routing (chip +OS).

The router set up listed above was what I based the build on.  I also need to add a wireless adapter, as the tutorial was shown using bridge-utils to accomplish that.  The router I built is using parts I have lying around.  My network is pretty much too mature for an over the counter (basic) router.  Being able to have a built in "switch" makes it far easier accomplish my goal of not spending any money on it.  I figured if DD WRT can do it with a mini version of linux, surely a full flavor could do it.  

So... When the interfaces file looks like this:
iface br0 inet static
    address 192.168.0.1
    network 192.168.0.0
    netmask 255.255.255.0
    broadcast 192.168.0.255
    bridge-ports eth1 wlan0

The bridge has an IP, does eth1 and wlan0 also have separate IPs as well?  I guess I'm expecting too much.

Thanks for the info.

---

### Post by nbkr on 2010-08-18
Of course you can bridge to nics to use them like a switch. 
First you have to create a new brdige

```

sudo brctl addbr br0

```

Now add the to interfaces to the bridge

```

sudo brctl addif br0 eth0
sudo brctl addif br0 eth1

```

The bridge is working now. If you want/need it you can activate STP on the bridge, set the aging of the learned mac adresses etc.

You can also use br0 like a normal interface and add an ip address to it using ifconfig or ip.

To turn the computer into a router will still have to activate IP forwarding using this command

```

echo 1 > /proc/sys/net/ipv4/ip_forward

```

You can make these changes permanent by adding a start up script or by modifing /etc/network/interfaces and /etc/sysctl.conf

However: Adding a WLAN Interface to the bridge often doesn't work because most WLAN-Cards don't accept other source mac-address than their own. So you have to be careful which card you buy.

---

### Post by Go3Team on 2010-08-19
> **nbkr said:**
> Of course you can bridge to nics to use them like a switch. 
First you have to create a new brdige

```

sudo brctl addbr br0

```

Now add the to interfaces to the bridge

```

sudo brctl addif br0 eth0
sudo brctl addif br0 eth1

```

The bridge is working now. If you want/need it you can activate STP on the bridge, set the aging of the learned mac adresses etc.

You can also use br0 like a normal interface and add an ip address to it using ifconfig or ip.

To turn the computer into a router will still have to activate IP forwarding using this command

```

echo 1 > /proc/sys/net/ipv4/ip_forward

```

You can make these changes permanent by adding a start up script or by modifing /etc/network/interfaces and /etc/sysctl.conf

However: Adding a WLAN Interface to the bridge often doesn't work because most WLAN-Cards don't accept other source mac-address than their own. So you have to be careful which card you buy.

Thanks nbkr! It's working great, and with an added script, persists on reboot.

Thanks a lot!

---

