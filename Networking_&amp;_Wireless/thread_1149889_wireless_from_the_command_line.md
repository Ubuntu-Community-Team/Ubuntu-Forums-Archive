---
title: "wireless from the command line"
date: 2009-05-05
forum: Networking &amp; Wireless
---

### Post by Hellbourne on 2009-05-05
Hi,

I can see the wireless network from the command line with 'iwlist scanning'. Let's denote it as 'the_wireless_network'. How do I connect to it using the command line only?

Thanks,

Amit

---

### Post by chili555 on 2009-05-05
```
sudo /etc/init.d/NetworkManager stop
sudo iwconfig wlan0 essid the_wireless_network
sudo dhclient wlan0
```Substitute your wireless interface, if it's not wlan0. Also, this assumes you have no encryption, WEP, WPA, etc. in place.

---

