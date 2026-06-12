---
title: "Localhost is extremely slow"
date: 2009-11-14
forum: Networking &amp; Wireless
---

### Post by Portland7677 on 2009-11-14
This is the first time in 10 months of using Ubuntu that I haven't been able to find the solution to a problem already posted on this forum.

Anyways, my problem is that when I share my internet connection the localhost is really slow.  My laptop, (running Jaunty) connects to the internet using a WiMAX USB dongle and I am sharing the internet connection with another laptop (running XP) via a crossover cable.

The problem is that when I run WEBrick to test a Ruby on Rails application it now takes up to a minute for pages to load.  This problem only exists if I am sharing the internet connection.

I have to run the following script every time I restart to enable the sharing.


#!/bin/sh
sudo ifconfig eth0 192.168.0.1
sudo iptables -A FORWARD -i ppp0 -o eth0 -s 192.168.0.0/24 -m conntrack --ctstate NEW -j ACCEPT
sudo iptables -A FORWARD -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
sudo iptables -A POSTROUTING -t nat -j MASQUERADE


Any help would be greatly appreciated.

---

### Post by nixscripter on 2009-11-18
Try putting this at the top of the script:

```
sudo iptables -I INPUT 1 -i lo -j ACCEPT
```

Also, make sure that localhost and your host name are listed in **/etc/hosts**.

---

