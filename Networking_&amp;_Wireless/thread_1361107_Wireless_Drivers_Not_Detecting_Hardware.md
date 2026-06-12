---
title: "Wireless Drivers Not Detecting Hardware"
date: 2009-12-21
forum: Networking &amp; Wireless
---

### Post by telecom369 on 2009-12-21
Ok
So last night my wireless drivers on my laptop failed on me.
I restarted the computer twice and downloaded ndiswrapper.
But nothing seems to work.

I run an Acer Aspire One with Ubuntu 9.10

In Network Tools, the only devices that come up are:
Loopback interface (lo)
Ethernet interface (eth0)

The contents of /etc/network/interfaces is:
auto lo
iface lo inet loopback

And when I try 'sudo mod_probe ath_pci', it comes back as:
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
FATAL: Module ath_pci not found.

Any Help?

---

### Post by Quarg on 2009-12-21
What hardware are you using?
If you don't know, post the output of 
```

lspci | grep Network

```
this looks for 'Network' in the output of lspci, which will tell us what network hardware your using

---

### Post by Quarg on 2009-12-21
Oh...
reading your post, it looks like you've got an atheros card. 
Personally, I do not like using ndiswrapper. ath_pci didn't work for my atheros card, I got the ath5k module, which (back in the intrepid days) was in a backports package of some sort. You might want to try disabling ndiswrapper, downloading the ath5k module (should be available in the package manager under some modules package) and blacklisting ath_pci in a blacklist file in /etc/modprobe.d/ directory.

---

