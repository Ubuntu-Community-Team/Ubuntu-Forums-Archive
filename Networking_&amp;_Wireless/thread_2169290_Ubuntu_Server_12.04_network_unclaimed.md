---
title: "Ubuntu Server 12.04 network unclaimed"
date: 2013-08-21
forum: Networking &amp; Wireless
---

### Post by Marius_Radvan on 2013-08-21
Hello

I have just installed Ubuntu Server 12.04 and the network adapter is inactive. 
The output for ```
lspci -nnk | grep -iA2 eth
``` is

```

Ethernet controller [0200]: Atheros Communications Inc. Device [1969:e091] (rev 13)
Subsystem: Micro-Star International Co., Ltd. Device [1462:7758]
PCI bridge [0604]: AsMedia Technology Inc. ASM1083/1085 PCIe to PCI Bridge [1b21:1080] (rev 03)

```

and the output for ```
sudo lshw -C network
``` is
```

*-network UNCLAIMED
    description: Ethernet Controller
    product: Atheros Communications Inc.
    vendor: Atheros Communications Inc.
    physical id: 0
    bus info: pci@0000:02:00.0
    version: 13
    width: 64 bits
    clock: 33MHz
    capabilities: pm pciexpress msi msix bus_master cap_list
    configuration: latency=0
    resources: memory:f7c00000-f7c3ffff ioport:e0000(size=128)

```

If I try ```
sudo ifconfig eth0 up
``` I get: ```
eth0: ERROR while getting interface flags: No such device
```

---

### Post by chili555 on 2013-08-21
See post #4 here: [http://ubuntuforums.org/showthread.php?t=2166562](http://ubuntuforums.org/showthread.php?t=2166562) 

You have the same device and the fix is the same. It will be quite challenging to transfer the backports package, build-essential and linux-headers and all their dependencies with no available internet. Do you have another spare NIC available? Wireless?

Since the driver exists in kernel version 3.10 (backports-[COLOR="#FF0000"]3.10-2[/COLOR]), you could probably install the daily build of Ubuntu 13.10 and the device would work by default. You could certainly try the live CD to confirm.

---

### Post by Marius_Radvan on 2013-08-21
I checked that post and the author specified that the fix only works for 13.04. I have 12.04

---

### Post by chili555 on 2013-08-21
> **Marius_Radvan said:**
> I checked that post and the author specified that the fix only works for 13.04. I have 12.04Would you like for me to propose a fix for 12.04 that involves ..." It will be quite challenging to transfer the backports package, build-essential and linux-headers and all their dependencies with no available internet." ...or what? You know I can do it!

EDIT: The author of that post, a very handsome fellow, was stating that the solution was only *tested* for 13.04 and none other; not that it wouldn't work. I just loaded up the live CD for 12.04 and compiled the package with just one warning during 'make.' It does install and loads. As to whether it properly drives the device, I can't say. I don't have the device.

---

### Post by Marius_Radvan on 2013-08-21
Thanks for your help

---

### Post by Marius_Radvan on 2013-08-22
The solution from [http://ubuntuforums.org/showthread.php?t=2166562](http://ubuntuforums.org/showthread.php?t=2166562) worked, thank you.

---

### Post by chili555 on 2013-08-22
Awesome! Glad it's working.

---

