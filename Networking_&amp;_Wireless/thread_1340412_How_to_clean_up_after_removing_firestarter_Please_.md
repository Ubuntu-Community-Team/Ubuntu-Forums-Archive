---
title: "How to clean up after removing firestarter? Please help..."
date: 2009-11-28
forum: Networking &amp; Wireless
---

### Post by darkod on 2009-11-28
I use internet trough my LAN onboard in my desktop. To share it occasionally with my netbook I have inserted a usb wi-fi adapter and created new wireless network. The netbook has integrated wi-fi of course.
That worked straight away and I was even very impressed because I didn't need to even select internet connection sharing anywhere. The spped on the internet on the netbook seemed reasonable.

Today I had some worries about the protection on my LAN connection and since Ubuntu doesn't activate firewall by default, I installed Firestarter package. It went straight forward and I didn't add any specific rules or anything. In the Preferences I specified that my internet connection is eth0 and the local home connection is wlan0. But then the internet speed on the netbook dropped significantly. Not sure if it was related to firestarter or just coincidence.
I tried removing it, also adding --purge option to clean it all up. I restarted Ubuntu. I deleted the ad-hoc network and created new one.
The speed still remains low. Not sure how much of this is related to having activated firestarted just briefly. I even emptied iptables with -F from other posts. Still the same.
Is there any where I could check if there is some rule left over? How to make sure it's purged completely?

Thanks in advance.

---

