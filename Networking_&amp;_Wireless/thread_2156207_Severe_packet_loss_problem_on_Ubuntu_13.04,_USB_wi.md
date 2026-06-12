---
title: "Severe packet loss problem on Ubuntu 13.04, USB wireless adapter"
date: 2013-06-20
forum: Networking &amp; Wireless
---

### Post by johnyy on 2013-06-20
Hi,


The machine is a desktop connecting to a 802.11 b/g/n AP using a usb wireless adaptor.
Chip-set of the adapter is Ratlink 2870/3070.
Running rt2800usb.


Network works but it's slow and unstable.


Here is a ping result to the AP.


The wireless was once not working at all although wireless manager shows it is connected to the AP, then I change the AP setting to use WPA and AES from (WPA2 and TKIP/AES mixed). After this network was fine for a while. Until I suspend the computer for a while and resumed. Restarting the computer at this point didn't help.






```

64 bytes from 192.168.0.1: icmp_req=245 ttl=128 time=1303 ms
64 bytes from 192.168.0.1: icmp_req=246 ttl=128 time=297 ms
64 bytes from 192.168.0.1: icmp_req=247 ttl=128 time=297 ms
64 bytes from 192.168.0.1: icmp_req=248 ttl=128 time=281 ms
64 bytes from 192.168.0.1: icmp_req=249 ttl=128 time=302 ms
64 bytes from 192.168.0.1: icmp_req=250 ttl=128 time=281 ms
64 bytes from 192.168.0.1: icmp_req=251 ttl=128 time=1327 ms
64 bytes from 192.168.0.1: icmp_req=252 ttl=128 time=333 ms
--- 192.168.0.1 ping statistics ---
256 packets transmitted, 117 received, 54% packet loss, time 256080ms
rtt min/avg/max/mdev = 0.833/307.254/6080.003/606.228 ms, pipe 7

```


Where should I be looking at?

---

### Post by praseodym on 2013-06-21
Please show:
```

route -n
iwconfig
sudo iwlist scan
cat /etc/resolv.conf
ifconfig -a
```

---

### Post by johnyy on 2013-06-21
route -n
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

```


iwconfig
```

eth0      no wireless extensions.




lo        no wireless extensions.




wlan0     IEEE 802.11bgn  ESSID:"YHome"  
          Mode:Managed  Frequency:2.432 GHz  Access Point: C8:3A:35:4E:87:38   
          Bit Rate=135 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=70/70  Signal level=-37 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:149  Invalid misc:35   Missed beacon:0

```


iwlist scan
```

eth0      Interface doesn't support scanning.




lo        Interface doesn't support scanning.




wlan0     Scan completed :
          Cell 01 - Address: C8:3A:35:4E:87:38
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=70/70  Signal level=-39 dBm  
                    Encryption key:on
                    ESSID:"YHome"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000134fc961c9
                    Extra: Last beacon: 288ms ago
                    IE: Unknown: 000559486F6D65
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 030105
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFE181BFFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D16050D0400000000000000000000000000000000000000
                    IE: Unknown: DD090010180202F02C0000
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 02 - Address: 00:24:A5:15:6E:7B
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key:on
                    ESSID:"Kole"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000024a87b26
                    Extra: Last beacon: 26964ms ago
                    IE: Unknown: 00044B6F6C65
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1ACC111BFFFF000000000000000000000100000000000000000000
                    IE: Unknown: 3D1606000000000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD6E0050F204104A0001101044000101103B0001031047001037B43BA86FE05D1FAED4F05960A7435D1021000644442D5752541023000C5748522D48502D473330304E10240001301042000531323334351054000800060050F2040001101100044B6F6C65100800020104103C000101

```


cat /etc/resolve.conf
```

# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1

```


ifconfig -a
```

eth0      Link encap:Ethernet  HWaddr 10:bf:48:79:f5:de  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)




lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:3642 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3642 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:433184 (433.1 KB)  TX bytes:433184 (433.1 KB)




wlan0     Link encap:Ethernet  HWaddr 00:b0:8c:06:ca:d4  
          inet addr:192.168.0.200  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2b0:8cff:fe06:cad4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:28440 errors:0 dropped:0 overruns:0 frame:0
          TX packets:37127 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:19598900 (19.5 MB)  TX bytes:7129582 (7.1 MB)

```

---

### Post by praseodym on 2013-06-21
Try to set the channel to "ficed", e.g. No. 13. Additionally, you can deactivate the power management:
```

sudo iwconfig wlan0 power off
```
IPv6 is "ignored" in the network-manager?

---

### Post by johnyy on 2013-06-21
The connection appears to be much better after power off.

In addition, rt2800usb isn't loading automatically at start up. Need to modprobe rt2800usb to enable wireless. What can be done here to load it automatically?

IPv6 isn't showing in AP setting, it doesn't seem to affect network usage? Is it necessary?\

The channel is switched to 11. There is no 13 here. The bit rate seemed to have dropped slightly then channel 6.

Currently still have 15% packet loss rate, but internet is much more usable than having power management on.

iwconfig

```

eth0      no wireless extensions.

lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"YHome"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: C8:3A:35:4E:87:38   
          Bit Rate=58.5 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=69/70  Signal level=-41 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:922  Invalid misc:152   Missed beacon:0

```

---

### Post by praseodym on 2013-06-21
```
echo rt2800usb | sudo tee -a /etc/modules
```
should do the trick.

---

### Post by johnyy on 2013-06-24
Thanks that is working.

---

