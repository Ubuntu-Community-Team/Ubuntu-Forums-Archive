---
title: "Ugh.. D-Link DWL-2000AP+ Access Point setup help"
date: 2009-11-09
forum: Networking &amp; Wireless
---

### Post by humphreybc on 2009-11-09
Hi there,

So we've been trying to get this stupid access point to work all day... it's been sitting on WEP for the last couple of years working pretty well, but the time came to change it to WPA and since we're changing the SSID and password for our other wireless access point, figured we'd bring this one into line as well. I have forgotten the login password we set years ago, so I just did a hard reset. 

Now we had it plugged into a laptop via ethernet and were trying to access the setup page but it wasn't letting us connect for ages. Eventually we managed to connect, and upgraded the firmware to a newer version that adds WPA capability.

Now, I cannot connect to the access point again. Here's some terminal output:

```

benjamin@benjamin-laptop:~$ sudo ifconfig eth0 192.168.0.50
[sudo] password for benjamin: 
benjamin@benjamin-laptop:~$ ping 192.168.0.50
PING 192.168.0.50 (192.168.0.50) 56(84) bytes of data.
64 bytes from 192.168.0.50: icmp_seq=1 ttl=64 time=0.051 ms
64 bytes from 192.168.0.50: icmp_seq=2 ttl=64 time=0.042 ms
64 bytes from 192.168.0.50: icmp_seq=3 ttl=64 time=0.042 ms
64 bytes from 192.168.0.50: icmp_seq=4 ttl=64 time=0.046 ms
64 bytes from 192.168.0.50: icmp_seq=5 ttl=64 time=0.042 ms
64 bytes from 192.168.0.50: icmp_seq=6 ttl=64 time=0.043 ms
64 bytes from 192.168.0.50: icmp_seq=7 ttl=64 time=0.042 ms
^C
--- 192.168.0.50 ping statistics ---
7 packets transmitted, 7 received, 0% packet loss, time 5994ms
rtt min/avg/max/mdev = 0.042/0.044/0.051/0.003 ms
benjamin@benjamin-laptop:~$ sudo telnet 192.168.0.50 80
Trying 192.168.0.50...
telnet: Unable to connect to remote host: Connection refused

```

So, as you can see, it's refusing connections now.... I'm stuck, any advice? I've tried to hard reset it again, powered it off and on, disabled my wireless and any other interfering devices... you name it.

Thanks

---

