---
title: "Wifi driver conflicts with Nvidia driver"
date: 2010-07-04
forum: Networking &amp; Wireless
---

### Post by Pim. on 2010-07-04
After a few day work i managed to get ubuntu 10.04 working on my Sony Vaio z12x. It took the install of a new kernel, adjustment of grub and finaly install of the NVidia drivers.

Now the video card works, the wifi driver stopt working.

The Sony has a Intel Advanced-N 6200 wifi chip, lshw -C network says:

  *-network **DISABLED**
       description: Wireless interface
       product: Centrino Advanced-N 6200
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 35
       serial: 00:23:14:c3:35:d4
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:35 memory:b8100000-b8101fff

I found a link: [http://ubuntuforums.org/showpost.php?p=9127310&postcount=14](http://ubuntuforums.org/showpost.php?p=9127310&postcount=14) but the drivers won't compile or install (snapshot)

Any steps i can take ???

---

### Post by Pim. on 2010-07-05
I see i was wrong, i booted an old kernel without the Nvidia driver and the WIFI driver stays disabled :(

So i gotta search again, suggestios anyone ?

---

