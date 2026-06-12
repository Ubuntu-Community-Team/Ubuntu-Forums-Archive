---
title: "e1000e corrupt EEPROM, NVM checksum invalid no ethernet device"
date: 2011-04-24
forum: Networking &amp; Wireless
---

### Post by dookiebowser on 2011-04-24
Having an issue with Intel Corporation 82573L Gigabit Ethernet Controller. I have no ethX detected, modprobe fails.

System detects the hardware:
```
$ lspci -v | grep 82573L
05:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
```

I have no eth0 due to modprobe failing:

```

[ 2419.341237] e1000e: Intel(R) PRO/1000 Network Driver - 1.3.10a-NAPI
[ 2419.341244] e1000e: Copyright(c) 1999 - 2011 Intel Corporation.
[ 2419.341291] e1000e 0000:05:00.0: Disabling ASPM  L1
[ 2419.341314] e1000e 0000:05:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[ 2419.341348] e1000e 0000:05:00.0: setting latency timer to 64
[ 2419.342039]   alloc irq_desc for 47 on node -1
[ 2419.342044]   alloc kstat_irqs on node -1
[ 2419.342072] e1000e 0000:05:00.0: irq 47 for MSI/MSI-X
[ 2419.342098] e1000e 0000:05:00.0: Disabling ASPM L0s 
***[ 2419.403258] e1000e 0000:05:00.0: (unregistered net_device): The NVM Checksum Is Not Valid
[ 2419.413563] e1000e 0000:05:00.0: PCI INT A disabled
***[ 2419.413579] e1000e: probe of 0000:05:00.0 failed with error -5

```

But Edubuntu (Meerkat), Ubuntu (Lucid) show the module as loaded:
```

$ lsmod | grep e100
e1000e                138991  0 

```

```

$ sudo lshw -C network
  *-network UNCLAIMED
       description: Ethernet controller
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:da000000-da01ffff ioport:4000(size=32)

```

 I am 90% sure this is the issue:
[https://bugzilla.redhat.com/show_bug.cgi?id=459202](https://bugzilla.redhat.com/show_bug.cgi?id=459202)

There is a driver with checksum bypass:
[https://bugzilla.redhat.com/attachment.cgi?id=317425](https://bugzilla.redhat.com/attachment.cgi?id=317425)

But has suffered "bitrot" and cannot be built with the current kernels.

The bypass driver is e1000e-0.4.1.7, the current version of the driver is e1000e-1.3.10a:

[http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=15817&ProdId=2198&lang=eng&OSVersion=Linux*&DownloadType=Drivers](http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=15817&ProdId=2198&lang=eng&OSVersion=Linux*&DownloadType=Drivers)



**Please someone tell me how I can remedy this.** The person that posted the checksum bypass also posted the code that was changed in the driver to make this hack work:

[https://bugzilla.redhat.com/show_bug.cgi?id=459202#c12](https://bugzilla.redhat.com/show_bug.cgi?id=459202#c12)

This is beyond my skills.

---

### Post by dookiebowser on 2011-04-25
I found these posts:

[https://bugzilla.kernel.org/show_bug.cgi?id=11382](https://bugzilla.kernel.org/show_bug.cgi?id=11382)

[http://lkml.org/lkml/2008/10/17/214](http://lkml.org/lkml/2008/10/17/214)

Somebody named Karston Keil at Suse.de was helping people restore their EEPROM and fix the issue, but since it has been so long (3 years now), I cannot reach him.


So the question is, does anybody have an EEPROM image for an HP dv6375....

Or, can I get this working by modifying the current driver to bypass the checksum?

There is a .sh fix included in the readme of the e1000e driver for an EEPROM issue, but it relies on using ethtool on eth0. I have no eth0.

I also might be able to use ethtool to edit the EEPROM, but don't know how or what to change.

```

       ethtool -e|--eeprom-dump DEVNAME    Do a EEPROM dump
        [ raw on|off ]
        [ offset N ]
        [ length N ]
        ethtool -E|--change-eeprom DEVNAME    Change bytes in device EEPROM
        [ magic N ]
        [ offset N ]
        [ length N ]
        [ value N ]

```

---

### Post by dookiebowser on 2011-04-25
I also have a "PXE-E05" LAN error on bootup. 

PXE-E05 EEPROM checksum error This message is displayed if the NIC EEPROM contents have been corrupted. This can happen if the system is reset or powered down when the NIC                           EEPROM is being reprogrammed. If this message is displayed, the configured bootstrap type (Int 18h, 19h,   PnP/BEV) has been lost and a default bootstrap type is selected. The default bootstrap type will be set to     PnP/BEV if the system supports the PnP/BBS runtime functions. If the PnP/BBS runtime functions are not       supported, Int 18h is the default bootstrap

---

### Post by sorcerer01 on 2011-06-30
exactly same issue here. 
same situation, even the bootstrap error.
no solution available.
HP Pavilion dv6236ea

---

### Post by sorcerer01 on 2011-07-01
issue probably solved, take a look at :

[http://thesorcerer.wordpress.com/2011/07/01/guide-intel-82573l-gigabit-ethernet-with-ubuntu-11-04-and-fix-pxe-e05/](http://thesorcerer.wordpress.com/2011/07/01/guide-intel-82573l-gigabit-ethernet-with-ubuntu-11-04-and-fix-pxe-e05/)

---

