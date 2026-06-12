---
title: "No Routing Table On Boot"
date: 2009-02-11
forum: Networking &amp; Wireless
---

### Post by andrew.bell.ia@gmail.com on 2009-02-11
Hi,

When I boot my system, the ethernet interface (eth0) comes up, but the routing table is empty.  I thought that putting information in /etc/network/interfaces was all that was necessary for configuration.  What am I missing?

Thanks,

---

### Post by Crafty Kisses on 2009-02-11
Does your wireless card appear when you run the following?
```
lspci
```
I'd also suggest you see if there's any network modules loaded, you can check by running the following:
```
lsmod
```

---

### Post by Iowan on 2009-02-11
Unless things have changed recently, Network Manager seems to ignore information entered in */etc/network/interfaces*. You can try [this]("http://www.prash-babu.com/2009/01/how-to-setup-static-ip-in-ubuntu.html") technique for static address.

I read in another thread that Network Manager keeps it's information in */etc/NetworkManager* (might be capitalized differently - I don't have Intrepid, so I can't check.)

---

### Post by andrew.bell.ia@gmail.com on 2009-02-13
Thanks for the thoughts, but I'm not using wireless.  TCP works fine.  If I run ifup on the adapter after boot, the routing table gets filled in and everything is OK, but this isn't happening automatically.

---

