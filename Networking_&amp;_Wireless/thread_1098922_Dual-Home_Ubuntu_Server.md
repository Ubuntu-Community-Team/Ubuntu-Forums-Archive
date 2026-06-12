---
title: "Dual-Home Ubuntu Server"
date: 2009-03-17
forum: Networking &amp; Wireless
---

### Post by xefialtis on 2009-03-17
I am having some very odd troubles with my router, but I don't need it - well, that is my understanding...

I have an Ubuntu 8.04 server with 2 NICs in it.
I have Comcast, and a Surfboard "cable modem"...
I use DynDNS
I have 5 web sites I run off the server
I have an internal network with about a dozen machines
I have a mail server
I have a proxy and filter (squid and dansguardian)
I have wireless on the router (several machines are wireless only)

EVERYTHING is working, right now, today

Currently, the set-up is: 
Comcast --> Cable Modem --> Router (firewall, etc) --> Server (proxy, etc) & Network

I want to change it to:
Comcast --> Cable Modem --> Server (firewall, proxy, etc) --> Router (wireless ap, etc) --> Network

In order to do this, I have to do a "dual-home" setup, where one NIC (eth0) is external to Comcast and the other NIC (eth1) is internal to the Network.

Can someone point me in the right direction?  I am not a "Linux Master" nor am I a "Linux Noob", I am somewhere in the middle, maybe a "Linux Enthusiast"... I do have 15 years experience working with computers (mostly Windows, but I left the Dark Side "recently")...

SO, any help/advice/pointers on how to do this so that my Server becomes the DHCP (v4/v6) and Gateway would be very helpful...

Thanks

---

### Post by gtr32 on 2009-03-17
It's been a while I had a Linux router, but DHCP service + iptables is what you're looking for.

[http://newbiedoc.sourceforge.net/networking/homegateway.html](http://newbiedoc.sourceforge.net/networking/homegateway.html)

---

### Post by cackles on 2009-03-19
This is what Im looking to do also, so here's a bump. I'd like to turn my Ubuntu server into a firewall/proxy. Squid for the proxy but I dunno about the firewall.

---

### Post by xefialtis on 2009-03-24
Talk about a learning curve.
I still haven't been able to get my Server on the dual NICs, but I am working on that...it seems they are unwilling to listen... (if anyone knows why Intel e1000 cards will say they DO NOT detect a link, when the lights come on and the cable is good, please forward that info...)
So, that is turning into a side issue. I might pick up a couple of the 3Com 3C2000-LP cards and try them...

I found that, in order to get multiple NICs running, and to use the server as a router, you have to do something called "MASQUERADEing" via IPTABLES.
[http://tldp.org/HOWTO/IP-Masquerade-HOWTO/firewall-examples.html#RC.FIREWALL-IPTABLES](http://tldp.org/HOWTO/IP-Masquerade-HOWTO/firewall-examples.html#RC.FIREWALL-IPTABLES)

Then you can use Squid and Firehol or any number of other things to protect the machine (nothing beats a good secure password and simple protections like fail2ban)

So, I have part of my problem solved...I'll post more as I get the rest of the issues resolved...

---

### Post by capscrew on 2009-03-24
> **xefialtis said:**
> Talk about a learning curve.
I still haven't been able to get my Server on the dual NICs, but I am working on that...

...I found that, in order to get multiple NICs running, and to use the server as a router, you have to do something called "MASQUERADEing" via IPTABLES.
[http://tldp.org/HOWTO/IP-Masquerade-HOWTO/firewall-examples.html#RC.FIREWALL-IPTABLES](http://tldp.org/HOWTO/IP-Masquerade-HOWTO/firewall-examples.html#RC.FIREWALL-IPTABLES)
...

This is not altogether correct.  I would not use IP Masquerading to forward all packets.  This is a form of NAT'ing and will alter the packet headers.

For an explanation of NAT'ing and when to use it, see: [[COLOR="Teal"]**http://www.faqs.org/docs/iptables/nattable.html**[/COLOR]]("http://www.faqs.org/docs/iptables/nattable.html")

For an explanation of where packet forwarding  fits into the scheme of things see: [**[COLOR="Blue"]http://www.netfilter.org/documentation/HOWTO//packet-filtering-HOWTO-6.html[/COLOR]**]("http://www.netfilter.org/documentation/HOWTO//packet-filtering-HOWTO-6.html")

In most circumstances you will:
a. Turn on packet forwarding
b. NAT all private address networks (on the interface)
c. Provide security via iptables (Through a GUI)

As a side note, firehol, fwbuilder, ferm firestarter, etc., all act upon iptables to configure the firewall.

If you just want to start forwarding between interfaces this is done in the /etc/sysctl.conf file.  Remember that you have turned on forwarding in BOTH directions (ie; both interfaces are being forwarded) See below:
```
#
# /etc/sysctl.conf - Configuration file for setting system variables
# See sysctl.conf (5) for information.
#

#kernel.domainname = example.com
#net/ipv4/icmp_echo_ignore_broadcasts=1

# the following stops low-level messages on console
kernel.printk = 4 4 1 7

# enable /proc/$pid/maps privacy so that memory relocations are not
# visible to other users.
kernel.maps_protect = 1

##############################################################3
# Functions previously found in netbase
#

# Uncomment the next line to enable Spoof protection (reverse-path filter)
#net.ipv4.conf.default.rp_filter=1

# Uncomment the next line to enable TCP/IP SYN cookies
#net.ipv4.tcp_syncookies=1

**[COLOR="Red"]# Uncomment the next line to enable packet forwarding for IPv4[/COLOR]**
#net.ipv4.conf.default.forwarding=1

# Uncomment the next line to enable packet forwarding for IPv6
#net.ipv6.conf.default.forwarding=1


```

---

