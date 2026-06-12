---
title: "BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller ndiswrapper 1.55 breaks"
date: 2009-10-05
forum: Networking &amp; Wireless
---

### Post by gmatt on 2009-10-05
I have the following network adapter. 

*-network:1 UNCLAIMED
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: c
       bus info: pci@0000:00:0c.0
       version: 02
       width: 32 bits
       clock: 33MHz

I have had it working in previous versions of ubuntu with ndiswrapper-1.11 with the windows xp drivers.


I'm at my wits end, I have tried for hours to figure out how to install an older version of ndiswrapper because obviously this new version has broken my driver. 

When I run ndiswrapper -l I have 

```

ndiswrapper -l
wmp54gsa : driver installed
	device (14E4:4318) present (alternate driver: ssb)



```

Just as before with ndiswrapper-1.11 (now its 1.55).

when I modprobe ndiswrapper I get 

```


 2549.358413] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[ 2549.406075] ndiswrapper: driver wmp54gsa (Linksys,12/06/2004, 3.90.16.0) loaded
[ 2549.407372] ndiswrapper 0000:00:0c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 2549.414943] ndiswrapper (NdisWriteErrorLogEntry:190): log: C000138D, count: 1, return_address: fa88cd1a
[ 2549.414952] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0x10e
[ 2549.415024] ndiswrapper (mp_init:219): couldn't initialize device: C0000001
[ 2549.415030] ndiswrapper (pnp_start_device:435): Windows driver couldn't initialize the device (C0000001)
[ 2549.415044] ndiswrapper (mp_halt:262): device eb21e480 is not initialized - not halting
[ 2549.415047] ndiswrapper: device eth%d removed
[ 2549.416215] ndiswrapper 0000:00:0c.0: PCI INT A disabled
[ 2549.416234] ndiswrapper: probe of 0000:00:0c.0 failed with error -22
[ 2549.422087] usbcore: registered new interface driver ndiswrapper



```

So I have tried to compile 1.11 from source so I can ues it again since I know it works. But then I get the following error

```

make[2]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
scripts/Makefile.build:46: *** CFLAGS was changed in "/home/basia/ndiswrapper-1.11/driver/Makefile". Fix it to use EXTRA_CFLAGS.  Stop.


```

After googling this error I found that it simply means that the kernel version and the driver I am trying to compile are not compatible and so there is nothing I can do about it. Is that true, am I forced to buy a new wifi card because I've upgraded to a new kernel?

---

