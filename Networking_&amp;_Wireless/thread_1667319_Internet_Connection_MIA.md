---
title: "Internet Connection MIA"
date: 2011-01-14
forum: Networking &amp; Wireless
---

### Post by bxdobs on 2011-01-14
Running Ubuntu 10.04 LTS under VMWARE Player 3.1.3 on an XP Pro 3 machine ... this has been working fine for several months ... now for some reason even though eth0 is connected and I can ping both the local xp machine and the local router, I no longer have internet access. ... I have tried turning off the xp firewall ... repairing VMWARE installation ... at this point it is not clear where the issue lies, XP? VMP? or Umuntu ... any help would be appreciated

ifconfig (minus hw and inet6 address)

eth0      Link encap:Ethernet  HWaddr  
          inet addr:192.168.131.128  Bcast:192.168.131.255  Mask:255.255.255.0
          inet6 addr:  Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:539 errors:0 dropped:0 overruns:0 frame:0
          TX packets:553 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:46221 (46.2 KB)  TX bytes:52800 (52.8 KB)
          Interrupt:17 Base address:0x1080 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:35 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3205 (3.2 KB)  TX bytes:3205 (3.2 KB)

---

