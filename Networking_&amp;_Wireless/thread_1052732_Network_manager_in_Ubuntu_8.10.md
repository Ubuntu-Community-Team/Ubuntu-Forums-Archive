---
title: "Network manager in Ubuntu 8.10"
date: 2009-01-28
forum: Networking &amp; Wireless
---

### Post by Krydox on 2009-01-28
Hi, alright I have this problem with internet at school with Ubuntu 8.10, because the network manager changed, and it doesn't work anymore somehow. It used to work fine with the older network manager.

I think the problem is a proxy, my school uses one. What I would do in the previous network manager, is setting up a static IP, and enable a system proxy and it would work. But I can't figure it out in Ubuntu 8.10.

---

### Post by pdtpatrick on 2009-01-28
I dont think it should be that much different. Just edit your /etc/network/interfaces and make your ip static.. then input the proxy server into your web browser (firefox). Should work.

---

### Post by Krydox on 2009-01-28
OMG that worked!

Thank you so much.

---

### Post by normanp on 2009-01-28
Please see my post in [http://ubuntuforums.org/showthread.php?t=1050965&page=2](http://ubuntuforums.org/showthread.php?t=1050965&page=2) for a solution.

---

