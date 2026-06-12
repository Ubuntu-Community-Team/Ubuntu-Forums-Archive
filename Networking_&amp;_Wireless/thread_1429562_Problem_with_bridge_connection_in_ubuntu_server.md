---
title: "Problem with bridge connection in ubuntu server"
date: 2010-03-14
forum: Networking &amp; Wireless
---

### Post by aquavitae on 2010-03-14
I'm running ubuntu server (9.10) at home as a home server, and I've got a bridge connection setup so that I can use wireless or ethernet.  I've read just about every guide on the internet for setting this up, but I'm still having some problems. The first problem is that I can't connect through the wired connection. Wireless works fine, but the syslog (grep eth0 /var/log/syslog) shows
```
Mar 14 15:23:30 ubuntu-server kernel: [    1.928696] eth0: RealTek RTL8139 at 0xd400, 00:40:95:30:4c:37, IRQ 18
Mar 14 15:23:33 ubuntu-server kernel: [   14.988373] device eth0 entered promiscuous mode
Mar 14 15:23:33 ubuntu-server kernel: [   15.003697] eth0: link down
Mar 14 15:23:33 ubuntu-server kernel: [   15.003831] ADDRCONF(NETDEV_UP): eth0: link is not ready
```

The second problem is that the connection takes about 15 seconds to come up - i.e. 15s between the first mention of br0 and the line saying that br0 has an address. The problem with this is that while br0 is procrastinating, the dhcp server tries to start, finds that the broadcast interface (br0) has an ip address 0.0.0.0, and bails.

Here is the output of 'grep br0 /var/log/syslog':
```

Mar 14 15:23:33 ubuntu-server kernel: [   15.073970] br0: port 2(wlan0) entering learning state
Mar 14 15:23:34 ubuntu-server kernel: [   16.170564] br0: port 2(wlan0) entering disabled state
Mar 14 15:23:34 ubuntu-server kernel: [   16.224466] br0: port 2(wlan0) entering learning state
Mar 14 15:23:35 ubuntu-server avahi-daemon[707]: Registering new address record for fe80::222:b0ff:fee8:f5d9 on br0.*.
Mar 14 15:23:44 ubuntu-server kernel: [   25.736014] br0: no IPv6 routers present
Mar 14 15:23:49 ubuntu-server kernel: [   31.224020] br0: port 2(wlan0) entering forwarding state
Mar 14 15:23:49 ubuntu-server avahi-daemon[707]: Joining mDNS multicast group on interface br0.IPv4 with address 10.10.10.1.
Mar 14 15:23:49 ubuntu-server avahi-daemon[707]: New relevant interface br0.IPv4 for mDNS.
Mar 14 15:23:49 ubuntu-server avahi-daemon[707]: Registering new address record for 10.10.10.1 on br0.IPv4.
Mar 14 15:23:49 ubuntu-server avahi-daemon[707]: Withdrawing address record for 10.10.10.1 on br0.
Mar 14 15:23:49 ubuntu-server avahi-daemon[707]: Leaving mDNS multicast group on interface br0.IPv4 with address 10.10.10.1.
Mar 14 15:23:49 ubuntu-server avahi-daemon[707]: Interface br0.IPv4 no longer relevant for mDNS.
Mar 14 15:23:49 ubuntu-server avahi-daemon[707]: Joining mDNS multicast group on interface br0.IPv4 with address 10.10.10.1.
Mar 14 15:23:49 ubuntu-server avahi-daemon[707]: New relevant interface br0.IPv4 for mDNS.
Mar 14 15:23:49 ubuntu-server avahi-daemon[707]: Registering new address record for 10.10.10.1 on br0.IPv4.

```

And here is the contents of /etc/network/interfaces

```

auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet manual
        wireless-mode ad-hoc
        wireless-essid UbuntuHome

auto br0
iface br0 inet static
        address 10.10.10.1
        network 10.10.10.0
        netmask 10.10.10.0
        broadcast 10.10.10.255
        bridge_ports eth0 wlan0

```

---

### Post by aquavitae on 2010-03-14
Ok, slightly embarrasing update. I eventually discovered the problem with eth0 - I'd forgotten to plug in the cable :oops:

But I still don't know why br0 takes so long to come up.  Any other files or logs I should post?

---

