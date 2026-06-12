---
title: "Wireless BCM4306"
date: 2009-09-09
forum: Networking &amp; Wireless
---

### Post by cmcanulty on 2009-09-09
OK I have tried everything driver install troubleshoot, etc Here is the terminal outputs please help I have no idea what  all the output means.
cmcanulty@Gateway:~$ lspci -vnn | grep 14e4
03:07.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
	Subsystem: Broadcom Corporation Device [14e4:0449]
cmcanulty@Gateway:~$ 

and

cmcanulty@Gateway:~$ lsmod | grep b43
b43                   131484  0 
mac80211              217592  1 b43
led_class              12036  1 b43
input_polldev          11912  1 b43
ssb                    41220  1 b43
cmcanulty@Gateway:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:03:25:1b:f2:62  
          inet addr:192.168.2.5  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::203:25ff:fe1b:f262/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:1842 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1706 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1899345 (1.8 MB)  TX bytes:254487 (254.4 KB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:36 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2688 (2.6 KB)  TX bytes:2688 (2.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:14:a5:47:03:8a  
          inet addr:10.42.43.1  Bcast:10.42.43.255  Mask:255.255.255.0
          inet6 addr: fe80::214:a5ff:fe47:38a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:4985 (4.9 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-14-A5-47-03-8A-33-38-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

cmcanulty@Gateway:~$

---

### Post by chili555 on 2009-09-09
Your wireless appears to be working fine; however, I am wondering why your wired has a 192.168.x.x address and your wireless has picked up 10.42.x.x. It doesn't make sense; your router is clearly in the 192.168.x.x neighborhood. We know this because the ethernet cable is hard-wired to it. Is 10.42.x.x your neighbor's wireless router? I suggest you detach the ethernet cable, reboot and try the wireless again.

I suspect Network Manager is a big part of the problem.> 

---

### Post by cmcanulty on 2009-09-09
I tried that but no go.No close neighbors, any other ideas. It worked fine under windows until I switched to Ubuntu yesterday. I downloaded a .rar file driver from here
[http://www.wireless-driver.com/download/broadcom/Broadcom-4306-driver-download.htm](http://www.wireless-driver.com/download/broadcom/Broadcom-4306-driver-download.htm)
but it says no archive and so I can't uncompress it. I also have the Ubuntu driver downloaded.fwcutter is a tool which can extract firmware from various source files.It's written for BCM43xx driver files.

---

### Post by chili555 on 2009-09-10
Tell us a bit more about your situation. The internet comes to your home or business and connects to what? A DSL modem? Does it have a wireless component that is active? Does that perchance attach to a wireless router? In other words, do you have two DHCP servers active at the same time accounting for your two weird IP addresses? I feel that we must get that corrected first.

---

