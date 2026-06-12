---
title: "[SOLVED] MAC address chance"
date: 2008-12-10
forum: Networking &amp; Wireless
---

### Post by vagelism on 2008-12-10
Hello to all how can I change my mac address?
I use eeebuntu and a asus eee p900 with atheros and madwifi pached drivers.
Thank you for your advice.

---

### Post by Dark X Dragon on 2008-12-10
In theory, a MAC address cannot be changed.

It is a unique identifier for networking hardware.

---

### Post by firefly2442 on 2008-12-10
```
sudo ifconfig eth0 down hw ether 00:00:00:00:00:01

sudo ifconfig eth0 up
```

Obviously, if you have multiple ethernet cards, wireless, or use some different type of network interface you'll have to change this.  This site might help too:

[http://www.howtogeek.com/howto/ubuntu/change-your-network-card-mac-address-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/change-your-network-card-mac-address-on-ubuntu/)

---

