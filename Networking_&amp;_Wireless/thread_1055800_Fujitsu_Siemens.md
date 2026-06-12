---
title: "Fujitsu Siemens"
date: 2009-01-31
forum: Networking &amp; Wireless
---

### Post by DroKZ on 2009-01-31
Hello,

Since a couple of months i have a Fujitsu Siemens Laptop.
Great laptop but i did have problems with enabling wireless.

This thread: [http://ubuntuforums.org/showthread.php?t=644899](http://ubuntuforums.org/showthread.php?t=644899)
helped me solving my problem. Great!

The wireless card is an Atheros AR5007EG.

Yesterday i started the update wizard. There were a lot of updates including some new kernel updates (don't know exactly.. x.x.23-rt)

So i updated all of these.
Today i started my laptop again.
My wireless led is on but wireless is not enabled. I can't find any wireless network and networkmanager didn't show me the wireless option..

Any also have got this problem since the last updates and has a solution how to solve this?

*edit: Even after trying an older kernel version wifi doesn't work*
*another edit:
Output 

My update history from yesterday:

```

Commit Log for Fri Jan 30 23:29:50 2009


Upgraded the following packages:
linux-headers-2.6.24-23 (2.6.24-23.46) to 2.6.24-23.48
linux-headers-2.6.24-23-rt (2.6.24-23.46) to 2.6.24-23.48
linux-image-2.6.24-23-rt (2.6.24-23.46) to 2.6.24-23.48
linux-libc-dev (2.6.24-23.46) to 2.6.24-23.48
python-apt (0.7.4ubuntu7.3) to 0.7.4ubuntu7.4
python-gobject (2.14.2-0ubuntu1) to 2.14.2-0ubuntu2

```

Ouput of lshw:
```

           *-network UNCLAIMED
                description: Ethernet controller
                product: AR242x 802.11abg Wireless PCI Express Adapter
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:08:00.0
                version: 04
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix bus_master cap_list
                configuration: latency=0

```

little piece of output from lspci:
```

08:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 04)
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)

```


Thanks in advance.
Jos

---

### Post by DroKZ on 2009-01-31
Problem is solved.

I had to go to the dir from Madwifi & acerhk and just type
make & make install.

After that simple reboot and everything works fine again

---

