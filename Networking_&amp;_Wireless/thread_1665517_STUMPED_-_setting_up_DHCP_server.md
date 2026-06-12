---
title: "STUMPED - setting up DHCP server"
date: 2011-01-12
forum: Networking &amp; Wireless
---

### Post by cherrio on 2011-01-12
Hey All,

kind of stumped, trying to setup dhcp3-server, have followed a bunch of tutorials, but still having issues.

Contents of /etc/network/interfaces (modified first two blocks of IP for privacy)

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address x.x.220.230
        netmask 255.255.254.0
        network x.x.220.0
        broadcast x.x.221.255
        gateway x.x.220.1
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 208.67.222.222 208.67.220.220
        dns-search localdomain

```

The server has only 1 IP (**x.x.220.230**) and a direct connection to the Net (I cannot get any more static ips). I will connect to the server via a VPN (pptpd), so I want the server to hand out a dhcp address on connection, preferably in block 192.168.x.x so it is clear it is a nat/dhcp address.

Contents of /etc/default/dhcp3-server
```

# Defaults for dhcp initscript
# sourced by /etc/init.d/dhcp
# installed at /etc/default/dhcp3-server by the maintainer scripts

#
# This is a POSIX shell fragment
#

# On what interfaces should the DHCP server (dhcpd) serve DHCP requests?
#       Separate multiple interfaces with spaces, e.g. "eth0 eth1".
INTERFACES="eth0"


```


Contents of /etc/dhcp3/dhcpd.conf

```

# The ddns-updates-style parameter controls whether or not the server will
# attempt to do a DNS update when a lease is confirmed. We default to the
# behavior of the version 2 packages ('none', since DHCP v2 didn't
# have support for DDNS.)
ddns-update-style none;

# option definitions common to all supported networks...
option domain-name "home.lan";
option domain-name-servers ubuntu.home.lan;

default-lease-time 600;
max-lease-time 7200;

# If this DHCP server is the official DHCP server for the local
# network, the authoritative directive should be uncommented.
#authoritative;

option subnet-mask 255.255.255.0;
option broadcast-address 192.168.1.255;
option routers 192.168.1.254;
option domain-name-servers 192.168.1.1, 192.168.1.2;
option domain-name “yourdomainname.com”;

subnet 192.168.1.0 netmask 255.255.255.0 {
    range 192.168.1.10 192.168.1.200;
}

```


I am pretty sure my problem is in the dhcpd.conf, I have tried a whole bunch of variations, but the server refuses to start.

In /var/log/syslog it always either says "No subnet declaration for eth0 (x.x.220.230)." or if I change the IPs to be something more like the actual server ip, "/etc/dhcp3/dhcpd.conf line 24: subnet x.x.220.230 netmask 255.255.255.0: bad subnet number/mask combination".

Totally stumped, any suggestions for what values I should have in dhcpd.conf?

Thanks in advance! :)

---

### Post by gmargo on 2011-01-12
Doesn't **pptpd** handle distribution of client IP addresses?  Why do you think you need a DHCP server?

---

### Post by cherrio on 2011-01-12
Thanks for the reply. I should have explained more, the real issue is that pptpd is not working correctly.

When I connect to server via VPN/pptpd, from a Windows client PC, with the get "Obtain an IP address automatically" checked in the properties window, my /var/log/syslog looks like,

[http://pastebin.com/CHZQ2kJ0](http://pastebin.com/CHZQ2kJ0) (on pastebin to avoid cluttering thread)

The line,
```
Jan 12 18:39:33 localhost pppd[7941]: Sent 2498919260 bytes, received 0 bytes.
```

I think is important. I had the same issue before (on a different server) and I fixed it by using DHCP.


If I set a static IP address on the Windows client PC, the log looks like : [http://pastebin.com/eMuViPYk](http://pastebin.com/eMuViPYk)

This time it says "Sent 90 bytes, received 134 bytes". As the server only has 1 static IP for itself, I wanted to use DHCP to allow the VPN clients to get there own NAT addresses.


I am still very much a Ubuntu/Linux newbiee, so I could be way off base!

---

### Post by gmargo on 2011-01-12
Can you post your **pptpd** configuration?

Also, using pastebin is rather discouraged - you can just as easily create an attachment to your post.

---

### Post by cherrio on 2011-01-12
Thanks for the follow up, I have attached my pptpd condfig files, I had to add .txt extension to the files to get them to upload properly.

Thanks for the help:)

---

### Post by gmargo on 2011-01-12
I haven't tested anything yet but I'm pretty sure this setting in your pptpd.conf file is incorrect:
```

localip SERVER_IP
remoteip HARD_CODED_TO_MY_LOCAL_IP

```These settings, according the the **pptpd.conf(5)** man page, are the IP addresses to be used on each end of the individual point-to-point links. It should a different network from your ethernet adapter (I think). Assuming that you're not using the 192.168.x.x range locally, you can use that for ppp.  I would try something like this first:
```

localip 192.168.0.1
remoteip 192.168.0.100-254

```

---

### Post by cherrio on 2011-01-13
Should have said that he SERVER_IP and HARD_CODED_TO_MY_LOCAL_IP are tokens, that I put in place of real values.

```
localip x.x.220.230
remoteip y.y.181.162
```


x.x.220.230 = Ubuntu Server IP (taken from ifconfig)
y.y.181.162 = Windows client PC IP (taken from whatismyip.com :P)


So if I set "remoteip 192.168.0.100-254", pptpd is smart enough to figure out the subnets/broadcast/gateway addresses itself? That would be pretty sweet!

---

### Post by cherrio on 2011-01-13
That worked!!! :)

localip 192.168.0.1
remoteip 192.168.0.100-254

I also had to update the options file and add ms-dns entries.

Thanks for the help :)

Robert

---

### Post by gmargo on 2011-01-13
That's great!

What did you end up with for the final versions of the config files?

---

### Post by cherrio on 2011-01-15
For the options file, just had to uncomment the ms-dns lines and add the open DNS IP addresses.

/etc/ppp/options
```

ms-dns 208.67.222.222
ms-dns 208.67.220.220
```


For the conf file, just uncomment the "recommended" settings

/etc/pptpd.conf
```

# (Recommended)
localip 192.168.0.1
remoteip 192.168.0.234-238
```


Perfect! :)

---

### Post by cherrio on 2011-01-15
For the options file, just had to uncomment the ms-dns lines and add the open DNS IP addresses.

/etc/ppp/options
```

ms-dns 208.67.222.222
ms-dns 208.67.220.220
```


For the conf file, just uncomment the "recommended" settings

/etc/pptpd.conf
```

# (Recommended)
localip 192.168.0.1
remoteip 192.168.0.234-238
```


Perfect! :)

---

