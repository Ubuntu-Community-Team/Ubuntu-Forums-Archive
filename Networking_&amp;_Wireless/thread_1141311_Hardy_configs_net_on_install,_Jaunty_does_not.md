---
title: "Hardy configs net on install, Jaunty does not"
date: 2009-04-28
forum: Networking &amp; Wireless
---

### Post by ussndmac on 2009-04-28
Hi,

If I install hardy desktop iso, it finds and configs the network fine.

If I install jaunty desktop iso, it does not. But, it does load the drivers and I can config it by hand after first boot.

This a realtek PCI 8139 card.

---

### Post by Iowan on 2009-04-28
I'm curious if your */etc/network/interfaces* file has lines similar to: ```
auto eth1
iface eth1 inet manual
```

---

### Post by ussndmac on 2009-04-29
I don't have access to the machine art the moment, but...

I'm talking about before /etc even exists in the install process.

During the hardy install, it detects the nic, then offers to allow manual config of the network.

During the Jaunty install it never offers.

---

### Post by DenysT on 2009-04-29
I think there is something wrong with Jaunty install when it comes to networks. Running the live CD I was able to access my network and samba shares with no problems, however after I installed Jaunty I was unable to access any of my network until I edited the smb.conf file. Strange that the network would work just fine from the live CD but not from a clean install.

---

