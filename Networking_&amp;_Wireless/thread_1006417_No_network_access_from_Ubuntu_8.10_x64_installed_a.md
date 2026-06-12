---
title: "No network access from Ubuntu 8.10 x64 installed as a guest on VMWare 6.5"
date: 2008-12-09
forum: Networking &amp; Wireless
---

### Post by dmee on 2008-12-09
Hello everybody,

I have installed Ubuntu 8.10 x64 as a guest on VMWare Workstation 6.5 which is being hosted by Windows Vista x64.

I have chosen NAT as a network connection type between host and guest. And there is no internet on the Ubuntu virtual machine.

Which is weird because Ubuntu machine is assigned with a valid IP from my host machine and it can even do pings (like ping ubuntuforums.org).

But no Firefox and no "apt-get install". What can be wrong with this configuration?

Here is the ifconfig result for Ubuntu (also check the screenshot attached – **Default route and Primary DNS are set to 192.168.125.2** – why?):
```
eth0      Link encap:Ethernet  HWaddr 00:0c:29:ae:9d:b3  
          inet addr:192.168.125.128  Bcast:192.168.125.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:feae:9db3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:23 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3639 (3.6 KB)  TX bytes:9329 (9.3 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:242 errors:0 dropped:0 overruns:0 frame:0
          TX packets:242 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15132 (15.1 KB)  TX bytes:15132 (15.1 KB)
```

And here is the ipconfig result for Windows machine (**note the default IPv4 address**):
```

Ethernet adapter VMware Network Adapter VMnet8:

   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : VMware Virtual Ethernet Adapter for VMnet
8
   Physical Address. . . . . . . . . : 00-50-56-C0-00-08
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
   Link-local IPv6 Address . . . . . : fe80::44fe:6684:aa1c:aead%21(Preferred)
**   IPv4 Address. . . . . . . . . . . : 192.168.125.1(Preferred)**
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . :
   DHCPv6 IAID . . . . . . . . . . . : 536891478
   DHCPv6 Client DUID. . . . . . . . : 00-01-00-01-10-C6-7D-B5-00-16-EA-D4-D8-08

   DNS Servers . . . . . . . . . . . : fec0:0:0:ffff::1%1
                                       fec0:0:0:ffff::2%1
                                       fec0:0:0:ffff::3%1
   NetBIOS over Tcpip. . . . . . . . : Enabled
```

---

