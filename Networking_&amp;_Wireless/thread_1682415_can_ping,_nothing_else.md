---
title: "can ping, nothing else"
date: 2011-02-05
forum: Networking &amp; Wireless
---

### Post by gletob on 2011-02-05
So I just set up an Ubuntu 10.04 server, in Virualbox (on a windows machine), and I've got networking set up, and I can ping my router, computers in the network, internet IP addresses, and even URLs like Google.com (The successfully resolve and ping). 

But if I try to use telnet, apt-get, or wget anything on the internet, it times out.

```
Linux eniac 2.6.32-24-server #39-Ubuntu SMP Wed Jul 28 06:21:40 UTC 2010 x86_64                                   GNU/Linux
Ubuntu 10.04.1 LTS

Welcome to the Ubuntu Server!
 * Documentation:  http://www.ubuntu.com/server/doc

  System information as of Sat Feb  5 21:17:54 EST 2011

  System load:  0.01              Processes:           88
  Usage of /:   1.2% of 77.35GB   Users logged in:     1
  Memory usage: 15%               IP address for lo:   127.0.0.1
  Swap usage:   0%                IP address for eth0: 192.168.1.112

  Graph this data and manage this system at https://landscape.canonical.com/

0 packages can be updated.
0 updates are security updates.

Last login: Sat Feb  5 17:20:31 2011
glenn@eniac:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 08:00:27:58:00:fd
          inet addr:192.168.1.112  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:27ff:fe58:fd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:11357 errors:0 dropped:0 overruns:0 frame:0
          TX packets:326 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:816839 (816.8 KB)  TX bytes:73510 (73.5 KB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1260 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1260 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:216193 (216.1 KB)  TX bytes:216193 (216.1 KB)

glenn@eniac:~$ ping ubuntu.com
PING ubuntu.com (91.189.94.156) 56(84) bytes of data.
64 bytes from vostok.canonical.com (91.189.94.156): icmp_seq=1 ttl=48 time=92.5 ms
64 bytes from vostok.canonical.com (91.189.94.156): icmp_seq=2 ttl=48 time=163 ms
64 bytes from vostok.canonical.com (91.189.94.156): icmp_seq=3 ttl=48 time=87.6 ms
64 bytes from vostok.canonical.com (91.189.94.156): icmp_seq=4 ttl=48 time=91.1 ms
^C
--- ubuntu.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3004ms
rtt min/avg/max/mdev = 87.627/108.606/163.141/31.537 ms
glenn@eniac:~$ Linux eniac 2.6.32-24-server #39-Ubuntu SMP Wed Jul 28 06:21:40 UTC 2010 x86_64                                   GNU/Linux
Ubuntu 10.04.1 LTS

Welcome to the Ubuntu Server!
 * Documentation:  http://www.ubuntu.com/server/doc

  System information as of Sat Feb  5 21:17:54 EST 2011

  System load:  0.01              Processes:           88
  Usage of /:   1.2% of 77.35GB   Users logged in:     1
  Memory usage: 15%               IP address for lo:   127.0.0.1
  Swap usage:   0%                IP address for eth0: 192.168.1.112

  Graph this data and manage this system at https://landscape.canonical.com/

0 packages can be updated.
0 updates are security updates.

Last login: Sat Feb  5 17:20:31 2011
glenn@eniac:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 08:00:27:58:00:fd
          inet addr:192.168.1.112  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:27ff:fe58:fd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:11357 errors:0 dropped:0 overruns:0 frame:0
          TX packets:326 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:816839 (816.8 KB)  TX bytes:73510 (73.5 KB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1260 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1260 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:216193 (216.1 KB)  TX bytes:216193 (216.1 KB)

glenn@eniac:~$ ping ubuntu.com
PING ubuntu.com (91.189.94.156) 56(84) bytes of data.
64 bytes from vostok.canonical.com (91.189.94.156): icmp_seq=1 ttl=48 time=92.5 ms
64 bytes from vostok.canonical.com (91.189.94.156): icmp_seq=2 ttl=48 time=163 ms
64 bytes from vostok.canonical.com (91.189.94.156): icmp_seq=3 ttl=48 time=87.6 ms
64 bytes from vostok.canonical.com (91.189.94.156): icmp_seq=4 ttl=48 time=91.1 ms
^C
--- ubuntu.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3004ms
rtt min/avg/max/mdev = 87.627/108.606/163.141/31.537 ms

glenn@eniac:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 eth0
glenn@eniac:~$



```

---

