---
title: "Wireless bg2200 connects but not communicating"
date: 2009-01-03
forum: Networking &amp; Wireless
---

### Post by lcallison on 2009-01-03
I have a Toshiba Tecra A2 with the Intel bg2200 wireless. I actually have a couple of them. They work fine in wireless with xp or vista. It connects to the wireless and gets an ip address but won't talk to anything. I can't ping anything on or off my network. I can see it on the dhcp client list on the router. It connect using eth0 just fine and connects anywhere I want to go. 

Here are the commands and the results that I have done. I am returning to linux after 9 years of not using it, so have forgotten most of what I used to know.

larry@larry-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.
eth0      Interface doesn't support scanning.
eth1      Scan completed :
          Cell 01 - Address: 00:22:75:13:7D:37
                             ESSID:"<hidden>"
                    Protocol:IEEE 802.11bg
                              Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                             Encryption key:on

          Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 11 Mb/s
          9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
          48 Mb/s; 54 Mb/s    Quality=72/100  Signal level=-56 dBm
          IE: WPA Version 1
                        Group Cipher : TKIP
                               Pairwise Ciphers (2) : TKIP CCMP
 Authentication Suites (1) : PSK
                           IE: IEEE 802.11i/WPA2 Version 1 Group Cipher : TKIP
                                  Pairwise Ciphers (2) : TKIP CCMP
 Authentication Suites (1) : PSK
                           Extra: Last beacon: 4784ms ago
pan0      Interface doesn't support scanning.

larry@larry-laptop:~$ ifconfig

eth0      Link encap:Ethernet  HWaddr 00:0e:7b:ba:26:1c  
          UP BROADCAST MULTICAST            MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


eth1      Link encap:Ethernet  HWaddr 00:0e:35:58:49:25  

          inet addr:192.168.117.51  Bcast:192.168.117.255  Mask:255.255.255.0

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:9217 errors:3259 dropped:3259 overruns:0 frame:0

          TX packets:655 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:1307566 (1.3 MB)  TX bytes:5361 (5.3 KB)

          Interrupt:11 Base address:0xc000 Memory:cffff000-cfffffff 


lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:281 errors:0 dropped:0 overruns:0 frame:0

          TX packets:281 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:19023 (19.0 KB)  TX bytes:19023 (19.0 KB)


larry@larry-laptop:~$ sudo lshw -c network

[sudo] password for larry: 

  *-network:0             
       description: Wireless interface

       product: PRO/Wireless 2200BG [Calexico2] Network Connection

       vendor: Intel Corporation
       physical id: 5

       bus info: pci@0000:01:05.0
       logical name: eth1

       version: 05
       serial: 00:0e:35:58:49:25
       width: 32 bits

       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
         configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq        firmware=ABG:9.0.2.6 (Mar 22 2005) ip=192.168.117.53 latency=64 link=yes        maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=IEEE 802.11g
    *-network:1
       description: Ethernet interface

       product: 82801DB PRO/100 VE (MOB) Ethernet Controller

       vendor: Intel Corporation
       physical id: 8

       bus info: pci@0000:01:08.0

       logical name: eth0
       version: 83

       serial: 00:0e:7b:ba:26:1c

       size: 10MB/s

       capacity: 100MB/s

       width: 32 bits

       clock: 33MHz

       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt         100bt-fd autonegotiation

       configuration: autonegotiation=on broadcast=yes driver=e100        driverversion=3.5.23-k4-NAPI duplex=half firmware=N/A latency=64 link=no        maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s

  *-network DISABLED
       description: Ethernet interface

       physical id: 2
       logical name: pan0
       serial: ae:72:85:96:8c:fc
              capabilities: ethernet physical

       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes        multicast=yes

larry@larry-laptop:~$ lsmod | grep bcm

larry@larry-laptop:~$ lsmod | grep b43

larry@larry-laptop:~$ lsmod | grep ndis

larry@larry-laptop:~$ uname -r

2.6.27-7-generic

Sorry this is so long. I copied it out of terminal and then copied it out of notepad on my xp laptop.

Any help appreciated.

Update - last night, it would connect easily, but not communicate. This morning, after connecting with eth0, it would not connect with wireless until I turned protection off on my router. Then, it connected immediately, but still no communication. It looks like, to me, that it is not reading any of the incoming packets.

---

### Post by lcallison on 2009-01-03
bump

---

### Post by lcallison on 2009-01-03
update. I figured out how to install ndisgtk and installed the windows driver. That was a mistake. Now, it locks up on initial load and won't start at all. The first time I did it, I had missed a command on the blacklisting of ipw2200. So, I reinstalled ubuntu and tried again. No such luck. I think I'll junk ubuntu and go try fedora.

---

### Post by pkands on 2009-01-04
I have similar problems with all Debian based systems that I have tried but only at work. I have BCM4211 using the SLA driver. Same thing with b43.
At home all is well. At work I get an IP address, etc but no internet. No wep or wpa involved.
This has been the case for 7.04 and up. Fedora works fine. XP ok.
I've tried dhclient but that doesn't help.
Does anyone have any suggestions about what might be causing this?

---

