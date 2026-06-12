---
title: "How do I undo this code that messed up my Internet stability?"
date: 2011-01-02
forum: Networking &amp; Wireless
---

### Post by Irishpolyglot on 2011-01-02
I was trying to access Internet on a wired ASDL connection on a school network that simply wasn't working and someone with way more experience hacking Linux than I could dream of typed something for me and got it to work. But since then my Internet is unstable on all other connections! For example, my current wifi at a hotel keeps disconnecting the log-in, and that isn't happening on my cellphone's wifi.

This is the code he wrote, copied directly from the terminal:

```
benny@benny-laptop:~$ sudo -s 
[sudo] password for benny: 
root@benny-laptop:~# ifconfig eth0 192.168.1.111 
root@benny-laptop:~# route add default gw 192.168.1.101 
root@benny-laptop:~# ping 141.1.1.1 
PING 141.1.1.1 (141.1.1.1) 56(84) bytes of data. 
^C 
--- 141.1.1.1 ping statistics --- 
4 packets transmitted, 0 received, 100% packet loss, time 2999ms 

root@benny-laptop:~# ifconfig eth0 192.168.1.109 
root@benny-laptop:~# ping 141.1.1.1 
PING 141.1.1.1 (141.1.1.1) 56(84) bytes of data. 
^C 
--- 141.1.1.1 ping statistics --- 
4 packets transmitted, 0 received, 100% packet loss, time 2998ms 

root@benny-laptop:~# ifconfig eth0 
eth0      Link encap:Ethernet  HWaddr 00:21:9b:ec:94:0d  
          inet addr:10.1.1.1  Bcast:10.1.1.255  Mask:255.255.255.0 
          inet6 addr: fe80::221:9bff:feec:940d/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:15 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:2063 (2.0 KB)  TX bytes:2580 (2.5 KB) 
          Interrupt:17 

root@benny-laptop:~# ifconfig eth0 down 
root@benny-laptop:~# ifconfig eth0 hw ether 00:24:8C:EA:9A:18 
root@benny-laptop:~# ping 141.1.1.1 
PING 141.1.1.1 (141.1.1.1) 56(84) bytes of data. 
^C 
--- 141.1.1.1 ping statistics --- 
2 packets transmitted, 0 received, 100% packet loss, time 1004ms 

root@benny-laptop:~# route -n 
Kernel IP routing table 
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface 
192.168.2.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0 
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0 
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 wlan0 
root@benny-laptop:~# route del default 
root@benny-laptop:~# route add default gw 192.168.1.101 
SIOCADDRT: No such process 
root@benny-laptop:~# ifconfig 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:26041 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:26041 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:2044343 (2.0 MB)  TX bytes:2044343 (2.0 MB) 

wlan0     Link encap:Ethernet  HWaddr 00:21:5c:a1:07:0d  
          inet addr:192.168.2.110  Bcast:192.168.2.255  Mask:255.255.255.0 
          inet6 addr: fe80::221:5cff:fea1:70d/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:49174 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:59155 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:26790479 (26.7 MB)  TX bytes:15921585 (15.9 MB) 

root@benny-laptop:~# ifconfig eth0 192.168.1.111 
root@benny-laptop:~# route add default gw 192.168.1.101 
SIOCADDRT: No such process 
root@benny-laptop:~# ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:24:8c:ea:9a:18  
          inet addr:10.1.1.1  Bcast:10.1.1.255  Mask:255.255.255.0 
          inet6 addr: fe80::224:8cff:feea:9a18/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:128 (128.0 B)  TX bytes:250 (250.0 B) 
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:26041 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:26041 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:2044343 (2.0 MB)  TX bytes:2044343 (2.0 MB) 

wlan0     Link encap:Ethernet  HWaddr 00:21:5c:a1:07:0d  
          inet addr:192.168.2.110  Bcast:192.168.2.255  Mask:255.255.255.0 
          inet6 addr: fe80::221:5cff:fea1:70d/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:49268 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:59172 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:26797439 (26.7 MB)  TX bytes:15923249 (15.9 MB) 

root@benny-laptop:~# 
root@benny-laptop:~# 
root@benny-laptop:~# 
root@benny-laptop:~# ifconfig eth0 192.168.1.111 
root@benny-laptop:~# route add default gw 192.168.1.101 
root@benny-laptop:~# ping 141.1.1.1 
PING 141.1.1.1 (141.1.1.1) 56(84) bytes of data. 
64 bytes from 141.1.1.1: icmp_seq=1 ttl=58 time=82.1 ms 
64 bytes from 141.1.1.1: icmp_seq=2 ttl=58 time=78.6 ms 
64 bytes from 141.1.1.1: icmp_seq=3 ttl=58 time=80.3 ms 
^C 
--- 141.1.1.1 ping statistics --- 
3 packets transmitted, 3 received, 0% packet loss, time 2003ms 
rtt min/avg/max/mdev = 78.696/80.396/82.150/1.429 ms 
root@benny-laptop:~# ifconfig eth0 hw ether 00:24:8C:EA:9A:10 
root@benny-laptop:~# ping 141.1.1.1 
PING 141.1.1.1 (141.1.1.1) 56(84) bytes of data. 
64 bytes from 141.1.1.1: icmp_seq=1 ttl=58 time=82.4 ms 
64 bytes from 141.1.1.1: icmp_seq=2 ttl=58 time=71.8 ms 
^C 
--- 141.1.1.1 ping statistics --- 
2 packets transmitted, 2 received, 0% packet loss, time 1001ms 
rtt min/avg/max/mdev = 71.894/77.165/82.437/5.278 ms 
root@benny-laptop:~# vim /etc/resolv.conf 
The program 'vim' can be found in the following packages: 
 * vim 
 * vim-gnome 
 * vim-tiny 
 * vim-gtk 
 * vim-nox 
Try: apt-get install <selected package> 
root@benny-laptop:~# ae /etc/resolv.conf 
ae: command not found 
root@benny-laptop:~# ke /etc/resolv.conf 
keditfiletype         kerneloops            keytool 
keepassx              kerneloops-submit     
kernel-helper         kernel-packageconfig  
root@benny-laptop:~# ^Cetc/resolv.conf 
root@benny-laptop:~# cat /etc/resolv.conf 
# Generated by NetworkManager 
nameserver 192.168.2.1 
root@benny-laptop:~# echo nameserver 141.1.1.1 > /etc/resolv.conf 
root@benny-laptop:~# 
```

I'm afraid I don't understand what he did at all! But can you tell me how to undo it? :)

Thanks!

---

