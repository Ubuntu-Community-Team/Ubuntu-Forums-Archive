---
title: "libvirtd - virt-install --network option"
date: 2013-07-16
forum: Networking &amp; Wireless
---

### Post by alexnaveentest on 2013-07-16
Hi Guys,

I have created two network bridge and defined it in network.xml file. Started it using virsh net-start "vlan test" where 'vlan test' is my network's name. Is it possible to add this using virt-install --network:"vlan test" option to create a VM with these two bridges. I get an error while trying to do so.

I can ofcourse do multiple --network parameter with virt-install to create a dual nic VM, but my question is .. do we have an option with virt-install to include a user defined network in to a VM while creating it??

Any help is much appreciated..

Regards,
Alex

---

### Post by bapoumba on 2013-08-04
Moved to Networking.

---

