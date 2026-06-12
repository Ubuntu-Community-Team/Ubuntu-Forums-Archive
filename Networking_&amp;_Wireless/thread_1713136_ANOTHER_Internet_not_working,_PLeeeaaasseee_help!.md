---
title: "ANOTHER Internet not working, PLeeeaaasseee help!"
date: 2011-03-23
forum: Networking &amp; Wireless
---

### Post by wolfy1988 on 2011-03-23
Hi all

I am new to ubuntu

Internet stopped working, I am using netbook version on my VAIO VPCM11M1E,

Right then I have try'd the whole up down thing and nothing.

This is what I have thus far:



wolfe@ubuntu:~$ rfkill
Usage:	rfkill [options] command
Options:
	--version	show version (0.4)
Commands:
	help
	event
	list [IDENTIFIER]
	block IDENTIFIER
	unblock IDENTIFIER
where IDENTIFIER is the index no. of an rfkill switch or one of:
	<idx> all wifi wlan bluetooth uwb ultrawideband wimax wwan gps fm
wolfe@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Frequency:2.472 GHz  Access Point: Not-Associated   
          Tx-Power=17 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
wolfe@ubuntu:~$ sudo ifconfig wlan0 up
[sudo] password for wolfe:
wolfe@ubuntu:~$
wolfe@ubuntu:~$ sudo ifconfig wlan0 up
wolfe@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:24:be:ba:1c:40  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:44

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:484 errors:0 dropped:0 overruns:0 frame:0
          TX packets:484 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:36792 (36.7 KB)  TX bytes:36792 (36.7 KB)

wlan0     Link encap:Ethernet  HWaddr 0c:ee:e6:fe:b1:3a  
          inet6 addr: fe80::eee:e6ff:fefe:b13a/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:5479 (5.4 KB)

wolfe@ubuntu:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

wolfe@ubuntu:~$ sudo getit /var/lib/NetworkManager/NetworkManager.state
sudo: getit: command not found
wolfe@ubuntu:~$ sudo ifconfig eth0 down
wolfe@ubuntu:~$ sudo ifconfig eth0 up
wolfe@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:24:be:ba:1c:40  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:44

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:532 errors:0 dropped:0 overruns:0 frame:0
          TX packets:532 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:40440 (40.4 KB)  TX bytes:40440 (40.4 KB)

wlan0     Link encap:Ethernet  HWaddr 0c:ee:e6:fe:b1:3a  
          inet6 addr: fe80::eee:e6ff:fefe:b13a/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:5479 (5.4 KB)

wolfe@ubuntu:~$

---

