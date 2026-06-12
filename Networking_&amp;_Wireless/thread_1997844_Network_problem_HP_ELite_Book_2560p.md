---
title: "Network problem HP ELite Book 2560p"
date: 2012-06-05
forum: Networking &amp; Wireless
---

### Post by bol on 2012-06-05
Dear Everyone: Now, twice more info below original post. Problem still not solved. Hope for assistance.

Have just installed 10.04LTS (because that is what I am running without any problem on four other computers) on my brand new HP Elite Book 2560p.

Everything - I think - runs like a dream, except wired network. My network card (Eth0) is simply not discovered. Wireless network connection works without a glitch. Does anyone know a remedy?

Thanks in advance for your assistance.

Bo L

Have found that the Elite Book has an "Unknown Interface (pan0)" that none of my other computers have. This pan0 interface has a hardware address but is not active and I have no clue as to configure it.

My other prtable HP, a quite old nx7400 (also sold as Compaq), shows no sign of any pan0 interface but sports a fully working eth0.

Still hoping for your assitance!

Bo L

MORE INFO:
~$ ifconfig eth0
eth0: error fetching interface information: Device not found

and here it is, but 'unclaimed' How do I claim it?


~$ sudo lshw -C network
  *-network UNCLAIMED     
       description: Ethernet controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       version: 04
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list
       configuration: latency=0
       resources: memory:d4700000-d471ffff memory:d472a000-d472afff ioport:4060(size=32)
  *-network
       description: Wireless interface
       product: WiFi Link 6000 Series
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:24:00.0
       logical name: wlan1
       version: 3e
       serial: 24:77:03:70:f5:9c
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=192.168.1.187 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:29 memory:d4400000-d4401fff

---

