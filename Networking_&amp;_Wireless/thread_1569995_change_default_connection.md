---
title: "change default connection"
date: 2010-09-07
forum: Networking &amp; Wireless
---

### Post by ishokenmei on 2010-09-07
Hi, everyone.  My computer has an onboard ethernet port (eth0) and pci  ethernet card (eth1).  It's set up as a router.  eth0 connects to  internet and eth1 connects to the LAN.   For some reason, eth1 is set as  default.  How can I change the default to eth0?  Thanks in advance.

---

### Post by linux-hack on 2010-09-07
well you could try by editing the network config file :

```
sudo vi /etc/network/interfaces
```

---

### Post by ishokenmei on 2010-09-07
Thanks for your reply, boogy9.  There are only two lines in the file /etc/network/interfaces: ```

auto lo
iface lo inet loopback

```
Can you tell me more detail about how to edit it so that eth0 becomes the default connection?

---

### Post by Iowan on 2010-09-07
Network Manager *should* be able to help with with the default route(s). You *should* be able to mark eth0 as local and add a route to eth0.

---

