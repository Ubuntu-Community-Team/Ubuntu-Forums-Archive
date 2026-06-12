---
title: "Network: Incoming connections work, outgoing fails"
date: 2012-12-04
forum: Networking &amp; Wireless
---

### Post by anirvan.majumdar on 2012-12-04
i recently set up my own server at home to run Ubuntu 12.04 server ed. on booting up, i noticed that a message related to networking comes up, and the booting process pauses. the message read something like - *waiting for network configuration* and after a while - [I]waiting another 60 seconds...
[/I]
on booting up, I realised that any command which requires a network connection was not working - ping, apt-get install, etc.

on firing the **ifup eth0** command, I get the error **RTNETLINK answers: File exists. Failed to bring up eth0**. I also realised, while searching the web for this problem, that this is probably one of the most common networking related issues - however, most of the questions are around setting up multiple IPs for the same machine.

**ifdown eth0** also fails, stating that eth0 is not configured. 

my **/etc/network/interfaces** file has a simple configuration for a static IP:
    
    ```
auto lo
    iface lo inet loopback
    
    auto eth0
    iface eth0 inet static
    address xx.xx.xx.xx
    netmask xx.xx.xx.xx
    broadcast xx.xx.xx.xx
    gateway xx.xx.xx.xx
    dns-nameservers xx.xx.xx.xx
```

The ****strangest**** part of this problem is that, while I can't connect to anything outside, I can ping to this particular server using the static IP configured in the `interface` file, and, i can even SSH into it!

I'm really at ends here with this problem, and any guidance is much appreciated. 

Thanks!

---

