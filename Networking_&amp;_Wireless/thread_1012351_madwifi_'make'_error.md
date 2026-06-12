---
title: "madwifi 'make' error"
date: 2008-12-15
forum: Networking &amp; Wireless
---

### Post by grnkry on 2008-12-15
hi, I'm having problems trying to get madwifi to set up on my laptop for a d-link dwa-642 card. I've tried following some guides on how to properly install it, but I keep getting an error when it gets to the 'make' command.

I'm _really_ new at this (decided to try something other than windows 2 days ago) and I don't even know commands for the konsole yet. I've pretty much just been copying straight out of the guides, so it's probably something simple that I'm just not able to see. This is what happens when I try to 'make'.
Any help would be greatly appreciated

```
eric@acerOne:~/Downloads/madwifi-0.9.3.2$ sudo make
[sudo] password for eric: 
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.27-9-generic/build SUBDIRS=/home/eric/Downloads/madwifi-0.9.3.2 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'
  CC [M]  /home/eric/Downloads/madwifi-0.9.3.2/ath/if_ath_pci.o
/home/eric/Downloads/madwifi-0.9.3.2/ath/if_ath_pci.c: In function 'ath_pci_probe':
/home/eric/Downloads/madwifi-0.9.3.2/ath/if_ath_pci.c:203: error: 'struct net_device' has no member named 'owner'
make[3]: *** [/home/eric/Downloads/madwifi-0.9.3.2/ath/if_ath_pci.o] Error 1
make[2]: *** [/home/eric/Downloads/madwifi-0.9.3.2/ath] Error 2
make[1]: *** [_module_/home/eric/Downloads/madwifi-0.9.3.2] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'
make: *** [modules] Error 2

```

---

### Post by moore.bryan on 2008-12-15
first things first; what *flavor* of ubuntu are you using?

---

### Post by grnkry on 2008-12-15
assuming flavour means what I think it is...it's 8.10 desktop edition.

---

### Post by moore.bryan on 2008-12-16
sorry... that *is* what i meant. you probably don't need to compile your own madwifi because intrepid includes the new atheros drivers natively. what, exactly, is the problem you're having?

---

