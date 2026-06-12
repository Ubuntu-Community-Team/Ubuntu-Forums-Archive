---
title: "How to verify ethernet connection"
date: 2013-01-14
forum: Multimedia Software
---

### Post by Mark_in_Hollywood on 2013-01-14
I have a SiliconDust HD HomeRun ATSC dual tuner. The cables and power are up and running, but my Precise Pangolin ver. 12.04 is not finding the device. Auto ethernet hangs and no connection is made. Anybody know how to make them talk to one-another?

---

### Post by efflandt on 2013-01-15
Are you connecting the tuner and your computer to a router, or trying to directly connect the tuner to your computer?

If you are trying to connect it directly to your computer you might need a "crossover" cable if ethernet on your computer does not auto sense cable type, and likely need to be running a dhcp server in Linux to give the tuner an IP address.

Although, the website for that device gives no clue how to find the tuner on a network.  If you do get it set up to get an IP address see if **avahi-browse -al** (small L) finds it. Or maybe it uses netbios and something related to samba could find it.

---

### Post by Mark_in_Hollywood on 2013-01-15
Directly from tuner to 'puter.

According to the motherboard mfg., MSI, this is the LAN

LAN 
&#8226; Supports 10/100 Fast Ethernet by Realtek 8201EL 

Running avahi-browse -al, I see no connection to my computer at all, those show are the next door neighbors, with whom, I share wifi.

Terminal said:

mark@Lexington-19:~$ avahi-browse -al
+  wlan2 IPv6 iTunes_Ctrl_F2959EAB3AFFD2C8                  iTunes Remote Control local
+  wlan2 IPv4 iTunes_Ctrl_F2959EAB3AFFD2C8                  iTunes Remote Control local
+  wlan2 IPv6 Paul XXXXXXX___s MacBook                      Apple File Sharing   local
+  wlan2 IPv4 Paul XXXXXXX___s MacBook                      Apple File Sharing   local
+  wlan2 IPv6 2837374C54F6@Paul's airport                   AirTunes Remote Audio local
+  wlan2 IPv4 2837374C54F6@Paul's airport                   AirTunes Remote Audio local
+  wlan2 IPv6 Paul's airport                                Apple AirPort        local
+  wlan2 IPv4 Paul's airport                                Apple AirPort        local
+  wlan2 IPv6 uYKfv838VtuTLT7zuf5SuQ@Z/e/Lw/oW8aHx3BLAWtgeA _acp-sync._tcp       local
+  wlan2 IPv4 uYKfv838VtuTLT7zuf5SuQ@Z/e/Lw/oW8aHx3BLAWtgeA _acp-sync._tcp       local
+  wlan2 IPv6 50-35-10-70 Paul's airport                    _sleep-proxy._udp    local
+  wlan2 IPv4 50-35-10-70 Paul's airport                    _sleep-proxy._udp    local

mark@Lexington-19:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 40:61:86:06:56:14  
          inet6 addr: fe80::4261:86ff:fe06:5614/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:130 errors:0 dropped:0 overruns:0 frame:0
          TX packets:102 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:44460 (44.4 KB)  TX bytes:21176 (21.1 KB)
          Interrupt:43 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:186 errors:0 dropped:0 overruns:0 frame:0
          TX packets:186 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:14100 (14.1 KB)  TX bytes:14100 (14.1 KB)

wlan2     Link encap:Ethernet  HWaddr 90:f6:52:0c:2d:a4  
          inet addr:192.168.1.72  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::92f6:52ff:fe0c:2da4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24600 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15342 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10519795 (10.5 MB)  TX bytes:4039483 (4.0 MB)

mark@Lexington-19:~$ netstat -i
Kernel Interface table
Iface   MTU Met   RX-OK RX-ERR RX-DRP RX-OVR    TX-OK TX-ERR TX-DRP TX-OVR Flg
eth0       1500 0       131      0      0 0           102      0      0      0 BMRU
lo        16436 0       186      0      0 0           186      0      0      0 LRU
wlan2      1500 0     24919      0      0 0         15543      0      0      0 BMRU

mark@Lexington-19:~$ ethtool -S eth2
Cannot get driver information: No such device

mark@Lexington-19:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: ttyACM0 --------------------------------------------------------------
  Type:              Mobile Broadband (GSM)
  Driver:            cdc_acm
  State:             disconnected
  Default:           no

  Capabilities:


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            forcedeth
  State:             disconnected
  Default:           no
  HW Address:        40:61:86:06:56:14

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on


- Device: wlan2  [2WIREXXX 2] --------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k_htc
  State:             connected
  Default:           yes
  HW Address:        90:F6:52:0C:2D:A4

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

 54 Mb/s, Strength 30 WEP
    *2WIREXXX:       Infra, 00:22:A4:E2:6D:D9, Freq 2412 MHz, Rate 54 Mb/s, Strength 72 WEP

  IPv4 Settings:
    Address:         192.168.1.72
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254


mark@Lexington-19:~$ sudo lshw -class network
[sudo] password for mark: 
  *-network               
       description: Wireless interface
       physical id: 1
       bus info: usb@1:2.3
       logical name: wlan2
       serial: 90:f6:52:0c:2d:a4
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ath9k_htc driverversion=3.2.0-35-generic-pae firmware=1.3 ip=192.168.1.72 link=yes multicast=yes wireless=IEEE 802.11bgn
mark@Lexington-19:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 wlan2
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan2
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan2

---

