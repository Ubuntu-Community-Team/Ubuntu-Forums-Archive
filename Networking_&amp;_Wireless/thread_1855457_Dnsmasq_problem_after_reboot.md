---
title: "Dnsmasq problem after reboot"
date: 2011-10-06
forum: Networking &amp; Wireless
---

### Post by mertoz on 2011-10-06
Hi, 
dns resolving and dhcp works fine, however when rebooting "/var/run/dnsmasq/resolv.conf" get emptied. 

My "dnsmasq.conf" file is pointing to a file where the nameservers and ips are located.

After reboot if I run "/etc/init.d/networking restart" the "resolv.conf" from /var get filled and everything works fine. How should I solve this? 

Thank you!

---

### Post by mertoz on 2011-10-12
I fixed the problem with dns inserting nameservers in /var/run/dnsmasq/resolv.conf

---

### Post by lkjoel on 2011-10-12
Could you mark this thread as solved? Thread tools->Mark this thread as solved.

---

