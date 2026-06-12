---
title: "Need help in Internet Sharing between Kubuntu 9.04 and Windows 2000"
date: 2009-06-03
forum: Networking &amp; Wireless
---

### Post by rahulabc on 2009-06-03
I just installed Kubuntu 9.04 on my pc which has also Xp installed. My internet is running fine on this pc but I have one more PC with Windows 2000 installed. Both PCs are connected using Networking Cable. From Xp, I can connect easily between 2 pcs. Ip address on default ethernet in Xp is set to automatic and in Second Ethernet, it is 192.168.0.1 with no gateway and in Second Pc, it is 192.168.0.2 with gateway 192.168.0.1.

When I start Kubuntu, the Network Manager shows "eth0 Connected" "eth1 Not Connected" and when I open Manage connections no ethernet card displays so m not able to set its IP address. eth0 is connected because it gets its IP address automatically. But what about eth1? How should I set its Ip address so that both pcs get shared.?

Please provide me its solution soon.

Any help would be greatly appreciated.

---

### Post by rahulabc on 2009-06-04
Please anybody help me.. I need ur help urgent..

---

### Post by superprash2003 on 2009-06-04
post contents of /etc/network/interfaces

---

### Post by rahulabc on 2009-06-04
auto lo
iface lo inet loopback

---

### Post by rahulabc on 2009-06-04
plzz help.. I can't be online whole day

---

### Post by superprash2003 on 2009-06-04
but if eth1 is disconnected , why would you want to set up an ip..

---

### Post by rahulabc on 2009-06-05
eth1 is not disconnected. The wire is set properly in both pcs. Kubuntu is assigning an automatic IP to eth1 which will not work as it has to be set up manually to work. Thats why it is showing that eth1 is disconnected.

---

### Post by superprash2003 on 2009-06-08
you could setup static ip like this [https://help.ubuntu.com/8.04/serverguide/C/network-configuration.html](https://help.ubuntu.com/8.04/serverguide/C/network-configuration.html)

---

