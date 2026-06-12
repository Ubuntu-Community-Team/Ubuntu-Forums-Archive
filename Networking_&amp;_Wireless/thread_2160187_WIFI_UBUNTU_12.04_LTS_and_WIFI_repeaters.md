---
title: "WIFI UBUNTU 12.04 LTS and WIFI repeaters"
date: 2013-07-05
forum: Networking &amp; Wireless
---

### Post by KeepItSimpleStupid on 2013-07-05
Connections are all but impossible.  Even pings to my router at 10.0.1.1 say for the first few pings it's going to 10.0.1.8 then ping does what it's supposed to do, but it still won't connect.  I'm running the LIVE CD.  A hard drive doesn't even exist in the machine.  A USB stick does for saving files.

I would EXPECT the network control panel for wireless to show the BSSID's available for the SSID and their signal strenghts, but it only shows one.  I would also expect the BSSID's to be listed relative to decreasing signal strenth.  e.g. the one your connected to is the first one in the list.

Now, at this point, I don't know what I have to do to make it connect and I didn't save the odd ping results to my router when i could not connect,

Below, you will find the ping to my broadcast address.  The Dup! entries are not real.  I think, the system is receiving packets from both BSSID's, but i don''t really know how wireless works.

The Wireless is wireless g and it connects at 18 mb/s.

I suppose you want to see these results:

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"WLAN"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: 00:11:50:43:58:25   
          Bit Rate=18 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=64/70  Signal level=-46 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:137   Missed beacon:0

(taken from a 3-D place I could not connect initially)

ubuntu@ubuntu:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
ubuntu@ubuntu:~$ 


IPv4 Settings:
    Address:         10.0.1.8
    Prefix:          24 (255.255.255.0)
    Gateway:         10.0.1.1

    DNS:             10.0.1.1


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        B8:70:F4:55:4C:A8

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off



ubuntu@ubuntu:~$ lspci -nn | grep Network
07:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller [10ec:8172] (rev 10)

The very first time I connected using a cable direct to the wireless AP.

Something, I think, is very amis.

Regards,

KISS



64 bytes from 10.0.1.1: icmp_req=11 ttl=64 time=1.68 ms
64 bytes from 10.0.1.1: icmp_req=12 ttl=64 time=1.73 ms
^C
--- 10.0.1.1 ping statistics ---
12 packets transmitted, 12 received, 0% packet loss, time 11018ms
rtt min/avg/max/mdev = 1.528/1.694/2.189/0.191 ms
ubuntu@ubuntu:~$ ping 10.0.1.255
Do you want to ping broadcast? Then -b
ubuntu@ubuntu:~$ ping -b 10.0.1.255
WARNING: pinging broadcast address
PING 10.0.1.255 (10.0.1.255) 56(84) bytes of data.
64 bytes from 10.0.1.207: icmp_req=1 ttl=64 time=6.06 ms
64 bytes from 10.0.1.231: icmp_req=1 ttl=255 time=7.97 ms (DUP!)
64 bytes from 10.0.1.1: icmp_req=1 ttl=64 time=8.16 ms (DUP!)
64 bytes from 10.0.1.220: icmp_req=1 ttl=64 time=52.9 ms (DUP!)
64 bytes from 10.0.1.5: icmp_req=1 ttl=255 time=54.4 ms (DUP!)
64 bytes from 10.0.1.220: icmp_req=2 ttl=64 time=2.49 ms
64 bytes from 10.0.1.5: icmp_req=2 ttl=255 time=5.96 ms (DUP!)
64 bytes from 10.0.1.231: icmp_req=2 ttl=255 time=6.54 ms (DUP!)
64 bytes from 10.0.1.1: icmp_req=2 ttl=64 time=6.61 ms (DUP!)
64 bytes from 10.0.1.207: icmp_req=2 ttl=64 time=6.72 ms (DUP!)
64 bytes from 10.0.1.220: icmp_req=3 ttl=64 time=3.06 ms
64 bytes from 10.0.1.5: icmp_req=3 ttl=255 time=3.08 ms (DUP!)
64 bytes from 10.0.1.231: icmp_req=3 ttl=255 time=3.14 ms (DUP!)
64 bytes from 10.0.1.1: icmp_req=3 ttl=64 time=3.30 ms (DUP!)
64 bytes from 10.0.1.207: icmp_req=3 ttl=64 time=3.81 ms (DUP!)
64 bytes from 10.0.1.220: icmp_req=4 ttl=64 time=1.58 ms
64 bytes from 10.0.1.231: icmp_req=4 ttl=255 time=2.46 ms (DUP!)
64 bytes from 10.0.1.5: icmp_req=4 ttl=255 time=2.53 ms (DUP!)
64 bytes from 10.0.1.1: icmp_req=4 ttl=64 time=3.10 ms (DUP!)
64 bytes from 10.0.1.207: icmp_req=4 ttl=64 time=6.70 ms (DUP!)
64 bytes from 10.0.1.220: icmp_req=5 ttl=64 time=1.59 ms
64 bytes from 10.0.1.5: icmp_req=5 ttl=255 time=2.54 ms (DUP!)
64 bytes from 10.0.1.231: icmp_req=5 ttl=255 time=2.70 ms (DUP!)
64 bytes from 10.0.1.1: icmp_req=5 ttl=64 time=2.80 ms (DUP!)
64 bytes from 10.0.1.207: icmp_req=5 ttl=64 time=3.59 ms (DUP!)
64 bytes from 10.0.1.220: icmp_req=6 ttl=64 time=1.59 ms
64 bytes from 10.0.1.5: icmp_req=6 ttl=255 time=3.10 ms (DUP!)
64 bytes from 10.0.1.231: icmp_req=6 ttl=255 time=3.23 ms (DUP!)
64 bytes from 10.0.1.1: icmp_req=6 ttl=64 time=3.30 ms (DUP!)
64 bytes from 10.0.1.207: icmp_req=6 ttl=64 time=7.66 ms (DUP!)
64 bytes from 10.0.1.220: icmp_req=7 ttl=64 time=1.57 ms
64 bytes from 10.0.1.5: icmp_req=7 ttl=255 time=2.71 ms (DUP!)
64 bytes from 10.0.1.231: icmp_req=7 ttl=255 time=2.78 ms (DUP!)
64 bytes from 10.0.1.1: icmp_req=7 ttl=64 time=2.92 ms (DUP!)
64 bytes from 10.0.1.207: icmp_req=7 ttl=64 time=3.06 ms (DUP!)
64 bytes from 10.0.1.220: icmp_req=8 ttl=64 time=3.08 ms
64 bytes from 10.0.1.5: icmp_req=8 ttl=255 time=3.09 ms (DUP!)
64 bytes from 10.0.1.231: icmp_req=8 ttl=255 time=4.04 ms (DUP!)
64 bytes from 10.0.1.1: icmp_req=8 ttl=64 time=4.06 ms (DUP!)
64 bytes from 10.0.1.207: icmp_req=8 ttl=64 time=4.20 ms (DUP!)

---

### Post by enduser79 on 2013-07-06
I was getting ttl=255 with this Sabrent card I bought at Fry's, I'm getting schooled on Linux as we speak, but I'm returning this card since it doesn't work correctly.

From the research I've done, you should look into an Alfa Networks card with a 5 or 9 Dbi antenna, they are Linux and Windows compatible and are under $40 (most models)

---

