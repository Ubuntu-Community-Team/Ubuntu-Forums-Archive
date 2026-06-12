---
title: "Need some help"
date: 2009-04-24
forum: Networking &amp; Wireless
---

### Post by rokar on 2009-04-24
I'm trying to set a static IP address for my server. It has 2 Ethernet connections. I went into my interface file edited like this. I added my second interface because it was not there.

auto eth0
iface eth0 inet static
        address 192.168.0.100
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1

auto eth1
iface eth1 inet static
        address 192.168.0.101
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1[FONT=Verdana]

I did some messing with my /etc/hosts it looks like this:
     127.0.0.1     localhost
     192.168.0.100     snoopy.wi.rr.com     snoopy

My /etc/resolv.conf file is this:
     domain  wi.rr.com
     search  wi.rr.com
     nameserver 192.168.0.1

Is there something I am missing? I ssh into it fine. It just cant get out to the web. Any help is greatly appreciated.
Thanks!!

-Jon 
[/FONT]

---

### Post by Iowan on 2009-04-24
Although I've seen some threads about bridging (which I still don't understand), it generally seems like trouble to have two interfaces in the same subnet (192.168.0.0/24) - seems to confuse routing.

---

