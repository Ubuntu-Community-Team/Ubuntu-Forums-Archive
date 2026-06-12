---
title: "eth0 not coming up automatically w/ dhcp (11.04)"
date: 2011-05-25
forum: Networking &amp; Wireless
---

### Post by lazzy_8 on 2011-05-25
Hi,
I have this in my /etc/networking/interfaces file:
auto lo
iface lo inet loopback

iface eth0 inet dhcp
  pre-up iptables-restore < /etc/iptables.rules
  post-down iptables-restore < /etc/iptables.rules

but eth0 doesn't automatically come up.  I have to do a "ifconfig eth0 up" and then do a dhclient eth0 in order to get an IP after each reboot.  Any idea what the problem is?

Thanks in advance!

---

### Post by chili555 on 2011-05-25
> Any idea what the problem is?Yes, you haven't instructed it to start **auto**matically. Please try this:```
auto lo
iface lo inet loopback

[COLOR="Red"]auto eth0[/COLOR]
iface eth0 inet dhcp
pre-up iptables-restore < /etc/iptables.rules
post-down iptables-restore < /etc/iptables.rules

```

---

### Post by lazzy_8 on 2011-05-25
Yes, that totally worked.  Thanks for the help!

---

