---
title: "How to uninstall a wireless driver?"
date: 2008-12-11
forum: Networking &amp; Wireless
---

### Post by FountainDew on 2008-12-11
How do I uninstall a wireless driver that is causing me problems? For example on my laptop I installed the following:

```
wget http://snapshots.madwifi.org/madwifi-hal-0.10.5.6-current.tar.gz
tar -xvf madwifi-hal-0.10.5.6-current.tar.gz
cd madwifi-hal-0.10.5.6-r3879-20081204
sudo apt-get install build-essential linux-headers-$(uname -r)
sudo make
sudo make install
```

---

