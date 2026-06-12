---
title: "Configure static IP - use of 'network'?"
date: 2011-04-15
forum: Networking &amp; Wireless
---

### Post by PA-J3Cub on 2011-04-15
Hello all. I'm setting up a home webserver with Ubuntu 10.10 and want to configure the interface to static. I'm using a router, which is setup and working correctly. I have been using linux workstation with dhcp for some time.

I've edited my interfaces file to reflect the parameters for setting static ip, with the exception of 'network'. No matter what I put into this setting, it causes me to loose connectivity to the outside world. I've tried to put my router IP, and my IP set by my provider. What should the 'network' value be?

At this time, my 'interfaces' files only includes the following and has connectivity out to the internet:

```

#The loopback network interface
auto lo
iface lo inet loopback
# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.2.120
        netmask 255.255.255.0
        broadcast 192.168.2.255
        gateway 192.168.2.1

```

Do I need the 'network' settings as shown in every tutorial (but never explained)?

TIA

---

### Post by chili555 on 2011-04-15
> Do I need the 'network' settings as shown in every tutorial (but never explained)?Nope. And you probably don't need the broadcast declaration, either. If it works the way it is, it works. Why change?

---

