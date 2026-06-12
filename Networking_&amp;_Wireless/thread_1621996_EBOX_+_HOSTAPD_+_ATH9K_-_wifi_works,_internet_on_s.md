---
title: "EBOX + HOSTAPD + ATH9K - wifi works, internet on server no internet on clients"
date: 2010-11-14
forum: Networking &amp; Wireless
---

### Post by bitscarre on 2010-11-14
Hello fellow Ubuntu users,

I have been trying for a few weeks now to setup my own home wireless server and router at home to no avail. I have tried ipcop, smoothwall, ubuntu 10.10 desktop edition, couldn't get any of them to work. Tried to run the mentioned ipcop and smoothwall both as standalone hardware installation as well as on a virtual machine, running either on vmware server of virtualbox. 

Each time I got to a point where I can get internet on the server, the wireless access point was working, I can connect to it, but cannot get internet on the client connecting to the server. From the wifi client I can ping the internal ip address of the wifi access point, but not the external one.

Network setup:

ADSL -> Cisco Router --->>> cat5 -->>>Linux Box --> WPA Secured Wifi >))))) Home network.

Hardware:
Router:Wireless ADSL2+ GatewayWAG54G2 Firmware Version:V1.00.19 
Linux Box: 
Shuttle XS35 Barebone, added 2gb ram and 100gb hdd, changed wifi card with an atheros chipset one
(For those interested, it doesn't have a fan and the cpu temp averages at 55 at night with central heating on, and 52 during the day, while standing in clear space - in a typical London winter climate, room temp ~25 C. Power consumption averages at 17W.)

**IP ADDRESSING**

Cisco Router:
```
MAC Address:     00:21:29:73:CC:97
IP Address:     192.168.1.1
Subnet Mask:     255.255.255.0    
DHCP Server:     Enable
Starting IP Address:     192.168.1.100
End IP Address:     192.168.1.149
```Linux Box:
```
router@firewall:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 80:ee:73:06:03:ec  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::82ee:73ff:fe06:3ec/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16200 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10335 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1541970 (1.5 MB)  TX bytes:26507802 (26.5 MB)
          Interrupt:28 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:46785 errors:0 dropped:0 overruns:0 frame:0
          TX packets:46785 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7016522 (7.0 MB)  TX bytes:7016522 (7.0 MB)

mon.wlan0 Link encap:UNSPEC  HWaddr B4-82-FE-8C-AF-A9-30-30-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:143 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10368 (10.3 KB)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr b4:82:fe:8c:af:a9  
          inet addr:192.168.10.1  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fe80::b682:feff:fe8c:afa9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:40 errors:0 dropped:0 overruns:0 frame:0
          TX packets:45 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4639 (4.6 KB)  TX bytes:5711 (5.7 KB)

router@firewall:~$ 

```Linux box wireless status
```
router@firewall:/$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  Mode:Master  Frequency:2.437 GHz  Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
mon.wlan0  IEEE 802.11bgn  Mode:Monitor  Frequency:2.437 GHz  Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
router@firewall:/$ 

```**Linux Box Software:**
Operating System:
```
Linux firewall 2.6.32-25-generic #45-Ubuntu SMP Sat Oct 16 19:48:22 UTC 2010 i686 GNU/Linux

```Webmin:
```
System hostname     firewall
Operating system     Ubuntu Linux 10.04.1
Webmin version     1.520
Time on system     Sun Nov 14 22:15:42 2010
Kernel and CPU     Linux 2.6.32-25-generic on i686
Processor information     Intel(R) Atom(TM) CPU D510 @ 1.66GHz, 4 cores
System uptime     0 hours, 33 minutes
Running processes     158
CPU load averages     0.23 (1 min) 0.18 (5 mins) 0.16 (15 mins)
CPU usage     0% user, 0% kernel, 1% IO, 99% idle
Real memory     993.08 MB total, 317.31 MB used
    
Virtual memory     2.84 GB total, 0 bytes used
    
Local disk space     88.89 GB total, 6.22 GB used

```EBox(installed from apt):
```

Modules:sysinfo network firewall antivirus apache ca dhcp dns ebackup events global ids l7-protocols logs monitor ntp objects radius remoteservices services software trafficshaping users

```Linux Box Iptables:
```

router@firewall:/$ sudo iptables -nvL
Chain INPUT (policy ACCEPT 4209 packets, 407K bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 4065 packets, 935K bytes)
 pkts bytes target     prot opt in     out     source               destination         
router@firewall:/$ 
```Linux Box Routes:
```

router@firewall:/$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.10.0    0.0.0.0         255.255.255.0   U     0      0        0 wlan0
router@firewall:/$ 

```Have installed the ath9k driver from the linux wireless website, compiled it, I have also installed linux-backports-modules-wireless-lucid-generic, after following advice from a forum post.

My hostapd.conf file is:
```
router@firewall:/$ cat /etc/hostapd/hostapd.conf
interface=wlan0
driver=nl80211
ssid=NewWifi
channel=6
hw_mode=g
auth_algs=1
wpa=2
wpa_passphrase=ubuntu forums
wpa_key_mgmt=WPA-PSK
wpa_pairwise=TKIP CCMP
rsn_pairwise=CCMP
router@firewall:/$ 
```Here is some pinging I have done:

From the linux box:
```

router@firewall:/$ ping ubuntu.com -c 1
PING ubuntu.com (91.189.94.156) 56(84) bytes of data.
64 bytes from vostok.canonical.com (91.189.94.156): icmp_seq=1 ttl=52 time=37.0 ms

--- ubuntu.com ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 37.065/37.065/37.065/0.000 ms
router@firewall:/$ ping 192.168.1.1 -c 1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=0.560 ms

--- 192.168.1.1 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 0.560/0.560/0.560/0.000 ms
router@firewall:/$ ping 192.168.10.1 -c 1
PING 192.168.10.1 (192.168.10.1) 56(84) bytes of data.
64 bytes from 192.168.10.1: icmp_seq=1 ttl=64 time=0.120 ms

--- 192.168.10.1 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 0.120/0.120/0.120/0.000 ms
router@firewall:/$ 

```From client connected to the linux box through wifi:
```
tablet@tablet:~$ ping ubuntu.com -c 1
ping: unknown host ubuntu.com
tablet@tablet:~$ ping 192.168.10.1 -c 1
PING 192.168.10.1 (192.168.10.1) 56(84) bytes of data.
64 bytes from 192.168.10.1: icmp_req=1 ttl=64 time=19.1 ms

--- 192.168.10.1 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 19.177/19.177/19.177/0.000 ms
tablet@tablet:~$ ping 192.168.1.1 -c 1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.10.199 icmp_seq=1 Destination Host Unreachable

--- 192.168.1.1 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

tablet@tablet:~$ 

```The problem that I am having is that I cannot get the wifi clients connected to the linux box, to get on the internet. I suspect there is some sort of routing error that I am making somewhere in the process, since I always get to the same result, no matter what software I try. 

I also do not know what's with the mon.wlan0 interface. In ebox it gives me the option to configure it as a NIC. However, I have configured only wlan0 with the static ip address mentioned above, linked to to the DHCP server, so every client that connects can get the ip address automatically. If someone can explain the purpouse of that extra interface, please do, I am curious and I am sure there are others interested in knowing this as well.

The purpouse of all this is to have a better QoS manager on my home network, better filtering for web browsing and better logging. On the network there are 6 clients who the internet 24/5 and 4 who use it rarely(1hr/day).

I am determined to find the solution to this and write a new and complete guide on how to do this from A to Z.

My bet is that the routing is wrong, I have tried hard to find a solution to it, searched the forums a lot, used the example .sh scripts to do the job, nothing seems to work or probably I am doing something wrong.

Thank you very much for your time reading this post. All solutions are welcome.

---

### Post by bitscarre on 2010-11-15
No answers, I guess this really is a challenge then...

---

### Post by bitscarre on 2010-11-18
Last bump.

---

### Post by jhorck on 2010-12-05
Did you enable ip-forwarding? net.ipv4.ip_forward = 1 in /etc/sysctl.conf
Did you configure dns-forwarding? I use dnsmasq for this (lightweight dns forwarder and dhcp server)
You can ignore the interface mon.wlan0

---

### Post by bitscarre on 2010-12-05
Yeah, I have enabled ip forwarding and dns forwarding. I managed to get it to work now. It took me a while but I got it now.   Now I am trying to route the traffic through 2 virtual machines running on top of ubuntu. Don't ask why :D

---

### Post by czinehuba on 2011-01-09
have u tried without encrypsion?
just add macfiltering 

mine work only without wep or wpa encrypsion

config:
wireless card: tplink TL-WN951N ar5008 3tx3r
ubuntu x64 10.10 kernel  2.6.35-24-generic
mb   gigabyte g41mft-us2h
celeron dual core E3200
2gb ddr3 dual ch
1tb wd black
hostapd 0.7.3

my problem is wireless internet speed is slower then isp provides about 1/3, and lan to wireless copy is max 2MB/s.

---

