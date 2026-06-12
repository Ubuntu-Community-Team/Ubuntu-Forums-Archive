---
title: "Getting two (2) nics to connect to 2 different networks"
date: 2011-02-10
forum: Networking &amp; Wireless
---

### Post by Princey on 2011-02-10
Hi, I'm running Kubuntu 10.10 although that shouldn't matter. I have two nics on my MSI 790FX-GD70 motherboard. I have two routers on two different networks. Network 1 with router 1 connects to the DLink with IP 10.20.30.xx which houses the Internet connection. Network 2, router 2 connects to a Linksys router 192.168.xxx.xx which runs my home theater system. 

Thing is I want to access both networks simultaneously. Currently, I must unplug network cable 2 to connect to the Internet. I access the home theater network ok fine. I know setting up a static IP for network 2 works on my Windows laptop but I can't get to do it under Linux. Any ideas?

---

### Post by Brandon Williams on 2011-02-10
I think that all you need is to make sure that you don't set an additional default gateway when you connect to the 192.168.*.* network. You only want a network route for that network, not a default route.

How are you managing the addresses? with network-manager or /etc/network/interfaces?

If it's with network-manager, then right-click on the icon, select "Edit connections ...", and edit the entry for "Auto eth1" (assuming that's the interface for 192.168.*.*). On the IPv4 settings tab, there is a button labelled "Routes...". Click that button and check the box that next to "Use this connection only for resources on its network", clock OK and then Apply.

If you use /etc/network/interfaces, then I only know how to handle this with static IPs instead of dhcp. With a static IP config, just don't specify a gateway for iface eth1. If you use dhcp, then you probably have to modify /etc/dhcp3/dhclient.conf in some way to avoid setting a default route when the 192.168.*.* interface is configured.

---

### Post by Princey on 2011-02-10
I rather use a static IP with network 2. However, the default network manager shipped with Kubuntu doesn't allow me to edit the connections. I remember years aback I could edit the network interfaces file but somehow lost how to do it. Any pointers?

---

### Post by Brandon Williams on 2011-02-11
Look for examples in /usr/share/doc/ifupdown/examples/network-interfaces.gz. A simple example of what you're trying to do would be:```
auto eth1
iface eth1 inet static
    address 192.168.N.N
    network 192.168.N.0
    netmask 255.255.255.0
    broadcast 192.168.N.255
```Note that I use 'N' wherever the number is going to be dependent on the specifics of your network setup. If you define the interface this way, with no gateway specified, then it should be the case that you end up with no default gateway added to the routing table when eth1 gets configured. If you don't want the interface to be configured automatically at boot, just remove the 'auto eth1' line and use 'sudo ifup' after you plug in the ethernet cable.

---

### Post by Princey on 2011-02-16
I edited the /etc/network/interfaces file and placed the information. When I restart the interface I keep getting this error message: > * Reconfiguring network interfaces...                                          /etc/network/interfaces:2: misplaced option
ifdown: couldn't read interfaces file "/etc/network/interfaces"
/etc/network/interfaces:2: misplaced option
ifup: couldn't read interfaces file "/etc/network/interfaces"


I've checked and verified to see if the file exists and it does. Here's the current contents:
> auto lo
face l inet loopback
auto eth0
iface eth0 inet static
address 192.168.35.34
network 192.168.35.1
netmask 255.255.255.192
broadcast 192.168.35.255

Note, it's eth0 I'm trying to make static and leave eth1 as DHCP controlled.

---

### Post by Brandon Williams on 2011-02-16
It looks like the line that defines the loopback interface got corrupted somehow. Line 2 (that's what the 2 means in the error message) should be:
```
iface lo inet loopback
```

---

### Post by Princey on 2011-02-17
I did that, I'm connecting to the internet now, but while ifconfig shows it's working, network manager reports it has no ip address. Should I just ignore network manager? 

P.S. I can connect to the other network with my streaming just fine. Thanks by the way for the help.

---

### Post by Hawkoon on 2011-02-17
I have a similar setup here, wifi and nic connecting to two different networks. I skipped the 'network' and 'broadcast' line for the static ip in /etc/network/interfaces, and I also have network manager reporting only one connection. But it has been working great for many months.

---

### Post by Brandon Williams on 2011-02-17
Yes, ignore network-manager for that interface. If it's in /etc/network/interfaces, then network-manager isn't managing it anyway. And regardless of which system is managing it, ifconfig is the authoritative source.

---

