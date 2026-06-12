---
title: "HP g60-243CL wireless not quite working"
date: 2009-03-09
forum: Networking &amp; Wireless
---

### Post by ucmotorsports on 2009-03-09
Thanks in advance for help! I got it to scan and find the wireless networks in range, but when i try to connect with network-manager I get the 2 grey dots with spinning thingy, to no avail. I have tried to manually configure also. The network has been changed to no encryption for diagnostic purposes...

1. HP G60-243CL
2. Atheros "unknown device" (ar928x according to intrepid live cd)
3. 
```
laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1f:16:6a:49:06  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:253 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2190 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2190 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:109500 (106.9 KB)  TX bytes:109500 (106.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:24:2b:7a:65:f2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-24-2B-7A-65-F2-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

4.
```
laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:""  
          Mode:Managed  Frequency:2.442 GHz  Access Point: Not-Associated   
          Tx-Power=23 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

5.
```
laptop:~$ lsmod | grep ath
ath9k                 271672  0 
lbm_cw_mac80211       271104  1 ath9k
led_class               7176  1 ath9k
```

6.
```
laptop:~$ dmesg | grep ath
[   32.419864] ath9k: 0.1
[   32.848980] phy0: Selected rate control algorithm 'ath9k_rate_control'
[   33.506770] Registered led device: ath9k-phy0:radio
[   33.506791] Registered led device: ath9k-phy0:assoc
[   33.506806] Registered led device: ath9k-phy0:tx
[   33.506820] Registered led device: ath9k-phy0:rx

```

7.
```
laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: nVidia Corporation
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1f:16:6a:49:06
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network
       description: Wireless interface
       product: Atheros Communications Inc.
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wmaster0
       version: 01
       serial: 00:24:2b:7a:65:f2
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k latency=0 module=ath9k multicast=yes wireless=IEEE 802.11abgn
```

8.
```
laptop:~$ iwlist scan
wlan0     Scan completed :
          Cell 03 - Address: 00:1B:2F:E6:AF:AC
                    ESSID:"NETGEAR"
                    Mode:Master
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=93/100  Signal level:-35 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=00000000348eb183
                    Extra: Last beacon: 5032ms ago
```

9.
```

laptop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                   [ OK ] 

```

10. Release: Ubuntu 8.04.2
Kernel: 2.6.24-23-generic x86_64

---

### Post by ucmotorsports on 2009-03-15
bumpitty bump bump...

---

### Post by jcorry on 2009-05-28
Did you ever get this sorted out?

I'm looking at the same laptop and wonder if it'll work...

---

### Post by avilella on 2009-06-02
Hi, did you try Jaunty?

Reports and possible solutions about issues with the Atheros driver (Atheros AR5009):
-- The Atheros drivers are already included in Jaunty.
[http://ubuntuforums.org/showthread.php?p=7218364](http://ubuntuforums.org/showthread.php?p=7218364)
[http://newyork.ubuntuforums.org/showpost.php?p=6772541&postcount=1](http://newyork.ubuntuforums.org/showpost.php?p=6772541&postcount=1)
[http://blog.hyperandy.com/2008/11/01/atheros-ar242x-ubuntu-810-ibex/](http://blog.hyperandy.com/2008/11/01/atheros-ar242x-ubuntu-810-ibex/)
[http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex](http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex)
[http://ubuntuforums.org/showthread.php?t=1120259](http://ubuntuforums.org/showthread.php?t=1120259)


> **ucmotorsports said:**
> Thanks in advance for help! I got it to scan and find the wireless networks in range, but when i try to connect with network-manager I get the 2 grey dots with spinning thingy, to no avail. I have tried to manually configure also. The network has been changed to no encryption for diagnostic purposes...

1. HP G60-243CL
2. Atheros "unknown device" (ar928x according to intrepid live cd)
3. 
```
laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1f:16:6a:49:06  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:253 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2190 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2190 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:109500 (106.9 KB)  TX bytes:109500 (106.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:24:2b:7a:65:f2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-24-2B-7A-65-F2-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

4.
```
laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:""  
          Mode:Managed  Frequency:2.442 GHz  Access Point: Not-Associated   
          Tx-Power=23 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

5.
```
laptop:~$ lsmod | grep ath
ath9k                 271672  0 
lbm_cw_mac80211       271104  1 ath9k
led_class               7176  1 ath9k
```

6.
```
laptop:~$ dmesg | grep ath
[   32.419864] ath9k: 0.1
[   32.848980] phy0: Selected rate control algorithm 'ath9k_rate_control'
[   33.506770] Registered led device: ath9k-phy0:radio
[   33.506791] Registered led device: ath9k-phy0:assoc
[   33.506806] Registered led device: ath9k-phy0:tx
[   33.506820] Registered led device: ath9k-phy0:rx

```

7.
```
laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: nVidia Corporation
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1f:16:6a:49:06
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network
       description: Wireless interface
       product: Atheros Communications Inc.
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wmaster0
       version: 01
       serial: 00:24:2b:7a:65:f2
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k latency=0 module=ath9k multicast=yes wireless=IEEE 802.11abgn
```

8.
```
laptop:~$ iwlist scan
wlan0     Scan completed :
          Cell 03 - Address: 00:1B:2F:E6:AF:AC
                    ESSID:"NETGEAR"
                    Mode:Master
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=93/100  Signal level:-35 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=00000000348eb183
                    Extra: Last beacon: 5032ms ago
```

9.
```

laptop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                   [ OK ] 

```

10. Release: Ubuntu 8.04.2
Kernel: 2.6.24-23-generic x86_64

---

