---
title: "vbox with virtual xp to log on nt domain"
date: 2009-02-04
forum: Networking &amp; Wireless
---

### Post by lar5 on 2009-02-04
Hi community,

i could need some help with virtual-box.
i run Ubuntu 8.10 with Vbox. in Vbox i do have a virtual windows xp machine. The host is part of a domain (nt active directory). Now i would like to log in to this domain from the virtual machine. the network config is like:

Domain controller/server ip : 10.5.10.10 mask:255.255.0.0

Ubuntu: 10.5.20.14 mask: 255.255.0.0 DNS:10.5.10.10

when i start the virtual xp i have through dhcp:

xp ip :10.0.2.15  gateway: 10.0.2.2


i can access the network shares, but i can not become member of the domain. i think its because of the NAT connection through Vbox host.
i would like to use the network adapter of the computer, from inside the virtual machine without nat, that i can apply a new ip (ex: 10.5.20.x mask 255.255.0.0), or to use even the same network configuration the host (ubuntu) is using.


any ideas ... help ... links ..... would be great.

thx anyway

---

### Post by veloce on 2009-02-10
> **lar5 said:**
> Hi community,

i could need some help with virtual-box.
i run Ubuntu 8.10 with Vbox. in Vbox i do have a virtual windows xp machine. The host is part of a domain (nt active directory). Now i would like to log in to this domain from the virtual machine. the network config is like:

Domain controller/server ip : 10.5.10.10 mask:255.255.0.0

Ubuntu: 10.5.20.14 mask: 255.255.0.0 DNS:10.5.10.10

when i start the virtual xp i have through dhcp:

xp ip :10.0.2.15  gateway: 10.0.2.2


i can access the network shares, but i can not become member of the domain. i think its because of the NAT connection through Vbox host.
i would like to use the network adapter of the computer, from inside the virtual machine without nat, that i can apply a new ip (ex: 10.5.20.x mask 255.255.0.0), or to use even the same network configuration the host (ubuntu) is using.


any ideas ... help ... links ..... would be great.

thx anyway

You'd be best to ask this question in the virtualisation section.  However, what you need to do is switch from using NAT to bridged for your virtual networking of the vm.  That will allow the vm to be on the same subnet as the windows domain controller.

---

