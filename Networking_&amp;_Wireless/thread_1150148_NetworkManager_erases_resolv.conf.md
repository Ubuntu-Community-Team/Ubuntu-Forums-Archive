---
title: "NetworkManager erases resolv.conf"
date: 2009-05-05
forum: Networking &amp; Wireless
---

### Post by kelvinator on 2009-05-05
After upgrading to 9.04 I had problems getting NetworkManager to manage my eth0 static connection. 

After fixing resolv.conf I fixed this with the command
sudo chattr +i /etc/resolv.conf. 

I have found many discussions on getting NetworkManager to work in 9.04 but most do not address the problem. Hopefully one of the experts can tell us why this happens.

---

