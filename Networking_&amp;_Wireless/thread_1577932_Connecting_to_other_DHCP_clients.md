---
title: "Connecting to other DHCP clients"
date: 2010-09-19
forum: Networking &amp; Wireless
---

### Post by renopete on 2010-09-19
I've moved to a new place and only have wireless access.  Both my laptop and tower are now linked to the same wireless router, which I set up in an adjacent building, giving both systems internet access.  I develop and maintain websites and have development versions of them on my tower.  In the past I was able access them from either the tower or the laptop.  At that time I had DSL and a wireless router with four wired ports and used static IP address and virtual IP addresses on the wired connections.

Thought it would be simple to replicate this setup via my wireless connection to the router but am not having any luck.

ifconfig shows that my tower's dhcp allocated IP address is 192.168.1.102.  But when I ping that address from my laptop the response is:

ping 192.168.1.102
PING 192.168.1.102 (192.168.1.102) 56(84) bytes of data.
From 192.168.1.100 icmp_seq=1 Destination Host Unreachable

Same thing happens when running ping from the tower to IP address of the laptop.

Not sure if there's a setting on the wireless router that I need to change to allow dhcp clients to see each other.

I modified /etc/network/interfaces from:

  auto wlan0

to 

  auto wlan0
  iface wlan0 inet static
  address 192.168.1.59    
  gateway 192.168.1.1       # The address of the wireless router
  netmask 255.255.255.0     # Same as when on dhcp
  network  192.168.1.0        # Same as when on dhcp
  broadcast 192.168.1.255  # Same as when on dhcp

But when I run:

sudo /etc/init.d/networking restart

it responds:

 * Reconfiguring network interfaces...
SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
SIOCSIFNETMASK: No such device
SIOCSIFBRDADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Failed to bring up wlan0.

The connection comes up in DHCP mode.

Sooo...  what's the best way to let wireless dhcp clients connect to each other reliably and automatically. I don't want to have rely on dhcp having assigned a specific IP address to my tower and laptop.

I have various vague ideas, but figure it may be better to get advice from folks who know more about networking then I do.

-Pete

---

