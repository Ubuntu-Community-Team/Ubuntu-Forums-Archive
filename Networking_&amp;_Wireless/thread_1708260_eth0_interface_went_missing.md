---
title: "eth0 interface went missing"
date: 2011-03-16
forum: Networking &amp; Wireless
---

### Post by aravindprasad on 2011-03-16
Hi,

I am really stumped on how to sole this issue :confused:, please look at the dump below and throw some suggestions at me. I have already tried reloading the drivers, restarting the interface (which is missing) and every other solution I found on this forum (well... not exactly all of them but many of them)

uname -a gives
Linux hostname 2.6.35-27-generic #48-Ubuntu SMP Tue Feb 22 20:25:46 UTC 2011 x86_64 GNU/Linux

Thanks in advance,
-Aravind

```

user@host:/home/user# [COLOR="Red"]ifconfig -a[/COLOR]
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:216 errors:0 dropped:0 overruns:0 frame:0
          TX packets:216 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:72040 (72.0 KB)  TX bytes:72040 (72.0 KB)

user@host:/home/user# [COLOR="Red"]lshw -C network[/COLOR]
  *-network UNCLAIMED     
       description: Ethernet controller
       product: 82566DM-2 Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi cap_list
       configuration: latency=0
       resources: memory:e3200000-e321ffff memory:e3224000-e3224fff ioport:30e0(size=32)

user@host:/home/user# [COLOR="Red"]dmesg | grep e1000[/COLOR]
[    2.382887] e1000e: Intel(R) PRO/1000 Network Driver - 1.0.2-k4
[    2.382890] e1000e: Copyright (c) 1999 - 2009 Intel Corporation.
[    2.382924] e1000e 0000:00:19.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.382934] e1000e 0000:00:19.0: setting latency timer to 64
[    2.383068] e1000e 0000:00:19.0: irq 46 for MSI/MSI-X
[   11.260057] e1000e 0000:00:19.0: PCI INT A disabled
[   12.509610] uvesafb: framebuffer at 0xe1000000, mapped to 0xffffc9000c700000, using 14336k, total 14336k
[   39.462948] mtrr: base(0xe1000000) is not aligned on a size(0xe00000) boundary

user@host:/home/user# 

```

---

### Post by dandnsmith on 2011-03-16
If the interface was working, and then went missing, perhaps you have the same problem as I had a while back - the interface has died.

I tried changing cable ports, cable, and OS, and finally convinced myself to try a new ethernet card (which solved it).

Over to you, now

---

### Post by falko on 2011-03-16
Does your /etc/network/interfaces look ok?

---

### Post by adduds on 2011-03-16
sounds simple did you try 

```
sudo ifup eth0
```

---

### Post by aravindprasad on 2012-02-15
Just to close this thread.

I took dandnsmith's suggestion and got a new $5 network card. And that solved the problem.

However there is an interesting point here. Once I put in the new PCI NIC, both the new NIC and the old onboard NIC started working fine. 

Now the old onboard card gets an address and works perfectly fine but only as long as the new NIC is sitting in its PCI slot. I wonder if some hardware component has failed on the onboard one and somehow its equivalent component on the new card surrogates for both the new and old NICs.

Thanks and regards,
-Aravind

---

