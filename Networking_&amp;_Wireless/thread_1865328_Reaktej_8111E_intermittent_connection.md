---
title: "Reaktej 8111E intermittent connection"
date: 2011-10-20
forum: Networking &amp; Wireless
---

### Post by gonintendo on 2011-10-20
My mother board is an MSI 768A-GD65 (B3) and its integrated lan chip is the realtek 8111E. I will randomly have my Internet cut out. It still shows that it's connected in the status area, but firefox (and chromium) will either say connecting for a minute until the page finally loads or just timeout alltogether. This is very annoying. The issue is present in both ubuntu 11.10 and kubuntu 11.10.

---

### Post by varunendra on 2011-10-20
Please post outputs of:
```
sudo lshw -C network
ifconfig
```

---

### Post by verymadpip on 2011-10-20
Some of us are having the same issue. People are trying to help, look here:

[http://ubuntuforums.org/showthread.php?t=1855441](http://ubuntuforums.org/showthread.php?t=1855441)

I've tried the method in praseodym's link & all seems well at the moment.
If the 'autogen' command doesn't work try 'autorun'
I also installed the packages 'build essential' & 'dkms'.  I don't  know if I needed to, but I read in another thread that I might need  them.

Good luck & keep us posted :)

---

### Post by gonintendo on 2011-10-20
ifconfig:
> eth0      Link encap:Ethernet  HWaddr 8c:89:a5:2d:17:73  
          inet addr:192.168.2.106  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::8e89:a5ff:fe2d:1773/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:886 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1036 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:496964 (496.9 KB)  TX bytes:250131 (250.1 KB)
          Interrupt:47 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:400 (400.0 B)  TX bytes:400 (400.0 B)


I'll try that fix out when I get home from work. Thanks guys!

---

### Post by gonintendo on 2011-10-20
lshw -C network
>   *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 06
       serial: 8c:89:a5:2d:17:73
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=N/A ip=192.168.2.106 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:47 ioport:b000(size=256) memory:da104000-da104fff memory:da100000-da103fff


---

### Post by varunendra on 2011-10-21
gonintendo,

Assuming you are using kernel 3x, please follow the link *verymadpip* has provided. The same issue, with kernel 3x has been confirmed to be solved there by *preseodym*, a much more experienced networking expert.

Alternatively you may follow this link (which alone is sufficient for kernel 2x): [http://ubuntuforums.org/showthread.php?p=11053381&postcount=6](http://ubuntuforums.org/showthread.php?p=11053381&postcount=6)
especially edits 1 and 3 in post #6 which may provide alternative solutions for kernel 3x. The one provided by praseodym is confirmed to be working by *verymadpip *though. So you may have better luck with that one.

Please confirm which method worked for you. It'll be a great contribution for others as this is a very common chip.

---

