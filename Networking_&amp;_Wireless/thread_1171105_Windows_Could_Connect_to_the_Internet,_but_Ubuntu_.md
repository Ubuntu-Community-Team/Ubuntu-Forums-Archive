---
title: "Windows Could Connect to the Internet, but Ubuntu Failed"
date: 2009-05-27
forum: Networking &amp; Wireless
---

### Post by Taiwan on 2009-05-27
I have installed both Windows and ubuntu on my PC. Windows could successfully connect to the Internet, but ubuntu failed. In ubuntu, I typed "ipconfig -a" and the result is as followed:

eth0      Link encap:Ethernet  HWaddr 00:0d:61:72:cc:c5  
          inet addr:192.168.0.176  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:61ff:fe72:ccc5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15 errors:0 dropped:0 overruns:0 frame:0
          TX packets:49 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2236 (2.1 KB)  TX bytes:5931 (5.7 KB)
          Interrupt:20 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1283 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1283 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:64188 (62.6 KB)  TX bytes:64188 (62.6 KB)

I am a beginner in ubuntu and don't know how to solve this problem. Could anyone give me advise? By the way, my PC is using the switch with DHCP connecting to the network.

Thanks in advance.

---

### Post by madverb on 2009-05-27
Paste output of
```
cat /etc/resolv.conf
ping google.com
ping 67.19.113.186
```

---

### Post by Taiwan on 2009-05-27
Hi, here's the outputs:

cat /etc/resolv.conf
[INDENT]### BEGIN INFO
#
# Modified_by:  NetworkManager
# Process:      /usr/bin/NetworkManager
# Process_id:   4854
#
### END INFO



nameserver 115.43.192.35
nameserver 203.133.10.67[/INDENT]

ping google.com
[INDENT]PING google.com (74.125.45.100) 56(84) bytes of data.
64 bytes from yx-in-f100.google.com (74.125.45.100): icmp_seq=1 ttl=238 time=206 ms
64 bytes from yx-in-f100.google.com (74.125.45.100): icmp_seq=2 ttl=236 time=204 ms
64 bytes from yx-in-f100.google.com (74.125.45.100): icmp_seq=3 ttl=236 time=204 ms
[/INDENT]

ping 67.19.113.186
[INDENT]PING 67.19.113.186 (67.19.113.186) 56(84) bytes of data.
64 bytes from 67.19.113.186: icmp_seq=1 ttl=41 time=187 ms
64 bytes from 67.19.113.186: icmp_seq=2 ttl=41 time=194 ms
64 bytes from 67.19.113.186: icmp_seq=3 ttl=41 time=188 ms[/INDENT]

Thank you for help!

---

### Post by Kevbert on 2009-05-27
Please supply the output of 
```
lspci | grep Network
```
Please note network must be a capital N.

---

### Post by madverb on 2009-05-27
What do you mean when you say Failed to connect to the Internet? It all seems to be working fine.

---

### Post by Taiwan on 2009-05-27
Hi, 
to Kevbert: I typed "lspci | grep Network" but there was no output on the screen.

to madverb: What I mean is that when I open Firefox and connect to websites such as yahoo or google, then Firefox told me "Address Not Found." However, in Windows system, I could browse those websites successfully.

---

### Post by Iowan on 2009-05-27
Is Windows using the same nameservers (DNS servers)? The pings seem to be successful... 
Firewall settings???

---

### Post by Taiwan on 2009-05-27
I found something very weird.

First, I went to Windows and disabled the network connection. Then, I returned to ubuntu, disable the network connection, and then enabled it. Finally, I opened Firfox and could successfully see the Yahoo or Google page.

But weird things happened! After a short time (about 1 second), Firefox failed to display web pages once again.

I repeated every step I said above, but the same problem occurred again. 

Could anyone give me any advise?

To Iowan: I don't know how to check whether Windows uses the same DNS server. Would you teach me? And I don't have the firewall in ubuntu.

---

### Post by superprash2003 on 2009-05-28
you could try using opendns servers - 208.67.222.222 and 208.67.220.220

---

