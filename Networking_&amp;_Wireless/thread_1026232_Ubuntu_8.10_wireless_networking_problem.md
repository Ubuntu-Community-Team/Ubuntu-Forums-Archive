---
title: "Ubuntu 8.10 wireless networking problem"
date: 2008-12-30
forum: Networking &amp; Wireless
---

### Post by rico_suave on 2008-12-30
My cousin downloaded the new ubuntu 8.10 and had some problems getting connected to the internet wirelessly. We've tried putting in IP addresses and DHCP info, tried a few terminal commands, editing wireless on ubuntu, and still came out with nothing after 2 hrs of searching and trying different solutions. Has anyone had this problem when they downloaded and first started up ubuntu 8.10? If you have had this problem and found a solutions for it, please let me know. My cousin and I both love Ubuntu as new users, but my cousin is the first to come up with this problem. Any advice would be greatly appreciated. Thank you Ubuntu members! :p

---

### Post by melojo on 2008-12-30
open a terminal and post the output of

```
lspci
sudo lshw -C network

```

This will give us more info so someone can help.

---

