---
title: "Wireless stuck on 1Mb/s, running 12.10 (WiFi Link 5100("
date: 2013-01-15
forum: Networking &amp; Wireless
---

### Post by danbrownlow on 2013-01-15
I'm getting incredibly low internet speeds, it doesn't go above 1Mb/s and it's hard to get anything done. I've looked around and found a few solutions before, but they don't appear to have done anything.

Any help would be appreciated!

Thank you.


sudo lshw -C network:

```

  *-network
       description: Wireless interface
       product: WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       serial: 00:24:d6:3c:d5:1c
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.5.0-21-generic firmware=8.83.5.1 build 33692 ip=192.168.2.39 latency=0 link=yes multicast=yes wireless=IEEE 802.11abg
       resources: irq:47 memory:d6500000-d6501fff


```

---

### Post by ahallubuntu on 2013-01-15
One possible solution (if you haven't tried it) is to set an option to limit the card to communicating at 54Mbps (diable 802.11n basically).  You can find this solution by googling - I have seen it before but forgotten the specifics.

I have no speed issues with my Intel 5100 card in Ubuntu 12.04 LTS.  I regularly transfer files from my NAS via wireless and get around 5Mbytes/second sustained transfer speed via my 802.11n router.

In fact, I have a couple of laptops with this same 5100 card and have had great luck with it in Linux.  Mostly Dell laptops; one is an Acer netbook.  I wonder if there is some compatibility issues with certain routers?  I suppose it could be something with 12.10 - I have barely used it.  Have you tried booting 12.04 LTS and see if you have the same issues?

What kind of laptop is it?  Make/model?  If it's an HP or Lenovo, you have a slightly different version of the 5100 than the cards I use.

---

