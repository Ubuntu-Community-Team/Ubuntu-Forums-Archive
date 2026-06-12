---
title: "XP can ping FreeNAS hostname, Ubuntu can't"
date: 2010-07-09
forum: Networking &amp; Wireless
---

### Post by nrogers64 on 2010-07-09
At work, I recently installed FreeNAS 0.7.4919 on a computer and set it up to be a samba server. Using a Windows XP Pro SP3 computer on the same subnet as the FreeNAS server, I can ping the FreeNAS server's hostname and it works just fine. However, using an Ubuntu 10.04 computer on the same subnet as the FreeNAS server, I am unable to ping the FreeNAS server's hostname. When I try, it says "ping: unknown host [the FreeNAS server's hostname]". I can ping its IP address just fine, though. Why is it that Windows XP Pro can ping the FreeNAS server's hostname but Ubuntu 10.04 can't?

Here's the output of the ifconfig command on the Ubuntu 10.04 computer:

```
    eth0      Link encap:Ethernet  HWaddr 00:14:c2:cd:a6:39 
              inet addr:10.37.74.141  Bcast:10.37.75.255  Mask:255.255.252.0
              inet6 addr: fe80::214:c2ff:fecd:a639/64 Scope:Link
              UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
              RX packets:3920 errors:0 dropped:0 overruns:0 frame:0
              TX packets:109 errors:0 dropped:0 overruns:0 carrier:0
              collisions:0 txqueuelen:1000
              RX bytes:404380 (404.3 KB)  TX bytes:21103 (21.1 KB)
              Interrupt:17

    lo        Link encap:Local Loopback 
              inet addr:127.0.0.1  Mask:255.0.0.0
              inet6 addr: ::1/128 Scope:Host
              UP LOOPBACK RUNNING  MTU:16436  Metric:1
              RX packets:8 errors:0 dropped:0 overruns:0 frame:0
              TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
              collisions:0 txqueuelen:0
              RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)
```

And here's the output of the ifconfig command on the FreeNAS server:

```
    fxp0: flags=8843<UP,BROADCAST,RUNNING,SIMPLEX,MULTICAST>  metric 0 mtu 1500
       options=8<VLAN_MTU>
       ether 00:11:11:be:88:14
       inet 10.37.72.53 netmask 0xfffffc00 broadcast 10.37.75.255
       media: Ethernet autoselect (100baseTX <full-duplex>)
       status: active
    lo0: flags=8049<UP,LOOPBACK,RUNNING,MULTICAST> metric 0 mtu 16384
       inet6 fe80::1%lo0 prefixlen 64 scopeid 0x2
       inet6 ::1 prefixlen 128
       inet 127.0.0.1 netmask 0xff000000 
```

Any help would be greatly appreciated. Thanks!

---

### Post by denver on 2010-07-09
If i am not mistaken, you can ping the NAS from your XP machine because it does a NetBios lookup and finds the IP. There is a post by javiwwweb that explains how to do this in ubuntu:

[http://ubuntuforums.org/showthread.php?t=88206](http://ubuntuforums.org/showthread.php?t=88206)

Good luck!

---

