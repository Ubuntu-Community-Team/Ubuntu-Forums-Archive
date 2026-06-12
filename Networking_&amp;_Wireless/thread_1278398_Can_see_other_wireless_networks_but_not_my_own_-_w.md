---
title: "Can see other wireless networks but not my own - why"
date: 2009-09-29
forum: Networking &amp; Wireless
---

### Post by nielsniemann on 2009-09-29
Hi

I'm also new to Ubuntu and Linux in generel. Great OS, but both sound and my Wireless Internet connection does not work :-(

I use WPA2 / AES as security, and I can see many other wireless networks.. but not my own. Broadcast is not hidden.

I have correct a little in etc/network: interfaces, so I now have:

auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-ssid cjnn
wpa-ap-scan 1
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk (HERE IS MY PASSWORD)

Ubuntu says connection establish but I cannot browse.

Does anyone know what is wrong?

If I take my laptop also try ubuntu, then I can see my network, and the Internet works.

Best regards
Niels

---

### Post by t0mppa on 2009-09-29
One possibility is that your AP is using a channel that your system isn't. You can find which channels your system recognizes on scans by running **iwlist <interface_logical_name> channel** on terminal.

Also, in the case where you get a connection but can't browse, it's probably either a routing or a DNS issue. So, try to run **nslookup [www.google.com](www.google.com)** and then **ping 74.125.127.100** to see if either or both of them fail.

---

