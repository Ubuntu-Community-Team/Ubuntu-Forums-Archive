---
title: "Setting up a simple DHCP server"
date: 2012-01-27
forum: Networking &amp; Wireless
---

### Post by Red0x on 2012-01-27
I am trying to set up a very simple DHCP server using dhcpd. I followed the instructions at [https://help.ubuntu.com/community/dhcp3-server](https://help.ubuntu.com/community/dhcp3-server) but I am getting an error:

```
me@mycomp:~$ sudo service isc-dhcp-server restart
 * Stopping ISC DHCP server dhcpd                                        [fail] 
 * Starting ISC DHCP server dhcpd                                          [fail]
 * check syslog for diagnostics.
```

In syslog:

```
Jan 27 19:11:17 mycomp dhcpd: No subnet declaration for eth0 (no IPv4 addresses).
Jan 27 19:11:17 mycomp dhcpd: ** Ignoring requests on eth0.  If this is not what
Jan 27 19:11:17 mycomp dhcpd:    you want, please write a subnet declaration
Jan 27 19:11:17 mycomp dhcpd:    in your dhcpd.conf file for the network segment
Jan 27 19:11:17 mycomp dhcpd:    to which interface eth0 is attached. **
```My /etc/default/isc-dhcp-server file:

```
INTERFACES="eth0"
```

My /etc/dhcp/dhcpd.conf file:

```
default-lease-time 600;
max-lease-time 7200;

subnet 192.168.2.0 netmask 255.255.255.0 {
range 192.168.2.10 192.168.2.100;
option subnet-mask 255.255.255.0;
option broadcast-address 192.168.2.255;
option routers 192.168.2.1;
}
```

My eth0 is a wired ethernet connection with static IP 192.168.2.1, mask 255.255.255.0, default gateway 192.168.2.1.

The syslog error is confusing. I am declaring a subnet mask in my dhcpd.conf file (at least I think I am) so I don't understand where I'm going wrong. Google and forum searches weren't much help.

---

### Post by Red0x on 2012-01-28
Solved.

The problem was that my /etc/network/interfaces files was missing an entry for my interface, eth0:

```
auto eth0
iface eth0 inet static
    address 192.168.2.1
    netmask 255.255.255.0
```

I thought setting these IP values in the Ubuntu connections manager would be enough, but it wasn't.

---

### Post by mörgæs on 2012-01-28
Good, then please mark the thread 'solved' using 'thread tools'.

---

