---
title: "Setting Temporary Static IP Address"
date: 2011-01-12
forum: Networking &amp; Wireless
---

### Post by mildenhall on 2011-01-12
I have a wireless printer server Netgear WGPS 606.

My router assigns 192.168.1.x and the IP addresses.

My print server was originally configured using Windows with the print server's windows config program. My daughter's little fingers have managed to do a factory reset. I no longer have a windows PC so....

I need to re-configure the print server. It's config page is at 192.168.0.102 and my Ubuntu 10.10 computer uses 192.168.1.x. I have turned wireless off, and have connected directly (wired) to the print server. Sadly my Ubuntu PC does not see 192.168.0.102.  

From reading, I need to set a static IP address on my Ubuntu PC to 192.168.0.x to see the config page at 192.168.0.102. It seems rather long winded and a bit dangerous getting back to dynamically linked IP address. Is there a way I can temporarially set my IP address please?

TIA

---

### Post by ripat on 2011-01-12
Simply:
```
$ sudo ifconfig eth0 192.168.0.x
```

---

### Post by mildenhall on 2011-01-12
Brilliant! Easier than I thought. Does that just stay active until a reboot, or do I need to reset it? Thanks

---

### Post by ripat on 2011-01-12
Yes, your original network settings will be restored at the next reboot but you even don't need to reboot. If you are using network manager, just do:
```
$ sudo restart network-manager
```

---

