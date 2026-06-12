---
title: "Wired internet not recognized on fresh installation, Ubuntu 10.04"
date: 2012-04-19
forum: Networking &amp; Wireless
---

### Post by loai.ghoraba on 2012-04-19
Hi all

I have installed Ubuntu 10.04, and I have the problem that wired internet connection is not recognized at all, however the wireless is working (I installed it package through USB modem). ifconfig yields the following:



ifconfig 
eth0      Link encap:Ethernet  HWaddr e8:39:df:95:99:df  
          inet6 addr: fe80::ea39:dfff:fe95:99df/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:39 errors:0 dropped:0 overruns:0 frame:2600
          TX packets:14 errors:6 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10388 (10.3 KB)  TX bytes:4900 (4.9 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1100 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1100 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:84520 (84.5 KB)  TX bytes:84520 (84.5 KB)

I have searched a lot of forums but in vain, most ppl answered with such an answer

[http://ubuntuforums.org/showthread.php?t=1857808&page=7](http://ubuntuforums.org/showthread.php?t=1857808&page=7)

but also didn't do any good.
My Ethernet controller is Atheros Communications AR8152 v1.1 Fast Ethernet

Any help ?

---

### Post by sanderj on 2012-04-19
First checks:

[LIST]
[*]is an ethernet cable connected on both sides?
[*]is DHCP configured on both sides?
[*]what is the output of "cat /var/log/dmesg | grep -i eth0"
[/LIST]

Here's my output without an ethernet cable connected:

```

sander@R540:~$ cat /var/log/dmesg | grep -i eth0
[    1.022467] sky2 0000:06:00.0: eth0: addr 00:24:54:e8:54:31
[   29.216478] sky2 0000:06:00.0: eth0: enabling interface
[   29.217407] ADDRCONF(NETDEV_UP): eth0: link is not ready
sander@R540:~$ 


```

---

