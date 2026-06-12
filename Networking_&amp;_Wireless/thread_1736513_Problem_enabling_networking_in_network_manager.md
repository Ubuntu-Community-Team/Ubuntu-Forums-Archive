---
title: "Problem enabling networking in network manager"
date: 2011-04-22
forum: Networking &amp; Wireless
---

### Post by dunc_smith on 2011-04-22
Hi I have upgraded from 10.04 to 10.10 and now can't enable networking. When I right click on the network manager applet the enable networking check box is greyed out.

Does anyone have any ideas how to solve this problem?


Thanks

---

### Post by dineshs on 2011-04-23
Run```
sudo gedit /var/lib/NetworkManager/NetworkManager.state
```Ensure that it reads ```

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
```
Restart

---

