---
title: "Network Setting/Network Manager application"
date: 2012-02-06
forum: Networking &amp; Wireless
---

### Post by bverly on 2012-02-06
Guys, i have problem with network manager application.
I cant open edit connection application,configure VPN. When i pressed this menu , there is nothing happen..Any one know which package should i download or replace

---

### Post by bverly on 2012-02-06
I cant create new Mobile Connection..

---

### Post by varunendra on 2012-02-07
Try:
```
sudo /etc/init.d/networking restart
sudo service network-manager restart
```

If these don't help, try reinstalling network-manager:
```
sudo apt-get install --reinstall network-manager
```

---

