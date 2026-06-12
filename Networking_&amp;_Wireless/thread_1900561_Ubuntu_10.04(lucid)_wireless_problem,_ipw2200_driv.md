---
title: "Ubuntu 10.04(lucid) wireless problem, ipw2200 driver"
date: 2011-12-26
forum: Networking &amp; Wireless
---

### Post by Daivana on 2011-12-26
Hello!

I have searched everywhere for a solution for my problem I hope someone can help me here.

I have one desktop computer (Windows XP) which is connected to a router and a laptop with Ubuntu 10.04(lucid) on it.

On my windows machine I created a bridged network (Wired+Wireless), I have a Wireless USB Adapter 54 Mbps (TP-Link, TL-WN322G) connected to my desktop PC.

So what I am trying to do is to use the wireless on my laptop.

I am using Wicd Network manager, in there I can see my network and when I try to connect to it says "Connection failed: Could not contact the wireless access point" :confused:

My desktop pc network configurations are::-?

"Network bridge"

IP address - 192.168.2.100
Subnet mask - 255.255.255.0
Default gateway - 192.168.2.1
----
Preferred DNS server - 192.168.2.1


"Wireless network connection" :-?

/=Properties>Wireless networks=/
In preferred networks I created a network with open authentication 
and disabled data encryption. (Computer-to-computer(Ad-hock) networks only)


So the setup on the Windows machine is just fine and I can surf the web with no problems ( wired Of Course ).


Now the laptop. :idea:

In Wicd network manager I see the desktops PC wireless network,
I click "Connect" and after some thinking it says "Connection failed: Could not contact the wireless access point"
I am using static IP: 
IP - 192.168.2.103
netmask - 255.255.255.0
Gateway - 192.168.2.2 <--- The gateway is different, but using 2.1 won't work either, why I use 192.168.2.2 it is because at the time when laptop tries to connect I can ping the laptop from my desktop pc, I could even use ["Synergy"]("http://synergy-foss.org/")


Now the troubleshooting commands: :-s

```
daivana@ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: 00:c0:9f:70:b1:80
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.2.105 latency=64 maxlatency=64 mingnt=32 multicast=yes
       resources: irq:10 ioport:3000(size=256) memory:e0205800-e02058ff
  *-network:1
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 6
       bus info: pci@0000:02:06.0
       logical name: eth1
       version: 05
       serial: 00:0e:35:bd:49:c7
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) latency=64 maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11g
       resources: irq:11 memory:e0204000-e0204fff
```


sudo lspci -nn

```
02:06.0 Network controller [0280]: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection [8086:4220] (rev 05)
```


```
daivana@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"New"  
          Mode:Ad-Hoc  Frequency:2.457 GHz  Cell: 02:0E:35:9B:C0:96   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=98/100  Signal level=-23 dBm  Noise level=-85 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:2   Missed beacon:0
```



```
daivana@ubuntu:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 94:0C:6D:FB:F9:CC
                    ESSID:"engelits"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.427 GHz (Channel 4)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=61/100  Signal level=-64 dBm  
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 132ms ago
          Cell 02 - Address: 02:0E:35:9B:C0:96
                    ESSID:"New"
                    Protocol:IEEE 802.11bg
                    Mode:Ad-Hoc
                    Frequency:2.457 GHz (Channel 10)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 9 Mb/s; 11 Mb/s
                              6 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=100/100  Signal level=-17 dBm  
                    Extra: Last beacon: 4ms ago
```



Please help :)

---

### Post by Daivana on 2011-12-29
bump

---

