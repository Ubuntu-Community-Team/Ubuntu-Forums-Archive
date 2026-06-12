---
title: "Combating terrible school network"
date: 2011-09-09
forum: Networking &amp; Wireless
---

### Post by biggiee on 2011-09-09
I am on a school network with high traffic where the connection seems to constantly "time out" on both wireless and Ethernet, yet i still maintain my ip address. To cope with this problem i have been running the fallowing script.
```
#!/bin/sh
sudo /etc/init.d/networking restart; sudo dhclient 
```
It works completely fine, but I am curious if there is a more efficient way to deal with this problem since, depending on the day and time, I could be running the script more times then I care for.

---

