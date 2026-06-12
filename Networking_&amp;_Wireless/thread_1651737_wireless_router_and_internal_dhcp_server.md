---
title: "wireless router and internal dhcp server"
date: 2010-12-23
forum: Networking &amp; Wireless
---

### Post by wcorey on 2010-12-23
I have a machine running U10.10 Desktop. It gets its address from a wireless router serving the 192.168.0 subnet. This works fine, all wireless clients, laptop, smartphone, tivos, etc get their addresses assigned from that. All is good.

I added a second nic such that this machine can be cluster controller (and cloud controller, and storage controller) Short of issuing 

> sudo ifconfig eth1 192.168.1.1 netmask 255.255.255.0 up


It never gets an address. I am trying to set up a dhcp server to do this but that doesn't work as expected.

The eth1 does not get an addr until I perform the above ifconfig cmd.

The dhcp3.conf is 

 subnet 192.168.1.0 netmask 255.255.255.0 {
        range 192.168.1.2 192.168.5.254;
        option broadcast-address 192.168.1.255;
        option domain-name-servers 192.168.1.1;
        option domain-name localdomain;
        default-lease-time 1800;                # default is 30 minutes
        max-lease-time 7200;                    # default is 2 hours
}
host uec1 {
        hardware ethernet 00:10:18:09:af:40;
        fixed-address 192.168.1.1;
        option domain-name-servers 0.0.0.0;
        option domain-name "";
}

Any thoughts?

And why, in the absence of the directed sudo ifconfig
does the system insist on creating an eth1.avahi which has an ipv4 address of some made up address????

Thanks,

---

### Post by slooow on 2010-12-23
Is the eth1 interface plugged into the router too? You need to explain the layout of your network a bit more. A dhcp server gives IP addresses to its clients.

---

