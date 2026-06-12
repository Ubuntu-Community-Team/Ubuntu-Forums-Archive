---
title: "Network address changes despite being static"
date: 2012-01-18
forum: Networking &amp; Wireless
---

### Post by kaplan71 on 2012-01-18
Hi there --

I am running the 10.04 LTS 64-bit distribution as a virtual server. The  host system is running Fedora Core 14 64-bit, and the virtual machine  software is the VirtualBox application. The virtual machine is set up  with a bridged connection.

I am periodically experiencing a situation where the virtual machine's  network address changes without warning, and I am forced to run the  ifdown and ifup commands to bring the address back to its original  state. 

I went through the motions of modifying the /etc/network/interfaces file  to have a static address. The syntax that I entered into the file is  shown below:

> auto eth0
iface eth0 inet static
address 132.183.12.225
netmask 255.255.255.0
network 132.183.12.0
broadcast 132.183.12.255
gateway 132.183.12.1                      I have confirmed that NetworkManager is not running on either the host or virtual server. Is there something wrong with my syntax, or is there another file that needs to modified? Thanks.

---

### Post by praseodym on 2012-01-18
Change "false" to "true" in the /etc/NetworkManager/nm-system-settings.conf, otherwise the NM ignores the "interfaces"

---

