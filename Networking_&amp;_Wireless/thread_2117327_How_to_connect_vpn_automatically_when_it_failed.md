---
title: "How to connect vpn automatically when it failed?"
date: 2013-02-18
forum: Networking &amp; Wireless
---

### Post by xiaocszn on 2013-02-18
My vpn failed a lot, i had to click connect every few minutes, how can i let it connect automatically when the connection break?

---

### Post by slickymaster on 2013-02-18
Try to reinstall it:
```
sudo apt-get purge network-manager-vpn
sudo apt-get install network-manager-vpnc
```

Then do this (see my images attached)

---

### Post by xiaocszn on 2013-02-18
I checked the box, but it didn't work. When the connection break, it still wouldn't connect automatically. 
Thank you all the same!

---

