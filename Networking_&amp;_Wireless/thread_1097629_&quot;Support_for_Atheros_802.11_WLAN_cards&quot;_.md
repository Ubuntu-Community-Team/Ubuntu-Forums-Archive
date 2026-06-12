---
title: "&quot;Support for Atheros 802.11 WLAN cards&quot;? I don't think so!"
date: 2009-03-16
forum: Networking &amp; Wireless
---

### Post by calvinps on 2009-03-16
Hi all!

When I looked on my hardware drivers thing on Intrepid, it says that it has support for the card I described above.

But when I put the details of my broadband modem into the network configuration thingy, nothing happens. I am using a wired connection just the now.

Can anyone provide a solution for this? Thanks

-Calvin

---

### Post by ugm6hr on 2009-03-16
Give more detail - see the wifi help link below.

---

### Post by calvinps on 2009-03-16
I did lshw -class network and here are the results:

```
calvinps@ubuntu:~$ lshw -class network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0

```

---

### Post by ugm6hr on 2009-03-16
Easy:
[http://ubuntuforums.org/showpost.php?p=6895635&postcount=2](http://ubuntuforums.org/showpost.php?p=6895635&postcount=2)

---

### Post by calvinps on 2009-03-16
Gee, thanks! It's working now!

-Calvin

---

