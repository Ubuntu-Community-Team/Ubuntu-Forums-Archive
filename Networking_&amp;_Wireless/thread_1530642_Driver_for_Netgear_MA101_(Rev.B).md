---
title: "Driver for Netgear MA101 (Rev.B)"
date: 2010-07-13
forum: Networking &amp; Wireless
---

### Post by kzinjuwadia on 2010-07-13
Does anyone know if Netgear MA101 (Rev.B) adapter driver is available for Ubuntu? I'm using Ubuntu 10.04. When I plugged in the adapter, Ubuntu asked to install the atmel firmware, which I did. Unplugging & re-plugging the adapter seems to take care of the earlier error. Following are the .bin that I copied to /lib/firmware.

kzinjuwadia@ubuntu:~$ ls Downloads/at76_usb-firmware-0.1/
atmel_at76c503-i3861.bin      atmel_at76c503-rfmd-acc.bin   atmel_at76c505a-rfmd2958.bin  atmel_at76c505-rfmd.bin       README
atmel_at76c503-i3863.bin      atmel_at76c503-rfmd.bin       atmel_at76c505-rfmd2958.bin   COPYRIGHT                 

I was able to see the networks in the range etc. However, never able to connect. I was able to connect to them from my laptop running Ubuntu 10.04 with internal Intel wireless adapter. So, network has no problem. Later I found that if I don't see driver in the output of "lshw -C network" for the network section of my netgear adapter, the driver is not at all installed.

There is a thread (mentioned below) over same question and the reply directs to links for redhat linux. I don't think it's applicable to ubuntu. Pl do correct me if I'm wrong.

[http://ubuntuforums.org/showthread.php?t=72944](http://ubuntuforums.org/showthread.php?t=72944)

Below is the output of lshw. I have internal Intel wireless adapter and the netgear adapter. I see driver for former but not for latter.

kzinjuwadia@ubuntu:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 82566MM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:1c:25:16:c9:7a
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k2 firmware=0.3-0 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:30 memory:fe200000-fe21ffff memory:fe225000-fe225fff ioport:1840(size=32)
  *-network
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 61
       serial: 00:1d:e0:00:d3:43
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=192.168.2.20 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:32 memory:df2fe000-df2fffff
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan1
       serial: 00:09:5b:10:3c:a7
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11b
kzinjuwadia@ubuntu:~$ 

Some more outputs that I hope will help you. wlan0 is intel adapter. wlan1 is netgear.

kzinjuwadia@ubuntu:~$ sudo lsmod | grep 80211
mac80211              204922  3 at76c50x_usb,iwlagn,iwlcore
cfg80211              126485  3 iwlagn,iwlcore,mac80211
kzinjuwadia@ubuntu:~$ sudo iwconfig wlan1 
wlan1     IEEE 802.11b  ESSID: off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr: off   Fragment thr: off
          Encryption key: off
          Power Management: off
          
kzinjuwadia@ubuntu:~$ sudo iwconfig wlan0 
wlan0     IEEE 802.11abgn  ESSID:"Shubham"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:11:50:3B:BE:93   
          Bit Rate=1 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr: off   Fragment thr: off
          Encryption key: off
          Power Management: off
          Link Quality=60/70  Signal level=-50 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

kzinjuwadia@ubuntu:~$ sudo ifconfig 
. . .
wlan0     Link encap:Ethernet  HWaddr 00:1d:e0:00:d3:43  
          inet addr:192.168.2.20  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:e0ff:fe00:d343/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6908 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6480 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7212626 (7.2 MB)  TX bytes:1061846 (1.0 MB)

wlan1     Link encap:Ethernet  HWaddr 00:09:5b:10:3c:a7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan1:avahi Link encap:Ethernet  HWaddr 00:09:5b:10:3c:a7  
          inet addr:169.254.6.35  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

When I try to bring wlan1 up, I get following in dmesg.
[ 2296.136099] wlan1: direct probe to AP 00:11:50:3b:be:93 timed out
[ 2301.781159] wlan1: direct probe to AP 00:11:50:3b:be:93 (try 1)
[ 2301.980104] wlan1: direct probe to AP 00:11:50:3b:be:93 (try 2)
[ 2302.180101] wlan1: direct probe to AP 00:11:50:3b:be:93 (try 3)
[ 2302.380100] wlan1: direct probe to AP 00:11:50:3b:be:93 timed out
[ 2585.816545] wlan1: deauthenticating from 00:09:5b:9d:d7:48 by local choice (reason=3)
[ 3181.353775] ADDRCONF(NETDEV_UP): wlan1: link is not ready

---

