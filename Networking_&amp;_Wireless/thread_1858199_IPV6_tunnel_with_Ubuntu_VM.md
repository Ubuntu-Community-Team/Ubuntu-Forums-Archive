---
title: "IPV6 tunnel with Ubuntu VM"
date: 2011-10-11
forum: Networking &amp; Wireless
---

### Post by sidd09 on 2011-10-11
Hi, 

I am creating an 6over4 tunnel using Hurricane Electric tunnel, 

Please find the network topology attached.

The tunnel is created using a windows PC.
Everything works fine with the windows machine and sends ipv6 traffic.

ubuntu is running on a virtual box and is bridged to windows.

but am unable to reach the tunnel through ubuntu or get to the internet.

Please let me know where I am going wrong.

---

### Post by lemming465 on 2011-10-13
Is the windows connection wired ethernet or wireless wifi?  If your hypervisor is Oracle's virtualbox, it still lacks support for bridging IPv6 over wireless.

---

