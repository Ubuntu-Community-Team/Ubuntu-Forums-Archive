---
title: "2 NICs, same network"
date: 2009-03-03
forum: Networking &amp; Wireless
---

### Post by Redalert Commander on 2009-03-03
Hi,

I have dual gigabit ethernet in my machine (Asus P5Q3 motherboard and running ubuntu 8.10), and want to use both as efficient as possible on the same network.
Unfortunatly bonding is not possible due to switch limitations.

My previous setup was working fine, until I tinkered with the modem/router.
Previously:
- each of the NIC's connected to the same gigabit switch
- each had their own dhcp assigned IP, and would be able to work independently.
- eth0: 10.0.0.40/24
- eth1: 10.0.0.41/24
The resulting route looked a bit like this:
destination gateway interface
10.0.0.0/24 *   eth0
10.0.0.0/24 *   eth1
* 10.0.0.138    eth1
This was achieved with standard settings using network-manager, resulting in internet traffic going over eth1 and internal network over eth0

That was working great, until now, it now gives a very unstable connection, fails from time to time, unplugging or disabling any of both interfaces results in normal traffic again.

Also, using wireshark, I can see packets destined for 10.0.0.41 when monitoring eth0, and vice versa.

Quick old setup (I left other devices out, this is only between the wall and my pc):
ASDL modem/router(both dhcp and dns server) -> gbps switch -> 100Mbps switch -> gbps switch -> pc

New:
ADSL modem/router in bridge mode -> server with 100Mbps card for the internet connection using PPPoE, Gbps NIC for LAN (debian etch, has a dhcp and DNS server set up) -> gbps switch -> 100Mbps Switch -> gbps switch -> pc

The dhcp and DNS services seem to be working fine, and I can see any real difference in both setups, as seen from my pc. All other devices on the network appear to be working correctly. Only my pc (the only one with dual gigabit ethernet seems to have issues when both interfaces are operational.
Even an SSH session to the server seems to have pauzes from time to time, for about 15 seconds, then resumes normal operation, for another 30 - 40 seconds.

Any help would be greatly appreciated,
RC

---

### Post by Crafty Kisses on 2009-03-03
I'm not quite sure what you're asking. I'm aware you want to use both NICs as efficiently as possible, but are you going for something like a Network bond?

---

### Post by Redalert Commander on 2009-03-04
No, as mentionded, bonding is not possible unfortunatly, the switch is unable to handle a bond.

The 2 interfaces are to act completely independantly, but are on the same network, each has their own IP and MAC.

thus what I want is that 1 interface is used for internet traffic, and the other for LAN traffic.
This was working previously, but not since I changed the server and modem/router.

What I want is something like this:
- traffic for LAN -> eth0
- traffic for internet -> eth0

this was achieved in the most simple way, see the routing table in my previous post.
the top entry takes priority over lower entries, so traffic was divided across them.

But now for some reason this setup is failing, and instead of completely separate devices, they seem to be entangled a bit, getting each others packages, yet no bond is configured, each has a different IP and MAC address. Connections to both the internet and the server fail/hang regulary. However disconnecting any of the 2 will cause everything to work as expected.

Both interfaces receive their info from the same dhcp server, getting the same gateway, subnet masks, dns server etc.. but ofcourse another IP (40 and 41)

---

### Post by HDave on 2009-05-29
Same issue here...did you ever resolve this?

---

### Post by Redalert Commander on 2009-06-11
unfortunately no.
I have switched to debian lenny on the desktop atm, wich gives an interesting new view.
1 interface gets disabled automatically, even when the network manager applet isn't started. All traffic goes over 1 pipe, I can switch them in network applet, but then the other one loses it's IP.
Configured both in /etc/network/interfaces for DHCP, disabled the network manager applet, yet the same result. At least this behavior is better than the one I had with Ubuntu. (the connection is stable now, I think it was a bug somewhere in Ubuntu)
 As I see it now on Lenny, the second interface gets disabled because they are on the same network (can someone with better understanding confirm this?). The second will only go up in case the first comes down, as a failover.

I didn't try any special configuration yet though.

Edit: I see an error in my previous post(the internet should go with eth1, not eth0):

What I want is something like this:
- traffic for LAN -> eth0
- traffic for internet -> eth1

---

### Post by ericab on 2009-06-24
can someone shed some light on how to accomplish this ? i would like to accomplish the exact same thing as Redalert Commander

---

### Post by Redalert Commander on 2009-06-29
I currently use a bond with mode 6 (doesn't need switch support), which seems to be working nicely, it's not the same as I described, but at least it seems better on high loads than a single interface.

My current /etc/network/interfaces file:
```
auto lo
iface lo inet loopback

auto eth0
auto eth1
auto bond0
iface bond0 inet dhcp
	hwaddress ether 00:1d:xx:xx:xx:xx
	bond_mode 6
	bond_miimon 100
	bond_downdelay 200
	bond_updelay 200
	slaves eth0 eth1

```
where the mac address is the one from eth0 (needed because the dhcp assigns the address, and there are ports forwarded to that IP)

I also added 'mii' to the /etc/modules file.
Then I had to disable some automatic networking tools which are provided with a default desktop installation.
In /etc/init.d
```

update-rc.d -f network-manager remove
update-rc.d -f network-manager-dispatcher remove

```
and I disabled the network manager applet in System - Preferences - Session (nm-applet)

No issues up so far. Of course rebooting or restarting the network service is required: /etc/init.d/networking restart 

PS: everything in this post, except for disabling the nm-applet, requires root access.

PPS: most of the info, I got from: [http://www.howtoforge.com/nic-bonding-on-debian-lenny](http://www.howtoforge.com/nic-bonding-on-debian-lenny)

---

