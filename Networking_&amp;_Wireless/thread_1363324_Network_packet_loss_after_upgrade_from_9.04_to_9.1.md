---
title: "Network packet loss after upgrade from 9.04 to 9.10"
date: 2009-12-24
forum: Networking &amp; Wireless
---

### Post by abeverley on 2009-12-24
After upgrading from Ubuntu 9.04 to 9.10 my Ethernet network has started to drop packets. In Firefox this results in slow/unresponsive browsing and when running mtr I see about a 20% packet loss as soon as the packets have left the PC.

I have tried the following:

- Upgraded the kernel (to 2.6.31-17-generic)
- Checked that no iptables rules are running
- Restarted my router
- Disabled ipv6
- Tried wicd instead of network-manager

None have any effect. When the PC is booted in windows the networking works fine. The network device is an Intel Ethernet Pro 100.

Any ideas?

Andy

---

### Post by abeverley on 2009-12-24
Okay, I've just booted into 2.6.28-16-generic and the networking works fine. I'll stick with this kernel for the time being, but it would be nice to know what the problem is and report it as required.

---

### Post by rumli on 2010-01-15
I had the same (or very similar) problem.  With 2.6.31-17-generic, I was seeing about 20-25% packet loss with my ASUS WL-167G usb wireless network adapter.  Like you, I booted into an older kernel (2.6.31-16-generic), and the problem went away.

---

