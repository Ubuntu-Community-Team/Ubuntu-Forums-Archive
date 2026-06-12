---
title: "Wireless 3945 on Dell Inspiron 1720 just won't work"
date: 2008-12-14
forum: Networking &amp; Wireless
---

### Post by nafihsus on 2008-12-14
:frown:  
Hi, I tried to get wireless running with the help of countless posts I found - so far all failed. I see the router, get an IP but the connection just won't work. Hope someone can help. Below the info collected following the sticky post for wireless help:

Dell Inspiron 1720, Intel 3945ABG, Ubuntu 8.04.1
Kernel: 2.6.24-22-generic i686


0c:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG Network Connection [8086:4222] (rev 02)

cenk@cenk1:~$ iwconfig wlan0
wlan0     IEEE 802.11abg  ESSID:"eldewlan"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:17:3F:41:34:9A
          Bit Rate=54 Mb/s   Tx-Power=15 dBm
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B
          Link Quality=96/100  Signal level:-30 dBm  Noise level=-55 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

cenk@cenk1:~$ lsmod | grep 3945
iwl3945                96244  0
lbm_iwl_mac80211      242420  1 iwl3945
rfkill                  8596  2 iwl3945
led_class               6020  1 iwl3945
lbm_iwl_cfg80211       33248  2 iwl3945,lbm_iwl_mac80211

dmesg:
[  393.225010] wlan0: RX authentication from 00:17:3f:41:34:9a (alg=0 transaction=2 status=0)
[  393.225021] wlan0: authenticated
[  393.225026] wlan0: associate with AP 00:17:3f:41:34:9a
[  393.228492] wlan0: RX ReassocResp from 00:17:3f:41:34:9a (capab=0x421 status=0 aid=1)
[  393.228500] wlan0: associated
[  393.228510] wlan0: WMM queue=2 aci=0 acm=0 aifs=3 cWmin=15 cWmax=1023 txop=0
[  393.233307] wlan0: WMM queue=3 aci=1 acm=0 aifs=7 cWmin=15 cWmax=1023 txop=0
[  393.233604] wlan0: WMM queue=1 aci=2 acm=0 aifs=2 cWmin=7 cWmax=15 txop=94
[  393.233968] wlan0: WMM queue=0 aci=3 acm=0 aifs=2 cWmin=3 cWmax=7 txop=47
[  393.234135] wlan0 (WE) : Wireless Event too big (366)
[  400.114789] wlan0: no IPv6 routers present
[  411.705960] b44: eth0: Link is up at 100 Mbps, full duplex.
[  411.705964] b44: eth0: Flow control is off for TX and off for RX.

cenk@cenk1:~$ sudo lshw -C network
[sudo] password for cenk:
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1f:3c:1a:36:30
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=192.168.2.7 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:09:ce:e8:bd
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.2.99 latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s

cenk@cenk1:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:17:3F:41:34:9A
                    ESSID:"eldewlan"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=98/100  Signal level:-27 dBm  Noise level=-55 dBm
                    Encryption key:off
                    IE: Unknown: 2D1A4C1003FFFF000000000000000000000000000000000000000000
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000000069ea1252
                    Extra:Last beacon:40ms ago

cenk@cenk1:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                             RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.wlan0.pid with pid 13551
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:1f:3c:1a:36:30
Sending on   LPF/wlan0/00:1f:3c:1a:36:30
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.2.1 port 67
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:1f:3c:1a:36:30
Sending on   LPF/wlan0/00:1f:3c:1a:36:30
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPOFFER of 192.168.2.7 from 192.168.2.1
DHCPREQUEST of 192.168.2.7 on wlan0 to 255.255.255.255 port 67
DHCPACK of 192.168.2.7 from 192.168.2.1
bound to 192.168.2.7 -- renewal in 150598482 seconds.

---

### Post by superprash2003 on 2008-12-14
please post ifconfig output

---

### Post by nafihsus on 2008-12-14
cenk@cenk1:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:09:ce:e8:bd
          inet addr:192.168.2.99  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:9ff:fece:e8bd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2158 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1948 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2144113 (2.0 MB)  TX bytes:400107 (390.7 KB)
          Interrupt:17

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1369 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1369 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:68488 (66.8 KB)  TX bytes:68488 (66.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3c:1a:36:30
          inet addr:192.168.2.5  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:3cff:fe1a:3630/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:132 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:16643 (16.2 KB)  TX bytes:5199 (5.0 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1F-3C-1A-36-30-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by superprash2003 on 2008-12-19
is 192.168.2.1 your modem ip?? if so post output of ping 192.168.2.1 .. also post output of cat /etc/resolv.conf

---

### Post by nafihsus on 2009-01-07
Happy New Year to all of you. I was out of the country therefore the delay.

192.168.2.1 is my router.
pinging the router with the LAN connected works fine. 
pinging with LAN disconnected results in:

cenk@cenk1:~$ ping 192.168.2.1
PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.
64 bytes from 192.168.2.1: icmp_seq=1 ttl=64 time=0.409 ms
64 bytes from 192.168.2.1: icmp_seq=2 ttl=64 time=0.371 ms
64 bytes from 192.168.2.1: icmp_seq=3 ttl=64 time=0.401 ms
64 bytes from 192.168.2.1: icmp_seq=4 ttl=64 time=0.396 ms
64 bytes from 192.168.2.1: icmp_seq=5 ttl=64 time=0.361 ms
64 bytes from 192.168.2.1: icmp_seq=6 ttl=64 time=0.405 ms
64 bytes from 192.168.2.1: icmp_seq=7 ttl=64 time=0.359 ms
64 bytes from 192.168.2.1: icmp_seq=8 ttl=64 time=0.341 ms
64 bytes from 192.168.2.1: icmp_seq=9 ttl=64 time=0.365 ms

--- 192.168.2.1 ping statistics ---
9 packets transmitted, 9 received, 0% packet loss, time 7998ms
rtt min/avg/max/mdev = 0.341/0.378/0.409/0.032 ms

cenk@cenk1:~$ cat /etc/resolv.conf
search eldenet
nameserver 192.168.2.1

---

### Post by superprash2003 on 2009-01-07
ok with LAN disconnected try opening this [http://74.125.45.100](http://74.125.45.100)

---

### Post by Balthesar on 2009-01-07
Hi there, 

I'm having the same issue with my Dell D430/3945. Ifconfig/iwconfig/bios all show the card as present and operating but the gui network config does not. I had a post all ready to go but i navigated out of the window and erased it...oy. 

I had read your tutorial superprash but thats led me to here. Does your laptop have the on/off/momentary switch on the side for the wifi and "wifi catcher"? 

Thanks Ubuntours! - Alex

---

### Post by superprash2003 on 2009-01-08
no dont see any such switch..post output of
1)iwlist scanning

---

### Post by superprash2003 on 2009-01-08
no dont see any such switch..post output of
1)iwlist scanning

---

### Post by nafihsus on 2009-01-14
Without LAN plugged in I can't reach any Internet address. 
Yes, my WLAN switch is on the left side of the laptop. 
WLAN LED shows that its switched on. 
I used to have a pre-installed Vista where WLAN instantly worked when I booted. In the meantime I have scrapped Vista, am happy with Ubuntu except wireless which just won't work.

---

