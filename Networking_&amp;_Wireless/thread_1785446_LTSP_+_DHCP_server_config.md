---
title: "LTSP + DHCP server config"
date: 2011-06-18
forum: Networking &amp; Wireless
---

### Post by afd on 2011-06-18
Hi.

I'm helping reconfigure an office and they have an LTSP server which also acts as a domain server.

When I plug a workstation directly in to the LTSP the DHCP kicks in, the IP address is given & the workstation boots to the given OS.

When I try to do the same thing through a switch it does not.

Here is the LTSP config file found at /etc/ltsp/dhcpd.conf


```
#
# Default LTSP dhcpd.conf config file.
#

authoritative;

subnet 10.1.0.0 netmask 255.255.255.0 {
    range 10.1.0.100 10.1.0.200;
    option domain-name "example.com";
    option domain-name-servers 8.8.8.8;
    option broadcast-address 10.1.0.255;
    option routers 10.1.0.1;
 #   next-server 192.168.1.4;
#    get-lease-hostnames true;
    option subnet-mask 255.255.255.0;
    option root-path "/opt/ltsp/i386";
    if substring( option vendor-class-identifier, 0, 9 ) = "PXEClient" {
        filename "/ltsp/i386/pxelinux.0";
    } else {
        filename "/ltsp/i386/nbi.img";
    }
}
```

I am guessing that the switch needs configuring to allow all traffic between the workstations & the LTSP but I wanted to rule out a misconfiguration of the LTSP as well.

Thanks

---

### Post by Rakeshvijayan on 2011-07-05
any one help me to configure this LTSP  .or give me your configuration file.

---

