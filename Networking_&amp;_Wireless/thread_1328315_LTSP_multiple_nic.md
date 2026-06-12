---
title: "LTSP multiple nic"
date: 2009-11-16
forum: Networking &amp; Wireless
---

### Post by anco on 2009-11-16
Dear All,

Today I tried a multiple nic on Ubuntu 9.10 LTSP i386. I did it before on 7.04 but I took me several hours to figure it out on 9.10. Main reason, very hard to google around for multiple nic setups with LTSP on latest version ubuntu.

Mostly single nic or two nic solutions are used with network extension with switch... However I happen to run into situations where for example only two or three clients are needed and one server in a single room, so adding a few nics or in my case an extra 4 port nic is much nicer when it comes to cabling an minimal devices that can break in a setup.

First I install the server in two nic configuration and than add users, check the server and finally add the extra nic cards as many as you need or can plugin your motherboard.

[B]The only two files to change are /etc/network/interfaces
[/B]

[I]# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth1
#iface eth1 inet dhcp

auto eth0
iface eth0 inet static
    address 192.168.2.254
    netmask 255.255.255.0
    network 192.168.2.0
    broadcast 192.168.2.255

auto eth2
iface eth2 inet static
    address 192.168.0.254
    netmask 255.255.255.0
    network 192.168.0.0
    broadcast 192.168.0.255

auto eth3
iface eth3 inet static
    address 192.168.3.254
    netmask 255.255.255.0
    network 192.168.3.0
    broadcast 192.168.3.255

auto eth4
iface eth4 inet static
    address 192.168.4.254
    netmask 255.255.255.0
    network 192.168.4.0
    broadcast 192.168.4.255

auto eth5
iface eth5 inet static
    address 192.168.5.254
    netmask 255.255.255.0
    network 192.168.5.0
    broadcast 192.168.5.255

[/I]


[B]and /etc/ltsp/dhcpd.conf
[/B]

[I]#
# Default LTSP dhcpd.conf config file.
#

authoritative;

subnet 192.168.0.0 netmask 255.255.255.0 {
    range 192.168.0.20 192.168.0.250;
    option domain-name "example.com";
    option domain-name-servers 192.168.0.1;
    option broadcast-address 192.168.0.255;
    option routers 192.168.0.1;
#    next-server 192.168.0.1;
#    get-lease-hostnames true;
    option subnet-mask 255.255.255.0;
    option root-path "/opt/ltsp/i386";
    if substring( option vendor-class-identifier, 0, 9 ) = "PXEClient" {
        filename "/ltsp/i386/pxelinux.0";
    } else {
        filename "/ltsp/i386/nbi.img";
    }
}

# ETH2 till ETH5 added Anco 16/11/09
authoritative;

subnet 192.168.2.0 netmask 255.255.255.0 {
    range 192.168.2.20 192.168.2.250;
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

authoritative;

subnet 192.168.3.0 netmask 255.255.255.0 {
    range 192.168.3.20 192.168.3.250;
    option domain-name "example.com";
    option domain-name-servers 192.168.3.1;
    option broadcast-address 192.168.3.255;
    option routers 192.168.3.1;
#    next-server 192.168.3.1;
#    get-lease-hostnames true;
    option subnet-mask 255.255.255.0;
    option root-path "/opt/ltsp/i386";
    if substring( option vendor-class-identifier, 0, 9 ) = "PXEClient" {
        filename "/ltsp/i386/pxelinux.0";
    } else {
        filename "/ltsp/i386/nbi.img";
    }
}


authoritative;

subnet 192.168.4.0 netmask 255.255.255.0 {
    range 192.168.4.20 192.168.4.250;
    option domain-name "example.com";
    option domain-name-servers 192.168.4.1;
    option broadcast-address 192.168.4.255;
    option routers 192.168.4.1;
#    next-server 192.168.4.1;
#    get-lease-hostnames true;
    option subnet-mask 255.255.255.0;
    option root-path "/opt/ltsp/i386";
    if substring( option vendor-class-identifier, 0, 9 ) = "PXEClient" {
        filename "/ltsp/i386/pxelinux.0";
    } else {
        filename "/ltsp/i386/nbi.img";
    }
}

authoritative;

subnet 192.168.5.0 netmask 255.255.255.0 {
    range 192.168.5.20 192.168.5.250;
    option domain-name "example.com";
    option domain-name-servers 192.168.5.1;
    option broadcast-address 192.168.5.255;
    option routers 192.168.5.1;
#    next-server 192.168.5.1;
#    get-lease-hostnames true;
    option subnet-mask 255.255.255.0;
    option root-path "/opt/ltsp/i386";
    if substring( option vendor-class-identifier, 0, 9 ) = "PXEClient" {
        filename "/ltsp/i386/pxelinux.0";
    } else {
        filename "/ltsp/i386/nbi.img";
    }
}
[/I]

Now after a reboot the thinclients seems to start on any interface (besides eth1 which is in my case the external network) but the login doesn't work. (server not responding message)

This is probably due to ssh keys or so because after next two commands my server works well.

sudo ltsp-update-sshkeys
sudo ltsp-update-image (don't know if this command was needed)

Now I have 5 ports on my server to connect thinclients, no extra switch needed.

I have written this in the hope i find it next time I need it and I hope some other people can use this information.

---

### Post by meadmarc on 2012-01-27
Perfect!  This is JUST what I need to know.  I wanted to distribute my thin client network across multiple network cards to load-balance the network better.  

One question, though-  what about my printers?  Those have fixed ip's, on the 192.168.0.X range.  What about my clients with 192.168.3.X or other IP's?  

Would I need to change the subnet mask to 255.255.251.0 to allow it to recognize the other ip ranges?

Thanks!

---

