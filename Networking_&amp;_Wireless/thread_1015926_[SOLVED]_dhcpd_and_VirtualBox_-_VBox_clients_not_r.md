---
title: "[SOLVED] dhcpd and VirtualBox - VBox clients not receiving leases"
date: 2008-12-19
forum: Networking &amp; Wireless
---

### Post by ziesemer on 2008-12-19
I've already seen and read many other posts that address VirtualBox and DHCP, but I think this one is a little different.  I also would have posted this to a VirtualBox or related forum, but it seems that most of the issue I'm having is specific to Ubuntu's networking configuration.

Starting with the simple case, I have my Ubuntu Intrepid Ibex (8.10) server.  It is setup with a static IP address for eth0 (and now br0), and dhcp3-server (3.1.1-1ubuntu2) for serving IPv4 addresses to the LAN - all working great.

I now installed VirtualBox 2.0.6 on this same box, intending to run a Windows XP SP3 guest.  I followed the instructions in the VirtualBox documentation for setting up host networking with a bridge.

This is what I have in my /etc/network/interfaces file:

```

auto lo
iface lo inet loopback

auto br0
iface br0 inet static
	address 192.168.x.1
	netmask 255.255.255.0
	bridge_ports eth0 vbox0

auto eth0
iface eth0 inet manual
	up ifconfig $IFACE 0.0.0.0 up
	up ip link set $IFACE promisc on
	down ifconfig $IFACE down

auto vbox0
iface vbox0 inet manual
	up ifconfig $IFACE 0.0.0.0 up
	down ifconfig $IFACE down
	tunctl_user mark

```

Originally, I had removed the "eth0" section after creating br0.  I then added it to try adding the promisc mode, as I've seen frequently suggested elsewhere online - but it doesn't seem to help.

I've confirmed that vbox0 and eth0 are both part of the bridge:

```

$ /usr/sbin/brctl show
bridge name	bridge id		STP enabled	interfaces
br0		8000.00301b46de09	no		eth0
							vbox0

```

However, I'm unable to receive any DHCP addresses from within the VirtualBox guest, with the guest configured to use vbox0.

If I manually configure an IP within the guest, everything works as expected - so I definitely appear to have proper IP connectivity and a functioning bridge.

Other computers on the LAN connected to eth0 also continue to successfully receive DHCP leases.

I've also completely opened everything in my iptables rules, just to make sure it wasn't interfering.

Could someone explain why I should or should not need to enable promiscuous mode on one or more interfaces for this to work?  It isn't needed for "normal" DHCP for the LAN.  If it is needed, why eth0 (as everything else I've found seems to suggest) instead of or in addition to br0 or vbox0?

Anything else I should be checking / changing?

THANKS!

---

### Post by ziesemer on 2008-12-26
Seems like I just needed to re-order /etc/network/interfaces so that the individual interfaces are brought up before the bridge.

Additionally, contradictory to many of the other notes I had found, promiscuous mode doesn't need to be enabled for any of the interfaces for this to work properly.

---

