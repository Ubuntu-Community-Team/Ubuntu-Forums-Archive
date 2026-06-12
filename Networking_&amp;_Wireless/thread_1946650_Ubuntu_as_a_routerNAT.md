---
title: "Ubuntu as a router/NAT"
date: 2012-03-25
forum: Networking &amp; Wireless
---

### Post by stephanelefou on 2012-03-25
Hi,

I'd like to setup Ubuntu 11.10 as a router between my public IP and my LAN.  I did it in the past using FreeBSD but never with Ubuntu.  The machine is already equipped with 2 NIC and are working.

I found this howto:
[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

It looks okay to me but maybe a little bit outdated, I'm seeking for your thoughts on it.

Thanks.

---

### Post by Cheesehead on 2012-03-25
If this is occasional sharing, then using the sharing feature of Network Manager works great.

For a permanent router, though, you may wish more robust firewall rules, and admin tools to assign dhcp addresses, port forwarding, etc, to support the needs of machines on your LAN. You *can* do most of those through NM, but I find it easier (and quicker to diagnose problems) to use /etc/network/interfaces and dnsmasq and a proper set of routing firewall rules.

---

### Post by collisionystm on 2012-03-25
Ready my reply on here

[http://ubuntuforums.org/showthread.php?t=1944407](http://ubuntuforums.org/showthread.php?t=1944407)

2nd page

---

