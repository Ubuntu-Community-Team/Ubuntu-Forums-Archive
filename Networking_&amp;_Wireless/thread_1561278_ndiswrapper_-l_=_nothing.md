---
title: "ndiswrapper -l = nothing?"
date: 2010-08-26
forum: Networking &amp; Wireless
---

### Post by soryu on 2010-08-26
i get nothing when i run this command,


mint@mint-desktop ~ $ dmesg | grep -e ndis -e wlan
[   24.690280] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  680.664522] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[  680.692174] usbcore: registered new interface driver ndiswrapper
mint@mint-desktop ~ $ ndiswrapper -l
mint@mint-desktop ~ $ 


what step am i missing here?

---

### Post by dineshs on 2010-08-26
I think it is because the driver is not installed.Pl post the results of
```
sudo lshw -C network
```and
```
iwconfig
```

---

### Post by soryu on 2010-08-26
here you GO.

hope this helps.




 _________________________________________
( Q: How many psychiatrists does it take  )
( to change a light bulb? A: Only one,    )
( but it takes a long time, and the light )
( bulb has                                )
(                                         )
( to really want to change.               )
 -----------------------------------------
  o
   o   \_\_    _/_/
    o      \__/
           (oo)\_______
           (__)\       )\/\
               ||----w |
               ||     ||
mint@mint-desktop ~ $ sudo lshw -c network
[sudo] password for mint: 
  *-network:0             
       description: Wireless interface
       product: RT2600 802.11 MIMO
       vendor: RaLink
       physical id: 3
       bus info: pci@0000:00:03.0
       logical name: wmaster0
       version: 00
       serial: 00:1e:e5:a9:72:3b
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci latency=66 multicast=yes wireless=IEEE 802.11bg
       resources: irq:3 memory:b0000000-b0007fff
  *-network:1
       description: Ethernet interface
       product: SMC2-1211TX
       vendor: Accton Technology Corporation
       physical id: 5
       bus info: pci@0000:00:05.0
       logical name: eth0
       version: 10
       serial: 00:10:b5:83:10:57
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.3 latency=66 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: irq:5 ioport:1000(size=256) memory:81000000-810000ff
mint@mint-desktop ~ $ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=9 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

mint@mint-desktop ~ $

---

### Post by dineshs on 2010-08-27
Remove your ethernet cable run this command
```
sudo dhclient wlan0
```and post the output of```
sudo lshw -C network
```and
```
iwconfig
```

---

### Post by soryu on 2010-08-27
ok,:D


 ________________________________________
/ Hain't we got all the fools in town on \
| our side? And hain't that a big enough |
| majority in any town?                  |
|                                        |
\ -- Mark Twain, "Huckleberry Finn"      /
 ----------------------------------------
       \   ,__,
        \  (oo)____
           (__)    )\
              ||--|| *
mint@mint-desktop ~ $ sudo dhclient wlan0
[sudo] password for mint: 
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:1e:e5:a9:72:3b
Sending on   LPF/wlan0/00:1e:e5:a9:72:3b
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
 * Reloading /etc/samba/smb.conf smbd only
   ...done.
mint@mint-desktop ~ $ sudo lshw -c network
  *-network:0             
       description: Wireless interface
       product: RT2600 802.11 MIMO
       vendor: RaLink
       physical id: 3
       bus info: pci@0000:00:03.0
       logical name: wmaster0
       version: 00
       serial: 00:1e:e5:a9:72:3b
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci latency=66 multicast=yes wireless=IEEE 802.11bg
       resources: irq:3 memory:b0000000-b0007fff
  *-network:1
       description: Ethernet interface
       product: SMC2-1211TX
       vendor: Accton Technology Corporation
       physical id: 5
       bus info: pci@0000:00:05.0
       logical name: eth0
       version: 10
       serial: 00:10:b5:83:10:57
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=66 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: irq:5 ioport:1000(size=256) memory:81000000-810000ff
mint@mint-desktop ~ $ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=9 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

mint@mint-desktop ~ $

---

### Post by dineshs on 2010-08-28
Hope you have enabled wireless in the modem/router.pl also see
[http://ubuntuforums.org/showpost.php?p=9680300&postcount=14](http://ubuntuforums.org/showpost.php?p=9680300&postcount=14)

---

### Post by soryu on 2010-08-28
checking router settings.
Wireless should be enabled. Laptop is working. 



HeYNoW!

---

### Post by soryu on 2010-08-28
looks like something working.
i dont know what it is though


mint@mint-desktop ~ $ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
rt61 : driver installed
	device (1814:0401) present (alternate driver: rt61pci)
mint@mint-desktop ~ $ 



so, card is being recognized.
what do i need left to go wireless?

---

### Post by dineshs on 2010-08-29
what about```
iwconfig
```
it shuld say something like
Access Point: 00:22:93:8E:95:AB
Access Point: Not-Associated is not a good sign

---

### Post by soryu on 2010-08-30
________________________
/ Don't Worry, Be Happy. \
|                        |
\ -- Meher Baba          /
 ------------------------
       \   ,__,
        \  (oo)____
           (__)    )\
              ||--|| *
mint@mint-desktop ~ $ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Auto  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:20 dBm   Sensitivity=-121 dBm  
          RTS thr=2347 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
:confused:

---

### Post by soryu on 2010-08-31
(going thru troubleshooting guide)

---

### Post by JSchultheis on 2011-09-19
> **dineshs said:**
> Remove your ethernet cable run this command
```
sudo dhclient wlan0
```and post the output of```
sudo lshw -C network
```and
```
iwconfig
```


```
 jeremy@poslaptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

jeremy@poslaptop:~$ sudo dhclient wlan0
SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
jeremy@poslaptop:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 07d1:3b11 D-Link System DWA-130 802.11n Wireless N Adapter(rev.A1) [Marvell W8360USB]
Bus 001 Device 002: ID 0930:6544 Toshiba Corp. Kingston DataTraveler 2.0 Stick (2GB)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
jeremy@poslaptop:~$ 
``````
 jeremy@poslaptop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 01
       serial: 00:0b:db:99:65:0f
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=32 link=no multicast=yes port=twisted pair speed=10Mbit/s
       resources: irq:7 memory:fcffe000-fcffffff
jeremy@poslaptop:~$  
```I can connect with ethernet.
lsusb finds my DWA-130



I had been working through from the beginning of the thread and I still have:

```
 jeremy@poslaptop:~$ ndiswrapper -l
jeremy@poslaptop:~$ 
 
```


Where am I getting stuck? any ideas? :popcorn:

---

