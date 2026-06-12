---
title: "Wireless connects to internet, but not to lan!"
date: 2008-12-24
forum: Networking &amp; Wireless
---

### Post by ruipedroca on 2008-12-24
Hi,

My wireless connection connects to internet, but not to lan!
But, if I plug the wired connection, it connects perfectly.
I've ouble checked the configuration in the GUI and everything seems to be equal.
What should I do?..



$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.10.0    *               255.255.255.0   U     0      0        0 eth0
192.168.10.0    *               255.255.255.0   U     0      0        0 wlan0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.10.1    0.0.0.0         UG    100    0        0 wlan0
default         192.168.10.1    0.0.0.0         UG    100    0        0 eth0
acerrp@acerrp:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:d4:4c:c6:17
          inet addr:192.168.10.101  Bcast:192.168.10.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Base address:0xa000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:86 errors:0 dropped:0 overruns:0 frame:0
          TX packets:86 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:7354 (7.1 KB)  TX bytes:7354 (7.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:16:cf:60:eb:3d
          inet addr:192.168.10.101  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fe80::216:cfff:fe60:eb3d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:115 errors:0 dropped:0 overruns:0 frame:0
          TX packets:145 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:74946 (73.1 KB)  TX bytes:30537 (29.8 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-16-CF-60-EB-3D-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

acerrp@acerrp:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"rp3"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:15:E9:24:E0:9A
          Bit Rate=1 Mb/s   Tx-Power=27 dBm
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B
          Link Quality=63/100  Signal level=-49 dBm  Noise level=-71 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

acerrp@acerrp:~$ 



Thanks in advance,

---

### Post by superprash2003 on 2008-12-24
eth0 and wlan0 have same ip.. thats not good..use different ips..


merry christmas..

---

### Post by ruipedroca on 2008-12-25
> **superprash2003 said:**
> eth0 and wlan0 have same ip.. thats not good..use different ips.. 

Didn't work.. Any ideas?

Regards

---

### Post by ruipedroca on 2008-12-25
Well, I've just found out the solution and it's pretty weird...:

I went to check my wife's laptop and checked the Network Settings GUI; and found out that the only difference was that the eth0 check box "Activate when the computer starts" was empty (disabled) while in my laptop it was enabled. 

So, I've just disabled it, saved, restarted the computer and it worked! 

Don't ask me why it worked, because I don't know! :)

---

