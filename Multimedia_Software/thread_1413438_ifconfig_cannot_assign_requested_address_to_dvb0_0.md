---
title: "ifconfig cannot assign requested address to dvb0_0 interface created with dvbnet"
date: 2010-02-22
forum: Multimedia Software
---

### Post by juliansomers on 2010-02-22
Hello!

I cannot bring up an interface for dvb/ip using ifconfig :

root@atom-test:~# ifconfig dvb0_0 up
SIOCSIFFLAGS: Cannot assign requested address

root@atom-test:~# ifconfig dvb0_0
dvb0_0    Link encap:Ethernet  HWaddr 00:00:00:00:00:00
          inet addr:192.168.238.238  Bcast:192.168.238.255  Mask:255.255.255.0
          BROADCAST NOARP MULTICAST  MTU:4096  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Base address:0x13ba

The interface was created by dvbnet without any problem:

root@atom-test:~# dvbnet -l

DVB Network Interface Manager
Copyright (C) 2003, TV Files S.p.A

Query DVB network interfaces:
-----------------------------
Found device 0: interface dvb0_0, listening on PID 5050, encapsulation MPE
-----------------------------
Found 1 interface(s).

root@atom-test:~# uname -a
Linux atom-test 2.6.31-16-generic #53-Ubuntu SMP Tue Dec 8 04:01:29 UTC 2009 i686 GNU/Linux

I am using a Prof Red 7300 DVB-S2 card with the cx88xx module. I also tested with an older BT878 DVB-S card, with the same error.

Attached is an strace of the ifconfig dvb0_0 up command. I'm afraid I don't know enough about the kernel to make head or tail of it -- can anyone help out?

many thanks, Julian

---

### Post by juliansomers on 2010-02-25
I think this is solved:
 
Since 2.6.24 something seems to have changed to cause ip/ifconfig it to bail out if there is not a valid mac address set on the interface. Because I'm only interested in multicast, I've never bothered with a mac address on the dvb interface. Assigning a mac address solves the problem. ifconfig dvbn_n hw ether 11:22:33:44:55:66

many thanks, Julian

---

