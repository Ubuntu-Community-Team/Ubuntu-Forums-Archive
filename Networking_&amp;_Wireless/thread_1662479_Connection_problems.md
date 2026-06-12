---
title: "Connection problems"
date: 2011-01-08
forum: Networking &amp; Wireless
---

### Post by lil8up on 2011-01-08
OK, so I just installed Ubuntu along side Windows 7 and I booted it up with one problem Ubuntu will not connect to a wireless or wired internet connection. I am clueless on what to do.
Windows 7 Home premium x64
Ubuntu 10.0 (something..)
Realteck RTL8188CE Wireless LAN 802.11n PCI-E NIC (wireless adapter)
Atheros AR8152 PCI-E Fast Ethernet Controller 
Any idea's on what I'm doing wrong or what the problem is?
Hope someone can help me fix this. :confused:

---

### Post by lil8up on 2011-01-08
Any help would be nice ):

---

### Post by PatchesTheCaveman on 2011-01-08
Go to Applications > Accessories > Terminal, and type each of the following commands, pressing Enter after each one:
```
lshw -C network
ifconfig -a
dmesg | grep -i ath
dmesg | grep -i rtl
```

Copy and paste the output to a reply to this thread.

---

