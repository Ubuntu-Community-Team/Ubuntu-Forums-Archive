---
title: "eth2 showing up but its not defined anywhere"
date: 2009-10-05
forum: Networking &amp; Wireless
---

### Post by chrislynch8 on 2009-10-05
Hi,

I have ONLY two NICs in my server eth0 and eth1. They are defined in /etc/network/interfaces and are working correctly i.e. I have internet access and the LAN is fully functional.

When I issue ifconfig I get the following interfaces which are correct.
eth0
eth1
ppp0
tun0
lo

If I issue ifconfig eth2 I get the following.
```

Link encap:Ethernet    HWaddr 00:1C:23:CO:F7:74
BROADCAST MULTICASET    MTU:1500    Metric:1
RX   packets:0 erros:0 dropped:0 overruns:0 frame:0
TX   packets:0 erros:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0b)    TX bytes:0 (0.0b)
Interrupt:169 Memory:f8000000-f8011100

```

I have a custom program that is used to monitor all comms and automatically fix any problems, this works as expected and it currently running on 4 servers.

The Interrupt and Memory info on eth2 is odd as this is not shown for any other interfaces, so this leaves me to believe that it is setup as a virtual NIC or something???

Rgds
Chris

---

### Post by Iowan on 2009-10-05
Does the MAC address (Hwaddr) match one of the others?
Does it show up in **lshw -C network**?

---

