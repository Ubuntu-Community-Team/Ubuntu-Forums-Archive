---
title: "Enabling Wireless (I've searched)"
date: 2009-03-29
forum: Networking &amp; Wireless
---

### Post by tdawg on 2009-03-29
Wireless not showing up in Network Configuration Panel. I can fix this problem by restarting computer, going into windows, and enabling it via a friends user interfaced program. Don't feel like having to do this every time. So how do I enable my wireless? Here's some useful information:



```
lo        no wireless extensions.

eth0      no wireless extensions.

```

```

eth0      Link encap:Ethernet  HWaddr 00:0f:1f:21:c9:c8  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:1fff:fe21:c9c8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:125819 errors:0 dropped:0 overruns:0 frame:0
          TX packets:69186 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:180952059 (172.5 MB)  TX bytes:6349266 (6.0 MB)
          Interrupt:11 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1148 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1148 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:57400 (56.0 KB)  TX bytes:57400 (56.0 KB)


```


```
  *-network:1 UNCLAIMED
                description: Network controller
                product: PRO/Wireless 2200BG Network Connection
                vendor: Intel Corporation
                physical id: 3
                bus info: pci@0000:02:03.0
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=32 maxlatency=24 mingnt=3

```

---

### Post by miegiel on 2009-03-29
Is there a wan0 (or was it wlan0?) listed in your /etc/network/interfaces ? If the interfaces file makes no sense to you just quote it here :)

---

### Post by tdawg on 2009-03-29
If you mean is it showing up where the wired connection is in the interface, then no.

---

### Post by miegiel on 2009-03-29
> **tdawg said:**
> If you mean is it showing up where the wired connection is in the interface, then no.

No, I mean what's in your /etc/network/interfaces file, you can open it with a text editor.

---

