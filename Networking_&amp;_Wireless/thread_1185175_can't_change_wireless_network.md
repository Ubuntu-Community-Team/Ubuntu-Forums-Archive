---
title: "can't change wireless network"
date: 2009-06-12
forum: Networking &amp; Wireless
---

### Post by kaston on 2009-06-12
I can't change the network that I am connected to.  Usually I just click on the "staircase" in the toolbar to bring up a list of available networks and then click on the one i want to connect to, but nothing happens when I do this.

Also, is there a way to specify which network I want to connect to among several available ones on startup?

---

### Post by superprash2003 on 2009-06-12
post output of the following
1)lshw -C network
2)iwconfig
3)sudo iwlist scan

---

### Post by kaston on 2009-06-12
1)lshw -C network

WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth1
       version: 02
       serial: 00:19:d2:52:f0:74
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.2.2mp firmware=14.2 1:0 () ip=192.168.1.75 latency=0 module=ipw3945 multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: PRO/100 VE Network Connection
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:07:08.0
       logical name: eth0
       version: 02
       serial: 00:a0:d1:68:e2:a9
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.17-k4-NAPI firmware=N/A latency=66 maxlatency=56 mingnt=8 module=e100 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 00:76:62:6e:65:74
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

2)iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"scooby1"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:19:E4:26:DC:B9   
          Bit Rate:54 Mb/s   Tx-Power:14 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=93/100  Signal level=-37 dBm  Noise level=-48 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:6266   Missed beacon:0

vboxnet0  no wireless extensions.

3)sudo iwlist scan

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:21:29:BB:EB:46
                    ESSID:"CeK"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=46/100  Signal level=-81 dBm  Noise level=-81 dBm
                    Extra: Last beacon: 64ms ago
          Cell 02 - Address: 00:19:E4:26:DC:B9
                    ESSID:"scooby1"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=92/100  Signal level=-39 dBm  Noise level=-39 dBm
                    Extra: Last beacon: 8ms ago
          Cell 03 - Address: 00:22:A4:EF:25:69
                    ESSID:"Ari & Mira"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=55/100  Signal level=-75 dBm  Noise level=-75 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 244ms ago

vboxnet0  Interface doesn't support scanning.

---

