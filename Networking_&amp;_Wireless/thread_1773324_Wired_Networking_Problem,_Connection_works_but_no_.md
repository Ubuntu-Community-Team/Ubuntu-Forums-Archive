---
title: "Wired Networking Problem, Connection works but no Internet"
date: 2011-06-01
forum: Networking &amp; Wireless
---

### Post by Peckles on 2011-06-01
Hey guys,

I just installed Ubuntu 11.04 desktop on my desktop in dual boot with Windows 7.  I consider myself a savvy computer user but have only a basic understanding on linux as I am new to it. 

Heres my problem, I am unable to connect to the Internet even though my wired Ethernet connection says it is connected normally.  The wierd thing about this is that I also have a wireless card in my desktop and when I connect through that I am able to connect to the Internet.  I am connecting to a router that is functioning as a repeater to my main router/cable modem.  I have tried to solve this myself but am having no luck.  Ironically, earlier today suddenly my ethernet connection worked for a few minutes without me modifying anything. 

Any help in this matter would be greatly appreciated.

The output of some terminal commands are below.

> ifconfig
eth0      Link encap:Ethernet  HWaddr 6c:f0:49:75:2f:f1  
          inet addr:192.168.0.104  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::6ef0:49ff:fe75:2ff1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:29897 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19644 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:38872917 (38.8 MB)  TX bytes:1802949 (1.8 MB)
          Interrupt:45 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:42 errors:0 dropped:0 overruns:0 frame:0
          TX packets:42 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2952 (2.9 KB)  TX bytes:2952 (2.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1e:e5:fb:5c:e3  
          inet addr:192.168.0.105  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:e5ff:fefb:5ce3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:90 errors:0 dropped:0 overruns:0 frame:0
          TX packets:79 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13867 (13.8 KB)  TX bytes:16382 (16.3 KB)
> iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"DH-9752R"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:02:6F:A1:53:6C   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-38 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1   Missed beacon:0
> telnet 192.168.0.1
Trying 192.168.0.1...
telnet: Unable to connect to remote host: Connection refused
however a pint to that ip address (my router) is successful.

> netstat -lr
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.0.0     *               255.255.255.0   U         0 0          0 eth0
192.168.0.0     *               255.255.255.0   U         0 0          0 wlan0
link-local      *               255.255.0.0     U         0 0          0 eth0
default         192.168.0.1     0.0.0.0         UG        0 0          0 eth0hosts.allow and hosts.deny are both fine (not blank but no entries)

Feel free to ask for anymore information.

---

### Post by dandnsmith on 2011-06-02
I'm really suspicious of those entries in the netstat listing which are identical except for the interface.
If you've traceroute loaded you could try to see what it will show (ping is sometimes useful too).

---

