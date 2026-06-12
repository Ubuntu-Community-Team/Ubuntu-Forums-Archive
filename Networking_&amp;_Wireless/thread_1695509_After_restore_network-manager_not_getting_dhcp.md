---
title: "After restore network-manager not getting dhcp"
date: 2011-02-26
forum: Networking &amp; Wireless
---

### Post by odulzaides on 2011-02-26
Hi,
My hard drive went bad and I had to replace it. I re-installed ubuntu 10.04 64 bit and then restored my root file system from a tar backup I had made.  As far as I can see all works well except 2 things. Networking and sound. I know this is a Networking forum so i'll keep it to that.

The eth0 is set for dhcp in network manager but when I  start the system  I do not get an ip address from the dhcp server. If I however run dhclient i am able to get an address, gateway, dns ok from the server. I have tried restarting the network and to no avail. In fact after acquiring a DHCP address when I run dhclient if I then restart networking it will once again lose it's address.

Wireless is also not working as I can set it up to connect to the AP in network-manager but it makes no attempt to connect. It does however get a APIPA address of 169.....

If someone has any clues I'd appreciate it.

Thanks
Oscar

---

