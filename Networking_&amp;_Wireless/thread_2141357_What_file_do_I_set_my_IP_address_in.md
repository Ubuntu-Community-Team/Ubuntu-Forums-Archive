---
title: "What file do I set my IP address in ?"
date: 2013-05-02
forum: Networking &amp; Wireless
---

### Post by arealperson on 2013-05-02
When I type ifconfig I get the following...

eth3      Link encap:Ethernet  HWaddr 00:0c:29:a5:d2:40  
          inet addr:192.168.1.102  Bcast:192.168.255.255  Mask:255.255.0.0
          inet6 addr: fe80::20c:29ff:fea5:d240/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19222 errors:0 dropped:0 overruns:0 frame:0
          TX packets:573 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1702670 (1.7 MB)  TX bytes:46152 (46.1 KB)
          Interrupt:19 Base address:0x2024 

********************************************
This -> inet addr:192.168.1.102  must be set somewhere in a file, but where ?
I must change this "Mask:255.255.0.0" to be this "Mask:255.255.255.0", but where is the file ??

Thanks,

---

### Post by SeijiSensei on 2013-05-02
[https://help.ubuntu.com/12.04/serverguide/network-configuration.html](https://help.ubuntu.com/12.04/serverguide/network-configuration.html)

---

### Post by Cheesemill on 2013-05-02
Is this a desktop installation or a server installation?

If it's a desktop then just go to Settings > Network and make your changes there.

If it's a server then you need to edit the /etc/network/interfaces files.

---

