---
title: "Wifi seems to be up but can't connect - HELP!"
date: 2011-01-28
forum: Networking &amp; Wireless
---

### Post by Raiden616 on 2011-01-28
The wireless adapter is apparently on and I can see my wireless networks in the network manager. However when I try and connect it hands on "Obtaining Ip address" and then times out. Running "sudo dhclient" causes a bunch of:

DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval X

until an eventual error:

No DHCPOFFERS recevied
No working leases in persistent databased - sleeping.

Any advice would be greatly appreciated. Thanks in advance!

---

### Post by lisati on 2011-01-28
Does your WiFi access point have something like filtering based on MAC address enabled?

---

### Post by Raiden616 on 2011-01-28
Thanks for your reply;

I have no mac address filtering enabled and DHCP is active.

---

