---
title: "manual IP configuration not surviving reboot"
date: 2009-02-04
forum: Networking &amp; Wireless
---

### Post by rsleventhal on 2009-02-04
Hi folks,

I'm a new Ubuntu user, but not new to Linux.

I've just installed Intrepid on my PC and all is well, but for one thing.

I don't use DHCP on this network but when I manually configure the IP/Netmask/Gateway, the changes I put into effect don't survive rebooting the machine.  In other words, it's all set back to DHCP again and I have to manually reconfigure.

Were this RHEL or CentOS, I'd edit /etc/sysconfig/network-scripts/ifcfg-eth0, but as that doesn't exist on my new favorite desktop linux distro, I'm at a loss.

Any pointers will be greatly appreciated.

Thanks in advance,
-Ray

---

### Post by DGortze380 on 2009-02-04
> **rsleventhal said:**
> Hi folks,

I'm a new Ubuntu user, but not new to Linux.

I've just installed Intrepid on my PC and all is well, but for one thing.

I don't use DHCP on this network but when I manually configure the IP/Netmask/Gateway, the changes I put into effect don't survive rebooting the machine.  In other words, it's all set back to DHCP again and I have to manually reconfigure.

Were this RHEL or CentOS, I'd edit /etc/sysconfig/network-scripts/ifcfg-eth0, but as that doesn't exist on my new favorite desktop linux distro, I'm at a loss.

Any pointers will be greatly appreciated.

Thanks in advance,
-Ray

You're looking for /etc/network/interfaces

---

### Post by rsleventhal on 2009-02-04
Well, isn't it just like me to find the answer after posting.  I have found this page and will try this tomorrow when at that machine...

[http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html](http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html)

I'll post the results.

-Ray

---

### Post by rsleventhal on 2009-02-04
> **DGortze380 said:**
> You're looking for /etc/network/interfaces

Thanks DGortze...much appreciated.

-Ray

---

### Post by Iowan on 2009-02-05
I bookmarked your link - [here]("http://www.prash-babu.com/2009/01/how-to-setup-static-ip-in-ubuntu.html") is another method... but use what works!

---

