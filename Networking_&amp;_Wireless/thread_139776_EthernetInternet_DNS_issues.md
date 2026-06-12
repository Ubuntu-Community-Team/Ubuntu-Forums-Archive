---
title: "Ethernet/Internet DNS issues"
date: 2006-03-04
forum: Networking &amp; Wireless
---

### Post by b_del_priore on 2006-03-04
I can't access certain sites/ip addresses

I have a DSL connection routed through an Intel pci 10/100 eternet card. I can only access about 1/3 of the sites I normally use.  I get connection timed out messages in firefox, and can only ping some servers through a terminal.  

It seems like any time I try to download additional software components/packages through the package manager, it only rarely works. 

Any tips/info appreciated.

Brandon

brandon@speedo:~$ lspci | grep Eth
0000:00:10.0 Ethernet controller: Intel Corp. 82557/8/9 [Ethernet Pro 100] (rev 0c)
brandon@speedo:~$

brandon@speedo:~$ lsmod | grep mii
mii                     5248  1 e100
brandon@speedo:~$


brandon@speedo:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
brandon@speedo:~$


brandon@speedo:~$ cat /etc/resolv.conf
search domain.actdsltmp
nameserver 192.168.0.1
nameserver 205.171.3.65
brandon@speedo:~$

brandon@speedo:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:02:B3:61:39:06
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::202:b3ff:fe61:3906/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7380 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6678 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:8152941 (7.7 MiB)  TX bytes:737729 (720.4 KiB)

brandon@speedo:~$

---

### Post by Monkeh on 2006-03-04
This is a pretty random guess, but do you use a D-Link router? I find their DNS server simply doesn't work with 2.6 kernels.

---

### Post by b_del_priore on 2006-03-04
ActionTEC DSL Modem With Wireless gateway (works great in Win98)

---

### Post by woedend on 2006-03-05
see if its a dns error by either testing ip addresses or changing the dns.

---

### Post by mips on 2006-03-05
Look at post #34 here [http://www.ubuntuforums.org/showthread.php?t=95350](http://www.ubuntuforums.org/showthread.php?t=95350)

Specifically the link to the linuxquestions website.

Look at post #4 here [http://www.ubuntuforums.org/showthread.php?t=78337](http://www.ubuntuforums.org/showthread.php?t=78337)

Specifically Option 1 & 3

[http://www.ubuntuforums.org/showthread.php?t=126764](http://www.ubuntuforums.org/showthread.php?t=126764)

---

