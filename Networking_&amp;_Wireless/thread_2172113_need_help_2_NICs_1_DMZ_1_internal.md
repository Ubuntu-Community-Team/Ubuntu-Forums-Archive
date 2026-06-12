---
title: "need help 2 NICs 1 DMZ 1 internal"
date: 2013-09-03
forum: Networking &amp; Wireless
---

### Post by dan29 on 2013-09-03
I am using Ubuntu Server LTS 12.04 and am trying to set things up with 2 nics on 2 networks.  I can either of the nics working seperately but I can't get them both working at the same time.  I'm sure I'm doing something wrong, but I can't figure out what.  I would really appreciate it if someone can point out what I'm doing wrong.

I am trying to set it up in the /etc/network/interfaces file (if there is somewhere else I need to be, please tell me!), here is what I have:

iface lo inet loopback
auto lo

auto eth0
iface eth0 inet static
 address 10.1.xxx.x
 netmask 255.255.255.0
 up route add default gw 10.1.xxx.x
 dns-search     local.domain
 dns-nameservers        8.8.8.8 208.67.222.222


auto eth1
 iface eth1 inet static
 address 66.213.xxx.x
 netmask 255.255.255.0
 up route add default gw 66.213.xxx.x
 dns-search    local.domain
 dns-namesrvers                8.8.8.8 208.67.222.222

---

### Post by houstonbofh on 2013-09-03
To start, your format is non-standard.  That can easily lead to confusion, so you might want to use the standard format;
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
#iface eth0 inet dhcp

iface eth0 inet static
address 192.168.40.49
gateway 192.168.40.1
netmask 255.255.255.0
dns-nameservers 192.168.40.1

```

Second, you have two default gateways.  You need to pick one.  If you want to do load sharing, you need a special app or appliance for that.

---

### Post by SeijiSensei on 2013-09-03
What do you mean by "working at the same time?"  After you fix the default gateway problem (it should be the 66.213 address I suspect), are you intending to pass packets between the 10 network and the Internet?  If so, you need to enable IP packet forwarding in /etc/sysctl.conf (see the instructions in that file), and you'll need some type of iptables masquerading rule.  But before we go down that road, what are you trying to accomplish?

---

