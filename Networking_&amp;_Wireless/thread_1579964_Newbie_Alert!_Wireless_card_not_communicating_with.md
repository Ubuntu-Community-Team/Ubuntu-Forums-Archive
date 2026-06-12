---
title: "Newbie Alert! Wireless card not communicating with kernel"
date: 2010-09-22
forum: Networking &amp; Wireless
---

### Post by cinemaniac on 2010-09-22
Hi,

I'm a 3 day old convert to ubuntu from windows. Have enjoyed my experience so far in spite of having loads of issues migrating (there's an unbelievable thrill in the learning experience). Anyways, here's the issue...

I'm using ubuntu 10.04LTS on an Intel D101GGC board. I also have a Belkin PCI Wireless Ethernet card along with the onboard Realtek 8139. Both cards have been working without any hassles ever since I migrated. However, I'd disabled the wired ethernet and was using only the wireless to connect to my router.

I went out for dinner a couple of hours ago and on starting up my computer once I returned, I see that the wireless is disabled. I tried the troubleshooting steps in the wiki [here]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported"). I found out that my system is recognising the card and also has the drivers installed (pasting the output of **lshw** for reference)

```

*-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth0
       version: 10
       serial: 00:13:20:c8:e3:b6
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.2 latency=64 maxlatency=64 mingnt=32 multicast=yes
       resources: irq:21 ioport:de00(size=256) memory:fddff000-fddff0ff

*-network:1
       description: Ethernet controller
       product: Belkin
       vendor: Belkin
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 20
       width: 32 bits
       clock: 33MHz
       configuration: driver=rtl8180 latency=64 maxlatency=64 mingnt=32
       resources: irq:16 ioport:dc00(size=256) memory:fdd00000-fdd001ff

```But the kernel is not communicating with the device as per the troubleshooting guide (pasting the output of the **iwconfig** command)

```

lo        no wireless extensions.

eth0      no wireless extensions.

```This is where the troubleshooting guide lost me. Not very sure what to do next. Any help would be greatly appreciated.

Thanks & cheers,

Sam :)

---

### Post by stardustdk on 2010-09-22
You might try this page:

> [http://www.ubuntugeek.com/how-to-troubleshoot-wireless-network-connection-in-ubuntu.html](http://www.ubuntugeek.com/how-to-troubleshoot-wireless-network-connection-in-ubuntu.html)


Best regards

---

### Post by cinemaniac on 2010-09-23
Thanks :)

Had to reinstall my drivers and I'm through. Everything is in order. :)

---

