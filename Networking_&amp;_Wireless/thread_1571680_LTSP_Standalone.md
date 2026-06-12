---
title: "LTSP Standalone"
date: 2010-09-10
forum: Networking &amp; Wireless
---

### Post by jeight on 2010-09-10
I already have experience using both ltsp-standalone and ltsp-cluster servers. What I did today was installed the ltsp-standalone on my laptop connected to a router.  Here is the thing. I already had Ubuntu installed and got the ltsp-standalone package. Did my build and configured my dhcp and everything is set up fine except... Everytime I reboot my computer I have to manually restart the dhcp3 server and sometimes the networking daemon. I am having problems figuring out why.  Any ideas would be useful. 

File: /etc/ltsp/dhcpd.conf
authoritative;

subnet 192.168.2.0 netmask 255.255.255.0 {
    range 192.168.2.150 192.168.2.250;
    option domain-name "example.com";
    option domain-name-servers 192.168.2.1;
    option broadcast-address 192.168.2.255;
    option routers 192.168.2.1;
#    next-server 192.168.2.1;
#    get-lease-hostnames true;
    option subnet-mask 255.255.255.0;
    option root-path "/opt/ltsp/i386";
    if substring( option vendor-class-identifier, 0, 9 ) = "PXEClient" {
        filename "/ltsp/i386/pxelinux.0";
    } else {
        filename "/ltsp/i386/nbi.img";
    }
}


 File: /etc/network/interfaces
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

---

