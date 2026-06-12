---
title: "Ralink RT2501USB (148f:2573) not working in Jaunty 64"
date: 2009-08-16
forum: Networking &amp; Wireless
---

### Post by d1ng3r on 2009-08-16
Hi,

I'm running Jaunty 64 on an amd x64 machine. 

```
2.6.28-14-generic
```I bought a generic Ralink RT2501usb wireless nic. 

When I booted up for the first time with the nic plugged in the system recognised it but I was unable to connect to wireless networks. 

```
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 008: ID 17a1:0128  
Bus 001 Device 007: ID 0c10:0000  
Bus 001 Device 006: ID 0458:003a KYE Systems Corp. (Mouse Systems) 
Bus 001 Device 005: ID 0e8f:6001 GreenAsia Inc. 
Bus 001 Device 004: ID 148f:2573 Ralink Technology, Corp. RT2501USB Wireless Adapter
Bus 001 Device 003: ID 0409:0058 NEC Corp. HighSpeed Hub
Bus 001 Device 002: ID 13fd:1840 Initio Corporation 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```I've spent the last two days reading through forums but have been unable to find the solution to my problem. 

I've tried using the drivers that come with the kernel (RT73usb). 

```
root@dingers-pc:/usr/src/modules/ndiswrapper# lsmod | grep rt
rt73usb                35716  0 
crc_itu_t              10496  1 rt73usb
rt2x00usb              20352  1 rt73usb
rt2x00lib              43008  2 rt73usb,rt2x00usb
led_class              13064  1 rt2x00lib
mac80211              251528  2 rt2x00usb,rt2x00lib
cfg80211               43680  2 rt2x00lib,mac80211
parport                49584  2 ppdev,lp
``````
root@dingers-pc:/home/dinger# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"Baldingers"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: 00:12:0E:4C:90:57   
          Bit Rate=54 Mb/s   Tx-Power=5 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Encryption key:off
          Power Management:off
          Link Quality=71/100  Signal level:-52 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```
When I try to connect using wicd it says "obtaining ip address." and doesn't connect. I've disabled encryption on my network so that I can just get the wireless working. 

If I remove and blacklist rt73usb, rt2x00usb and rt2x00lib and try to use ndiswrapper 

```

root@dingers-pc:/usr/src/modules/ndiswrapper# lsmod |grep ndis
ndiswrapper           250624  0 
```When I run ndisgtk I can select either the rt73i.nf or the rt2500.inf from the winx64 directory on the windows partition. The rt73.inf returns the error unable to see if hardware is present but then it says present: yes in the status windows 

```

root@dingers-pc:/home/dinger# ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
rt73 : driver installed
    device (148F:2573) present (alternate driver: rt2500usb)
```If I use the rt2500 drivers that ndiswrapper's site says I should use

It tells me it cannot detect if the hardware is present:

```

root@dingers-pc:/home/dinger# ndiswrapper -l
rt2500usb : driver installed
```I can then force it:

```
root@dingers-pc:/home/dinger# ndiswrapper -a 148f:2573 rt2500usb
WARNING: Driver 'rt2500usb' will be used for '148F:2573'
This is safe _only_ if driver rt2500usb is meant for chip in device 148F:2573
root@dingers-pc:/home/dinger# ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
rt2500usb : driver installed
    device (148F:2573) present (alternate driver: rt2500usb)
```This also just says obtaining ip address when I try to connect, then times out. 
```

root@dingers-pc:/usr/src/modules/ndiswrapper# lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:21:85:5f:42:93
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full latency=0 link=yes module=r8169 multicast=yes port=MII speed=100MB/s
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 9a:d4:c2:57:9a:50
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
  *-network:1
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:0e:e8:d6:49:c8
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+rt73 driverversion=1.53+Ralink,09/07/2006, 1.01.03. link=yes multicast=yes wireless=IEEE 802.11g


``````
I cannot complile the ndiswrapper from source. It gives me this error: 
alink,09/07/2006, 1.01.03. link=yes multicast=yes wireless=IEEE 802.11g
root@dingers-pc:/usr/src/modules/ndiswrapper# make
make -C /usr/src/linux-headers-2.6.28-14-generic M=/usr/src/modules/ndiswrapper
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-14-generic'
  MKEXPORT /usr/src/modules/ndiswrapper/crt_exports.h
  CC [M]  /usr/src/modules/ndiswrapper/crt.o
  MKEXPORT /usr/src/modules/ndiswrapper/hal_exports.h
  CC [M]  /usr/src/modules/ndiswrapper/hal.o
  CC [M]  /usr/src/modules/ndiswrapper/iw_ndis.o
/usr/src/modules/ndiswrapper/iw_ndis.c: In function ‘ndis_translate_scan’:
/usr/src/modules/ndiswrapper/iw_ndis.c:1031: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/usr/src/modules/ndiswrapper/iw_ndis.c:1031: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/usr/src/modules/ndiswrapper/iw_ndis.c:1031: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/usr/src/modules/ndiswrapper/iw_ndis.c:1031: error: too few arguments to function ‘iwe_stream_add_event’
/usr/src/modules/ndiswrapper/iw_ndis.c:1041: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/usr/src/modules/ndiswrapper/iw_ndis.c:1041: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/usr/src/modules/ndiswrapper/iw_ndis.c:1041: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/usr/src/modules/ndiswrapper/iw_ndis.c:1041: error: too few arguments to function ‘iwe_stream_add_point’
/usr/src/modules/ndiswrapper/iw_ndis.c:1047: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/usr/src/modules/ndiswrapper/iw_ndis.c:1047: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/usr/src/modules/ndiswrapper/iw_ndis.c:1047: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/usr/src/modules/ndiswrapper/iw_ndis.c:1047: error: too few arguments to function ‘iwe_stream_add_event’
/usr/src/modules/ndiswrapper/iw_ndis.c:1058: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/usr/src/modules/ndiswrapper/iw_ndis.c:1058: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/usr/src/modules/ndiswrapper/iw_ndis.c:1058: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/usr/src/modules/ndiswrapper/iw_ndis.c:1058: error: too few arguments to function ‘iwe_stream_add_event’
/usr/src/modules/ndiswrapper/iw_ndis.c:1073: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/usr/src/modules/ndiswrapper/iw_ndis.c:1073: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/usr/src/modules/ndiswrapper/iw_ndis.c:1073: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/usr/src/modules/ndiswrapper/iw_ndis.c:1073: error: too few arguments to function ‘iwe_stream_add_event’
/usr/src/modules/ndiswrapper/iw_ndis.c:1087: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/usr/src/modules/ndiswrapper/iw_ndis.c:1087: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/usr/src/modules/ndiswrapper/iw_ndis.c:1087: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/usr/src/modules/ndiswrapper/iw_ndis.c:1087: error: too few arguments to function ‘iwe_stream_add_event’
/usr/src/modules/ndiswrapper/iw_ndis.c:1098: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/usr/src/modules/ndiswrapper/iw_ndis.c:1098: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/usr/src/modules/ndiswrapper/iw_ndis.c:1098: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/usr/src/modules/ndiswrapper/iw_ndis.c:1098: error: too few arguments to function ‘iwe_stream_add_point’
/usr/src/modules/ndiswrapper/iw_ndis.c:1114: warning: passing argument 1 of ‘iwe_stream_add_value’ from incompatible pointer type
/usr/src/modules/ndiswrapper/iw_ndis.c:1114: warning: passing argument 4 of ‘iwe_stream_add_value’ from incompatible pointer type
/usr/src/modules/ndiswrapper/iw_ndis.c:1114: warning: passing argument 5 of ‘iwe_stream_add_value’ makes pointer from integer without a cast
/usr/src/modules/ndiswrapper/iw_ndis.c:1114: error: too few arguments to function ‘iwe_stream_add_value’
/usr/src/modules/ndiswrapper/iw_ndis.c:1125: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/usr/src/modules/ndiswrapper/iw_ndis.c:1125: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/usr/src/modules/ndiswrapper/iw_ndis.c:1125: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/usr/src/modules/ndiswrapper/iw_ndis.c:1125: error: too few arguments to function ‘iwe_stream_add_point’
/usr/src/modules/ndiswrapper/iw_ndis.c:1131: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/usr/src/modules/ndiswrapper/iw_ndis.c:1131: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/usr/src/modules/ndiswrapper/iw_ndis.c:1131: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/usr/src/modules/ndiswrapper/iw_ndis.c:1131: error: too few arguments to function ‘iwe_stream_add_point’
/usr/src/modules/ndiswrapper/iw_ndis.c:1153: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/usr/src/modules/ndiswrapper/iw_ndis.c:1153: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/usr/src/modules/ndiswrapper/iw_ndis.c:1153: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/usr/src/modules/ndiswrapper/iw_ndis.c:1153: error: too few arguments to function ‘iwe_stream_add_point’
make[2]: *** [/usr/src/modules/ndiswrapper/iw_ndis.o] Error 1
make[1]: *** [_module_/usr/src/modules/ndiswrapper] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-14-generic'
make: *** [modules] Error 2

```ifconfig gives: 

```
root@dingers-pc:/usr/src/modules/ndiswrapper# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:21:85:5f:42:93  
          inet addr:10.0.0.250  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::221:85ff:fe5f:4293/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9517 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9300 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5228400 (5.2 MB)  TX bytes:962616 (962.6 KB)
          Interrupt:251 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2102 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2102 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:89820 (89.8 KB)  TX bytes:89820 (89.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:0e:e8:d6:49:c8  
          inet6 addr: fe80::20e:e8ff:fed6:49c8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:152 (152.0 B)  TX bytes:3540 (3.5 KB)

wlan0:avahi Link encap:Ethernet  HWaddr 00:0e:e8:d6:49:c8  
          inet addr:169.254.9.109  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

```
Please advise me how I can get this wireless card working?

thanks for your help

---

