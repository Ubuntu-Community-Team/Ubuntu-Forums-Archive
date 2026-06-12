---
title: "DHCP question"
date: 2010-02-09
forum: Networking &amp; Wireless
---

### Post by techaview on 2010-02-09
Guys, got a problem here

i just purchased an oem box with 5 network interfaces. I want to set interface 1 as WAN link using DHCP connected to my modem. I have set interface 2 as internal and set a class C network. I have enabled and configured the DHCP module based on the class c network set on interface 2. Is it possible for me to plug my network cable into interface 3 - 5 so that my client machines can get the DHCP leases from interface 2? I have tried to plugged the cable into interfaces 3 - 5 and they are not getting the leases from the DHCP server from interfaces 2. Thank you.

---

### Post by suseendran.rengabashyam on 2010-02-09
Hi,

You can make the DHCP server to listen on multiple interfaces by editing the file /etc/default/dhcp3-server. Open /etc/default/dhcp3-server and edit the following line

```
INTERFACES=""
```

to

```
INTERFACES="ethX ethY ethZ"
```

where ethX, ethY and ethZ are the network interfaces on which you want the DHCP server to listen.

Restart the dhcp3 daemon for the changes to take effect.

You would need to setup dhcp leases in your /etc/dhcp3/dhcpd.conf appropriate for each interface depending upon the IP address/netmask associated with the interface.

---

