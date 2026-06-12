---
title: "eth2 starts only when I login"
date: 2012-10-01
forum: Networking &amp; Wireless
---

### Post by vitke on 2012-10-01
I noticed that my colleagues cannot login to my computer over the network unles I am logged in. It seems that the network interface starts only when I login. If I login as root and I am not logged in as a user, there is no network. Here is what happens in syslog if I logout:

Oct  1 11:38:12 darcy acpid: client 6740[0:0] has disconnected
Oct  1 11:38:12 darcy acpid: client 6740[0:0] has disconnected
Oct  1 11:38:12 darcy acpid: client connected from 11054[0:0]
Oct  1 11:38:12 darcy acpid: 1 client rule loaded
Oct  1 11:38:12 darcy NetworkManager[1110]: <info> (eth2): device state change: activated -> disconnected (reason 'connection-removed') [100 30 38]
Oct  1 11:38:12 darcy NetworkManager[1110]: <info> (eth2): deactivating device (reason 'connection-removed') [38]
Oct  1 11:38:13 darcy NetworkManager[1110]: <info> (eth2): canceled DHCP transaction, DHCP client pid 10244
Oct  1 11:38:13 darcy avahi-daemon[1111]: Withdrawing address record for fe80::225:22ff:fe33:92ec on eth2.
Oct  1 11:38:13 darcy avahi-daemon[1111]: Leaving mDNS multicast group on interface eth2.IPv6 with address fe80::225:22ff:fe33:92ec.
Oct  1 11:38:13 darcy avahi-daemon[1111]: Interface eth2.IPv6 no longer relevant for mDNS.
Oct  1 11:38:13 darcy avahi-daemon[1111]: Withdrawing address record for 192.168.0.149 on eth2.
Oct  1 11:38:13 darcy avahi-daemon[1111]: Leaving mDNS multicast group on interface eth2.IPv4 with address 192.168.0.149.
Oct  1 11:38:13 darcy avahi-daemon[1111]: Interface eth2.IPv4 no longer relevant for mDNS.
Oct  1 11:38:13 darcy NetworkManager[1110]: <info> DNS: starting dnsmasq...
Oct  1 11:38:13 darcy dnsmasq[10262]: exiting on receipt of SIGTERM
Oct  1 11:38:13 darcy NetworkManager[1110]: <info> (eth2): writing resolv.conf to /sbin/resolvconf

and eth2 stops.

This is Ubuntu 12.10, upgraded several times during the past years. This problem existed a few years before I realised.

How can I make eth2 start during the boot?

---

### Post by albandy on 2012-10-01
> **vitke said:**
> I noticed that my colleagues cannot login to my computer over the network unles I am logged in. It seems that the network interface starts only when I login. If I login as root and I am not logged in as a user, there is no network. Here is what happens in syslog if I logout:

Oct  1 11:38:12 darcy acpid: client 6740[0:0] has disconnected
Oct  1 11:38:12 darcy acpid: client 6740[0:0] has disconnected
Oct  1 11:38:12 darcy acpid: client connected from 11054[0:0]
Oct  1 11:38:12 darcy acpid: 1 client rule loaded
Oct  1 11:38:12 darcy NetworkManager[1110]: <info> (eth2): device state change: activated -> disconnected (reason 'connection-removed') [100 30 38]
Oct  1 11:38:12 darcy NetworkManager[1110]: <info> (eth2): deactivating device (reason 'connection-removed') [38]
Oct  1 11:38:13 darcy NetworkManager[1110]: <info> (eth2): canceled DHCP transaction, DHCP client pid 10244
Oct  1 11:38:13 darcy avahi-daemon[1111]: Withdrawing address record for fe80::225:22ff:fe33:92ec on eth2.
Oct  1 11:38:13 darcy avahi-daemon[1111]: Leaving mDNS multicast group on interface eth2.IPv6 with address fe80::225:22ff:fe33:92ec.
Oct  1 11:38:13 darcy avahi-daemon[1111]: Interface eth2.IPv6 no longer relevant for mDNS.
Oct  1 11:38:13 darcy avahi-daemon[1111]: Withdrawing address record for 192.168.0.149 on eth2.
Oct  1 11:38:13 darcy avahi-daemon[1111]: Leaving mDNS multicast group on interface eth2.IPv4 with address 192.168.0.149.
Oct  1 11:38:13 darcy avahi-daemon[1111]: Interface eth2.IPv4 no longer relevant for mDNS.
Oct  1 11:38:13 darcy NetworkManager[1110]: <info> DNS: starting dnsmasq...
Oct  1 11:38:13 darcy dnsmasq[10262]: exiting on receipt of SIGTERM
Oct  1 11:38:13 darcy NetworkManager[1110]: <info> (eth2): writing resolv.conf to /sbin/resolvconf

and eth2 stops.

This is Ubuntu 12.10, upgraded several times during the past years. This problem existed a few years before I realised.

How can I make eth2 start during the boot?

Add these lines to /etc/network/interfaces

auto eth2
iface eth2 inet dhcp

---

### Post by Iowan on 2012-10-01
Network Connections should have options for "Connect automatically" and "Available to all users"

---

