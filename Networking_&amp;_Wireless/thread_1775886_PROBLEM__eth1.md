---
title: "PROBLEM : eth1"
date: 2011-06-05
forum: Networking &amp; Wireless
---

### Post by evarie on 2011-06-05
This is my output after login on my server. You can see double/twice "Welcome to Ubuntu !" The second welcome is the big problem.

This is my output code:

```

Linux 2.6.32-32-generic-pae #62-Ubuntu SMP Wed Apr 20 22:10:33 UTC 2011 i686 GNU/Linux
Ubuntu 10.04.2 LTS

Welcome to Ubuntu!
 * Documentation:  https://help.ubuntu.com/

  System information as of Sun Jun  5 16:46:11 CEST 2011

  System load:  0.47              Processes:           87
  Usage of /:   84.0% of 3.54GB   Users logged in:     1
  Memory usage: 26%               IP address for eth1: 192.168.1.5
  Swap usage:   0%

  Graph this data and manage this system at https://landscape.canonical.com/

Ubuntu 10.04.2 LTS

Welcome to Ubuntu!
 * Documentation:  https://help.ubuntu.com/

  System information as of Wed Apr 27 17:36:09 CEST 2011

  System load:  0.58              Processes:           70
  Usage of /:   84.4% of 3.54GB   Users logged in:     0
  Memory usage: 23%               IP address for eth1: 192.168.1.104
  Swap usage:   0%

  Graph this data and manage this system at https://landscape.canonical.com/

```

When I want a ssh-connection. I must use the first ip-address 192.168.1.5 and this works correct.
But; I can not connect with ssh to ip 192.168.1.104 caus this is fake and a error too.


This is my output of my ifconfig command:
```

root@server:~# ifconfig
eth1      Link encap:Ethernet  HWaddr 00:50:fc:b8:5e:29  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::250:fcff:feb8:5e29/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1129 errors:0 dropped:0 overruns:0 frame:0
          TX packets:91 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:73469 (73.4 KB)  TX bytes:11797 (11.7 KB)
          Interrupt:11 Base address:0x1000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```

It is strange that there is no ip-address 192.168.1.104

---

