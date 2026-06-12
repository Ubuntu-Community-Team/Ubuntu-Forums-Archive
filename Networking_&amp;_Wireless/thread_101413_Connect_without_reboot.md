---
title: "Connect without reboot?"
date: 2005-12-09
forum: Networking &amp; Wireless
---

### Post by mechanic on 2005-12-09
If I boot the local router  *after* I boot the U. machine in the morning, I don't get a connection. After waiting a while at 'waiting for network connection to come up' in the boot sequence the machine times out on that one and moves on. If the router is booted (from cold - it's not on 24/7) after that - result: no connection. The only obvious way forward is to reboot the U. machine. There *must* be a method of forcing U. to remake the connection surely? Any ideas?

m.

Edit: OOPs forgot to set the 'mail responses' tag!

---

### Post by amohanty on 2005-12-09
```
dhclient eth0
```

replace eth0 with the name of your primary nic

HTH

---

### Post by mechanic on 2005-12-10
Thanks 'amohanty'; a quick look at the man page for dhclient reveals a powerful utility!

m.

---

### Post by amohanty on 2005-12-10
glad to be of help.

---

