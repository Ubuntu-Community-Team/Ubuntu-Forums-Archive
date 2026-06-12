---
title: "UFW interfering with my LXC containers"
date: 2013-01-19
forum: Networking &amp; Wireless
---

### Post by cryptochrome242 on 2013-01-19
Hi,

as soon as I enable the UFW firewall with one simple rule (allow tcp/22), my LXC containers can no longer aqquire IP addresses via DHCP (through the lxc-bridge). Any hints?

Thanks

---

### Post by terrypearson on 2013-09-26
Just a guess, 

sudo nano /etc/default/ufw
----
# Change:
# DEFAULT_FORWARD_POLICY="DROP"
# to
DEFAULT_FORWARD_POLICY="ACCEPT"

Then restart ufw

I am basing this off [http://docs.docker.io/en/latest/installation/ubuntulinux/#ubuntu-raring](http://docs.docker.io/en/latest/installation/ubuntulinux/#ubuntu-raring) which says that the forward policy is not setup correctly by default for lxc.

---

