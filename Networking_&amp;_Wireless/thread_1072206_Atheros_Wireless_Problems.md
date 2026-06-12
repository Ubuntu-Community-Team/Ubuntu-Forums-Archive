---
title: "Atheros Wireless Problems"
date: 2009-02-17
forum: Networking &amp; Wireless
---

### Post by binbash on 2009-02-17
Hey guys, my friend gave his notebook to me to install ubuntu.Everything works perfect except this issue : 

I have atheros chipset wireless card : 

```

Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

```

I followed this howto : 

```
http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/
```

I disabled bluetooth and tried this both with wicd and network-manager-gnome

-Wireless works with this howto BUT when i restart the ubuntubox, i have to do sudo make unload && sudo make load to get it working (sometimes a couple of times).Yes i wrote the module to startup so it loads at startup
-At gnome network manager (also at conky) signal shows 0 when i connect to adhoc or any other network

My kernel is (i tried with 3 different kernels ) :

2.6.27-7-generic

Looking for a fix for my issues, thanks for reading



EDIT : I also tried madwifi method but it does not connect to anything with madwifi

---

### Post by binbash on 2009-02-17
Bump

---

### Post by Testrum on 2009-02-17
STCHMAN has a step-by-step tutorial on how to set up an Atheros WiFi card located [**here**.](http://www.stchman.com/ath_drv.html) Hope that helps.

~Testrum

---

### Post by Ketara on 2009-02-17
Just a thought, have you tried ndiswrapper?

I have that card working just fine with ndiswrapper on an HP dv8000 laptop.

---

