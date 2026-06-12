---
title: "Briged networking doesn't work after latest kernel upgrade (2.6.28-13-server)"
date: 2009-07-06
forum: Networking &amp; Wireless
---

### Post by Tobatus on 2009-07-06
I had briged eth0 (for KVM) with configuration:
auto eth0
iface eth0 inet manual

auto br0
iface br0 inet static
        address 195.218.X.X
        netmask 255.255.X.X
        network 195.218.X.X
        broadcast 195.218.X.X
        gateway 195.218.X.X
        bridge_ports eth0
        bridge_fd 9
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off

It worked before, but after kernel upgrade it doesn't work anymore. /etc/init.d/networking just hangs at "Configuring network interfaces". Any ideas what has broken or is wrong?

---

### Post by Tobatus on 2009-07-07
Any ideas or should I just create a bug report?

---

