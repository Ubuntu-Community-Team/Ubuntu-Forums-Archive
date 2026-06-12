---
title: "HDHomeRun, DHCP, to NIC staticly?"
date: 2009-10-19
forum: Multimedia Software
---

### Post by bgiannes on 2009-10-19
I have a HDHomeRun and a mythtv-backend.  I currectly have both the PC and the HDHomeRun connected to the same switch.  Both the PC and the HDHomeRun get there IP address from a router. the wrt-310n router has dd-wrt installed.

PC        192.168.1.100 eth0 (networkmanager)
HDHomeRun 192.168.1.110 

The PC has two nic, I'd like to setup a dhcp server on nic eth1 and have the HDHomeRun directly connect to it.  But i still would like the PC to get it's IP address from the router.

so i tryed installing dhcp, (i tryed following some howto's) but my setup must be a little different and the dhcp server will not startup??

network settings interface
> auto lo
iface lo inet loopback

auto eth1
iface eth1 inet static
address 192.254.10.1
netmask 255.255.255.0
#broadcast

dhcp.conf
>     option subnet-mask 255.255.255.0;
    option broadcast-address 192.168.10.255;
    option routers 192.168.10.1;
    option domain-name SOMENAME;
    option domain-name-servers 192.168.10.1;

    default-lease-time 600;
    max-lease-time 7200;

    # If this DHCP server is the official DHCP server for the local
    # network, the authoritative directive should be uncommented.
    authoritative;

    subnet 192.168.10.0 netmask 255.255.255.0 {
    range 192.168.10.10 192.168.10.100;
    }
# hdhomerun
group {
	# hdhomerun
	host hdhomerun {
		hardware ethernet 00:0c:41:1c:f4:04;
		}
	}

---

### Post by bgiannes on 2009-12-04
the answer is, networkmanager config file needs to be told not to manage eth1, then everything works. and it's address should be 192.168.10.1

---

