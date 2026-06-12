---
title: "basic NFS question"
date: 2009-09-03
forum: Networking &amp; Wireless
---

### Post by methodtwo on 2009-09-03
Hi there
erm if i have an NFS server that uses a wireless interface.And this server is assigned its I.P address via dhcp from a router.Then for the client to mount one of this server's exported directories i would have to find the server's I.P address with, say, ifconfig.Then i would have to mount the directory(ies) using the server's I.P address in the mount command.Is there a way to have the server use DHCP and not have to go through the above proceedure?

---

### Post by methodtwo on 2009-09-03
I know i could just assign the server a static I.P address.I was just wondering if there is a way to achieve the same using DHCP?

---

### Post by Jose Catre-Vandis on 2009-09-03
Give the server a name on your client computers:
```
sudo nano /etc/hosts
```

However, this relies on the dhcp server consistently issuing the same IP address to your server, which it should do (if you don't mess around too much with the settings and configuration)

But as you say, a fixed IP is a much better solution, and a server should have a fixed IP for the very reason of always being able to find it!

---

