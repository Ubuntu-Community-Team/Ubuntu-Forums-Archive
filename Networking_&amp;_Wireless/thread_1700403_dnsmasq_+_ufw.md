---
title: "dnsmasq + ufw"
date: 2011-03-05
forum: Networking &amp; Wireless
---

### Post by delta_one_ on 2011-03-05
I have spent many hours googling and trying things now, but I can not seem to get this sorted.

I have a server running as a gateway, I am using dnsmasq for dns and dhcp, but I want ufw also, so that it is secure. But it seems that ufw is blocking dnsmasq from assigning IP addresses.

My external interface is eth0 and my internal interface is virtual, eth0:0

Everything works fine as a gateway (including dhcp) until I enable ufw. I have managed to let everything through the firewall except the dhcp.

```

# ufw status
Status: active

To                         Action      From
--                         ------      ----
22                         LIMIT       Anywhere
80                         ALLOW       Anywhere
Samba                      ALLOW       192.168.0.0/24
53                         ALLOW       192.168.0.0/24
10000                      ALLOW       192.168.0.63
67                         ALLOW       Anywhere

```

From my understanding, having port 67 open should allow dhcp server to work, I opened with:
```
#ufw allow bootps
```

Any ideas? =)

---

### Post by delta_one_ on 2011-03-06
Ok so after another day of being confused by the firewall appearing to be blocking DHCP, by chance I found out that it was a network problem unrelated to this server, so I had actually set it up right in the first place.

Anyway for anyone that is wondering, to allow a DHCP server to work through ufw, after enabling ufw on the same computer as is running the DHCP server, by running:
```
#ufw enable
```

all you need to do is:
```
#ufw allow bootps
```

Also if you are using dnsmasq like me and you want the same computer to work as a dns forwarder, you will want to run:
```
#ufw allow domain
```

---

### Post by ronalde@launchpad.net on 2011-12-25
Hi,

I guess I've the same setup
eth0 (dhcip from isp) > internet
eth0:0 (static internal ip) > lan

the host is running dnsmasq for dhcp, dns and pxe.

Could you please post your ufw-config and /etc/networking/interfaces?

Thanks,
Ronald

---

