---
title: "No network connection as guest in VirtualBox"
date: 2012-02-02
forum: Networking &amp; Wireless
---

### Post by three_jeeps on 2012-02-02
Host OS is WinXP sp3, guest OS is Ubuntu 10.1 and VirtBox is v4.18
Dell xps laptop with wireless connection.
XP sees the network fine.  Ubuntu cannot reach network -e.g. ping results in 'Network Unreachable'...
Netstat -r shows an empty routing table.
Ifconfig shows:
eth2      Link encap:Ethernet  HWaddr 08:00:27:20:9a:18  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:184 errors:0 dropped:0 overruns:0 frame:0
          TX packets:184 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:13952 (13.9 KB)  TX bytes:13952 (13.9 KB)

VirtualBox shows eth2 as IntelPro/1000 desktop attached to NAT.

dhclient shows:
Listening on LPF/eth3/08:00:27:df:56:a1
Sending on   LPF/eth3/08:00:27:df:56:a1
Listening on LPF/eth2/08:00:27:20:9a:18
Sending on   LPF/eth2/08:00:27:20:9a:18
Sending on   Socket/fallback
DHCPDISCOVER on eth3 to 255.255.255.255 port 67 interval 3....

Firewall is down on xp(host OS).
I am lost....what do I need to do to make Ubuntu (guest OS) see the network???????
Am communicating to a router over wireless...and it worked yesterday....I have NO clue what happend....Help Pls!?!?!?! What should I do?
-John

---

