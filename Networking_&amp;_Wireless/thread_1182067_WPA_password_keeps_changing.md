---
title: "WPA password keeps changing?"
date: 2009-06-08
forum: Networking &amp; Wireless
---

### Post by WarpHorse on 2009-06-08
I recently installed the latest version of ubuntu, my first time installing any kind of linux. Everything is working great except that whenever I enter the correct WPA key for my router into the network manager and I go back to check it, it's a totally different giant line of strange numbers and letters. I can't connect to my wireless because of this.

---

### Post by duanedesign on 2009-06-08
The scrambling of the password is a security feature and perfectly normal.

There are some bug reports floating around with similar problems as yours. What wireless card do you have? 
You can run
```
 lspci
``` 
and look for the following:

```
*-network
    description: Wireless interface
    product: AR928X Wireless Network Adapter
    vendor: Atheros
    ect...
    ect...
capabilities: bus_master cap_list logical ethernet physical wireless
configuration: broadcast=yes driver=ath9k latency=0 module =ath9k wireles=IEEE 802.11abgn 
```

post that.
that will help in narrowing down which bug you might be suffering from.

---

### Post by WarpHorse on 2009-06-08
Thanks for the quick reply :) My network card is an Atheros Communications ar5008 wireless network adapter.

---

