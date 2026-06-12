---
title: "rt2860 / rt2860sta no longer works after upgrade to natty"
date: 2011-05-16
forum: Networking &amp; Wireless
---

### Post by JensLH on 2011-05-16
I recently upgraded my Zepto laptop to Natty (11.04), and unfortunately the wifi no longer worked. I have a WPA net, and the combination with a Ralink chip seems unfortunate - judging from the number of internet posts.

After browsing loads of threads on the 'net I think I have found a solution for 11.04 - I hope it will work out of the box in 11.10 ! :-)

1) Add "blacklist rt2800pci" to /etc/modprobe.d/blacklist.conf

I think this makes the wifi stuff work as I can then do "iwlist wlan0 scan" and get reasonable output. But there is no integration with the Network Manager. So I have also done this (again, with inspiration from a few threads):

2) Edit /etc/NetworkManager/NetworkManager.conf - change the "managed=false" under "[ifupdown]" to "managed=true".

You may have to do a "service network-manager restart", restart or similar to get it going.

It also seems I can suspend and get a wifi net connection upon wakeup.

I hope it helps a few people out there.

---

### Post by sgerrand on 2011-05-17
brilliant - blacklisting both rt2800pci and rt2x00pci worked for me. thanks for the tip!

---

