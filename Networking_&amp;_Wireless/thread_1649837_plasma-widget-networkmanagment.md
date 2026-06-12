---
title: "plasma-widget-networkmanagment"
date: 2010-12-20
forum: Networking &amp; Wireless
---

### Post by Faoesch on 2010-12-20
I can't seem to find out how the VPN client works. The problem is when I type in my user and group password and set it to saved, it changes back to always ask when I go back to this connection.
I hope someone can help me :). Thanks in advance.

Faoesch

---

### Post by Zorael on 2010-12-21
Try creating a new user. Does it happen when logged in as him as well? Perhaps it's a bug in the plasmoid itself or in the wallet.

I ended up using KVpnc (from the repos, package name **[kvpnc](apt://kvpnc)**), which has its own flaws but is a bit more advanced.

---

### Post by Faoesch on 2010-12-21
Well my friend has Kubuntu as well and has exactly the same problem. So yes, it's not just with me. I just found this [https://bugs.launchpad.net/ubuntu/+source/plasma-widget-networkmanagement/+bug/350301](https://bugs.launchpad.net/ubuntu/+source/plasma-widget-networkmanagement/+bug/350301). So is it impossible to use the the plasma-widget-networkmanagement without kwallet?

---

