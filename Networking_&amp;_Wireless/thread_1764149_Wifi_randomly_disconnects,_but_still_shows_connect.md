---
title: "Wifi randomly disconnects, but still shows connection."
date: 2011-05-21
forum: Networking &amp; Wireless
---

### Post by drazelian on 2011-05-21
This one is driving me nuts. Im on ubuntu 111.04, and have been so since early april. It's been happening in the past few days. I think it started right after I installed tor network and vidalia from the software center. I didnt like them and uninstalled both the next day. This was on Wednesday. 

I use a wireless internet network, and about every 5 minutes, the network just stops working. If i'm in the middle of a youtube video, it will stop loading. If im downloading something  it will stop downloading. A page will halt refreshing midway.
Whats weird is that the network notifier sill shows that my connection is fine, and the "network disconnected" box doesn't pop up. If I go into the drop down wireless menu, click on my network again, it will load up and work fine for about 5 minutes.

All other wireless devices in this house work perfectly fine and do not have this problem, as well as another 11.04 laptop.

Any help would be greatly appreciated.

---

### Post by juliobahar on 2011-05-29
I'm having the exact same problem with my desktop pc, especially after upgrading it to ubuntu 11.04 -never suffered this before.

I thought I solved the problem by replacing native network-manager with WICD, then I changed my G-series Realtek USB adapter with a D-Link DWA 125 N-series USB WIFI adapter.

But today after fiddling around with the connection and my android phone, this same - pain in the neck - problem arose to the surface. At this very moment I can connect wirelessly to my router but I'm absolutely unable to get internet thru with this PC

Btw all other phones and laptops in my house are working fine.

---

### Post by GSF1200S on 2011-06-21
> **drazelian said:**
> This one is driving me nuts. Im on ubuntu 111.04, and have been so since early april. It's been happening in the past few days. I think it started right after I installed tor network and vidalia from the software center. I didnt like them and uninstalled both the next day. This was on Wednesday. 

I use a wireless internet network, and about every 5 minutes, the network just stops working. If i'm in the middle of a youtube video, it will stop loading. If im downloading something  it will stop downloading. A page will halt refreshing midway.
Whats weird is that the network notifier sill shows that my connection is fine, and the "network disconnected" box doesn't pop up. If I go into the drop down wireless menu, click on my network again, it will load up and work fine for about 5 minutes.

All other wireless devices in this house work perfectly fine and do not have this problem, as well as another 11.04 laptop.

Any help would be greatly appreciated.

Please post the results of the following commands:

```
lsmod
lsusb
lspci
iwconfig
ifconfig
cat /etc/network/interfaces
```

Also, see post #12 on this thread:
[http://ubuntuforums.org/showthread.php?t=1738030&page=2&highlight=DWA-125](http://ubuntuforums.org/showthread.php?t=1738030&page=2&highlight=DWA-125)

---

