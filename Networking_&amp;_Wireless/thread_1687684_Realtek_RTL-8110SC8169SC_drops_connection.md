---
title: "Realtek RTL-8110SC/8169SC drops connection"
date: 2011-02-14
forum: Networking &amp; Wireless
---

### Post by larryfroot on 2011-02-14
Hi, hope you wonderful people can help. I have a wired net connection that often drops in the daytime but rarely evening and never late at night. The problem was in Jaunty as well (I skipped Karmic) and I am now running lucid. The ethernet hardware is Realtek RTL-8110SC/8169SC Gigabit Ethernet

The following is the above hardware as seen by hwinfo


```
hwinfo --netcard
33: PCI 108.0: 0200 Ethernet controller                         
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_10ec_8167
  Unique ID: rBUF.39IzRgA_gQD
  Parent ID: bSAa.M2gbdOfB0S7
  SysFS ID: /devices/pci0000:00/0000:00:0a.0/0000:01:08.0
  SysFS BusID: 0000:01:08.0
  Hardware Class: network
  Model: "Realtek RTL-8110SC/8169SC Gigabit Ethernet"
  Vendor: pci 0x10ec "Realtek Semiconifconfig[   19.704017] eth0: no IPv6 routers present
eth0      Link encap:Ethernet  HWaddr 00:1c:25:da:e4:92  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:25ff:feda:e492/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:39727 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40537 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:28995787 (28.9 MB)  TX bytes:9068520 (9.0 MB)
          Interrupt:16 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 ovhwinfo --netcard
33: PCI 108.0: 0200 Ethernet controller                         
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_10ec_8167
  Unique ID: rBUF.39IzRgA_gQD
  Parent ID: bSAa.M2gbdOfB0S7
  SysFS ID: /devices/pci0000:00/0000:00:0a.0/0000:01:08.0
  SysFS BusID: 0000:01:08.0
  Hardware Class: network
  Model: "Realtek RTL-8110SC/8169SC Gigabit Ethernet"
  Vendor: pci 0x10ec "Realtek Semiconductor Co., Ltd."
  Device: pci 0x8167 "RTL-8110SC/8169SC Gigabit Ethernet"
  SubVendor: pci 0x105b "Foxconn International, Inc."
  SubDevice: pci 0xff1f 
  Revision: 0x10
  Driver: "r8169"
  Driver Modules: "r8169"
  Device File: eth0
  I/O Ports: 0xce00-0xceff (rw)
  Memory Range: 0xefcff000-0xefcff0ff (rw,non-prefetchable)
  Memory Range: 0xefb00000-0xefb1ffff (ro,prefetchable,disabled)
  IRQ: 16 (101250 events)
  HW Address: 00:1c:25:da:e4:92
  Link detected: yes
  Module Alias: "pci:v000010ECd00008167sv0000105Bsd0000FF1Fbc02sc00i00"
  Driver Info #0:
    Driver Status: r8169 is active
    Driver Activation Cmd: "modprobe r8169"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #28 (PCI bridge)
erruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)
ductor Co., Ltd."
  Device: pci 0x8167 "RTL-8110SC/8169SC Gigabit Ethernet"
  SubVendor: pci 0x105b "Foxconn International, Inc."
  SubDevice: pci 0xff1f 
  Revision: 0x10
  Driver: "r8169"
  Driver Modules: "r8169"
  Device File: eth0
  I/O Ports: 0xce00-0xceff (rw)
  Memory Range: 0xefcff000-0xefcff0ff (rw,non-prefetchable)
  Memory Range: 0xefb00000-0xefb1ffff (ro,prefetchable,disabled)
  IRQ: 16 (101250 events)
  HW Address: 00:1c:25:da:e4:92
  Link detected: yes
  Module Alias: "pci:v000010ECd00008167sv0000105Bsd0000FF1Fbc02sc00i00"
  Driver Info #0:
    Driver Status: r8169 is active
    Driver Activation Cmd: "modprobe r8169"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #28 (PCI bridge)

```

And this is the output of ifconfig

```
[   19.704017] eth0: no IPv6 routers present
eth0      Link encap:Ethernet  HWaddr 00:1c:25:da:e4:92  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:25ff:feda:e492/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:39727 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40537 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:28995787 (28.9 MB)  TX bytes:9068520 (9.0 MB)
          Interrupt:16 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 ovhwinfo --netcard
33: PCI 108.0: 0200 Ethernet controller                         
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/ifconfig[   19.704017] eth0: no IPv6 routers present
eth0      Link encap:Ethernet  HWaddr 00:1c:25:da:e4:92  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:25ff:feda:e492/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:39727 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40537 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:28995787 (28.9 MB)  TX bytes:9068520 (9.0 MB)
          Interrupt:16 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 ovhwinfo --netcard
33: PCI 108.0: 0200 Ethernet controller                         
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_10ec_8167
  Unique ID: rBUF.39IzRgA_gQD
  Parent ID: bSAa.M2gbdOfB0S7
  SysFS ID: /devices/pci0000:00/0000:00:0a.0/0000:01:08.0
  SysFS BusID: 0000:01:08.0
  Hardware Class: network
  Model: "Realtek RTL-8110SC/8169SC Gigabit Ethernet"
  Vendor: pci 0x10ec "Realtek Semiconductor Co., Ltd."
  Device: pci 0x8167 "RTL-8110SC/8169SC Gigabit Ethernet"
  SubVendor: pci 0x105b "Foxconn International, Inc."
  SubDevice: pci 0xff1f 
  Revision: 0x10
  Driver: "r8169"
  Driver Modules: "r8169"
  Device File: eth0
  I/O Ports: 0xce00-0xceff (rw)
  Memory Range: 0xefcff000-0xefcff0ff (rw,non-prefetchable)
  Memory Range: 0xefb00000-0xefb1ffff (ro,prefetchable,disabled)
  IRQ: 16 (101250 events)
  HW Address: 00:1c:25:da:e4:92
  Link detected: yes
  Module Alias: "pci:v000010ECd00008167sv0000105Bsd0000FF1Fbc02sc00i00"
  Driver Info #0:
    Driver Status: r8169 is active
    Driver Activation Cmd: "modprobe r8169"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #28 (PCI bridge)
erruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)
pci_10ec_8167
  Unique ID: rBUF.39IzRgA_gQD
  Parent ID: bSAa.M2gbdOfB0S7
  SysFS ID: /devices/pci0000:00/0000:00:0a.0/0000:01:08.0
  SysFS BusID: 0000:01:08.0
  Hardware Class: network
  Model: "Realtek RTL-8110SC/8169SC Gigabit Ethernet"
  Vendor: pci 0x10ec "Realtek Semiconductor Co., Ltd."
  Device: pci 0x8167 "RTL-8110SC/8169SC Gigabit Ethernet"
  SubVendor: pci 0x105b "Foxconn International, Inc."
  SubDevice: pci 0xff1f 
  Revision: 0x10
  Driver: "r8169"
  Driver Modules: "r8169"
  Device File: eth0
  I/O Ports: 0xce00-0xceff (rw)
  Memory Range: 0xefcff000-0xefcff0ff (rw,non-prefetchable)
  Memory Range: 0xefb00000-0xefb1ffff (ro,prefetchable,disabled)
  IRQ: 16 (101250 events)
  HW Address: 00:1c:25:da:e4:92
  Link detected: yes
  Module Alias: "pci:v000010ECd00008167sv0000105Bsd0000FF1Fbc02sc00i00"
  Driver Info #0:
    Driver Status: r8169 is active
    Driver Activation Cmd: "modprobe r8169"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #28 (PCI bridge)
erruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.ifconfig0 B)
```

I also have some (edited) output from dsmeg | more if anyone wants to check that out too.

I am also very network ignorant, so please think of me as a small, confused child. Thank you for any help you can offer me, it really is most appreciated.

---

### Post by larryfroot on 2011-02-18
bump?

---

### Post by larryfroot on 2011-03-12
Any reply would be welome - perhaps even to point me to where I might find an answer. Thanks

---

### Post by drdos2006 on 2011-03-12
This is from a previous thread I saved because it helped me.
My ISP had made some changes to the network and I had constant dropouts until I disconnected IPv6.

> 
You may be having connection issues because of IPv6 even though it shows an IPv4 connection. 

 How do I prove ipv6 has been successfully disabled
There seems to be much disagreement between distros regarding how ipv6 is disabled, even between different versions of the same distro. Rather than just follow instructions for disabling ipv6 for a given distro, I would like to also test that ipv6 is not used any more. Any software or executable that relies on ipv6, that I can use to confirm that ipv6 has been successfully disabled?
From your server, type

cat /proc/sys/net/ipv6/conf/*/disable_ipv6
They should all be 1.

Disabling IPV6 is best done via sysctl. In ubuntu, add the following to /etc/sysctl.conf
From your terminal, type

sudo  gedit  /etc/sysctl.conf

Add the following lines.
# Disable IPV6
net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1


Reboot your server.
ifconfig should not mention an IPV6 address on any interface after you have rebooted.

IPV6 should still be considered in your security setup on your machine, just in case it is, for example, re-enabled after an upgrade etc.

To check if IPv6 is enabled, just simply use netstat:

Code:

netstat -tlv

If you see any "tcp6" entries, then IPv6 is not disabled.

You may be also having IPv6 problems in your browser.
For Firefox, type
 
about:config
 
in the browser bar.
Filter with IPv6
Change IPv6disabled to true
Restart Firefox.


regards

---

