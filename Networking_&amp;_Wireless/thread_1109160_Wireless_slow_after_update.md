---
title: "Wireless slow after update"
date: 2009-03-28
forum: Networking &amp; Wireless
---

### Post by crispy_chunks on 2009-03-28
Hello, I am running 8.10 and recently updated to kernel 2.6.27.11-generic and this made my wireless connection really really really slow. When I ssh into the slow machine typing commands is like getting across 1 character pr second. I have noticed several other persons have this problem and their description is the same as mine. For example:

[http://ubuntuforums.org/showthread.php?t=1092157&highlight=slow](http://ubuntuforums.org/showthread.php?t=1092157&highlight=slow)
[http://ubuntuforums.org/showthread.php?t=1092870&highlight=slow](http://ubuntuforums.org/showthread.php?t=1092870&highlight=slow)

I am very sure this problem is related to the kernel update. Please is anyone else finds similar threads lets stick them all together here.

Changing encryption type, disabling ipv6, rate settings and even network card havent helped. This is so frustrating and I dont want to end up installing the system from scratch again.

**lsusb:**
```
Bus 005 Device 004: ID 0586:3410 ZyXEL Communications Corp. Wi-Fi Wireless LAN Adapter
```

**ifconfig:**
```
wlan1     Link encap:Ethernet  HWaddr 00:19:cb:f4:e6:21  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:553 errors:0 dropped:0 overruns:0 frame:0
          TX packets:373 errors:0 dropped:0 overruns:0 carrier:0
```

**iwconfig:**
```
wlan1     IEEE 802.11bg  ESSID:"KGB"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1D:7E:E0:20:A5   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=72/100  Signal level:47/100  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

**dmesg:**
```
[   47.005651] firmware: requesting zd1211/zd1211b_ub
[   47.049148] firmware: requesting zd1211/zd1211b_uphr
[   47.135510] zd1211rw 5-6:1.0: firmware version 4725
[   47.175515] zd1211rw 5-6:1.0: zd1211b chip 0586:3410 v4810 high 00-19-cb AL2230_RF pa0 g--NS
[   47.213182] /dev/vmnet: open called by PID 5188 (vmnet-bridge)
[   47.213204] /dev/vmnet: hub 0 does not exist, allocating memory.
[   47.213225] /dev/vmnet: port on hub 0 successfully opened
[   47.213255] bridge-wlan1: is a Wireless Adapter
[   47.213263] bridge-wlan1: up
[   47.221189] bridge-wlan1: attached
[   47.221278] bridge-wlan1: disabling the bridge
[   47.233026] bridge-wlan1: down
[   47.233044] bridge-wlan1: detached
[   47.313093] NET: Registered protocol family 17
[   48.166912] wlan1: authenticate with AP 00:1d:7e:e0:20:a5
[   48.364027] wlan1: authenticate with AP 00:1d:7e:e0:20:a5
[   48.564021] wlan1: authenticate with AP 00:1d:7e:e0:20:a5
[   48.648796] wlan1: authenticated
[   48.648809] wlan1: associate with AP 00:1d:7e:e0:20:a5
[   48.848164] wlan1: associate with AP 00:1d:7e:e0:20:a5
[   49.048043] wlan1: associate with AP 00:1d:7e:e0:20:a5
[   49.248032] wlan1: association with AP 00:1d:7e:e0:20:a5 timed out
[   74.172507] wlan1: authenticate with AP 00:1d:7e:e0:20:a5
[   74.184503] wlan1: authenticate with AP 00:1d:7e:e0:20:a5
[   74.388024] wlan1: authenticate with AP 00:1d:7e:e0:20:a5
[   74.430968] wlan1: authenticated
[   74.430985] wlan1: associate with AP 00:1d:7e:e0:20:a5
[   74.633351] wlan1: associate with AP 00:1d:7e:e0:20:a5
[   74.657559] wlan1: RX AssocResp from 00:1d:7e:e0:20:a5 (capab=0x401 status=0 aid=3)
[   74.657573] wlan1: associated
[   74.659170] /dev/vmnet: open called by PID 5188 (vmnet-bridge)
[   74.659193] /dev/vmnet: hub 0 does not exist, allocating memory.
[   74.659214] /dev/vmnet: port on hub 0 successfully opened
[   74.659241] bridge-wlan1: is a Wireless Adapter
[   74.659255] bridge-wlan1: up
[   74.659262] bridge-wlan1: attached
[  140.868531] ppdev0: registered pardevice
[  140.916407] ppdev0: unregistered pardevice
[  141.284667] ppdev0: registered pardevice
[  141.332276] ppdev0: unregistered pardevice
[  142.380851] type=1503 audit(1238262437.887:6): operation="inode_permission" requested_mask="::rw" denied_mask="::rw" fsuid=7 name="/dev/tty" pid=7130 profile="/usr/sbin/cupsd"
[  143.429590] type=1503 audit(1238262438.935:7): operation="inode_permission" requested_mask="::rw" denied_mask="::rw" fsuid=7 name="/dev/tty" pid=7136 profile="/usr/sbin/cupsd"
[  143.467724] type=1503 audit(1238262438.971:8): operation="inode_permission" requested_mask="::rw" denied_mask="::rw" fsuid=7 name="/dev/tty" pid=7137 profile="/usr/sbin/cupsd"
[  143.624153] ppdev0: registered pardevice
[  143.672049] ppdev0: unregistered pardevice

```

**lshw -C network**
```
 *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:03:02.0
       logical name: eth0
       version: 10
       serial: 00:11:2f:59:83:a4
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=127.0.0.1 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan1
       serial: 00:19:cb:f4:e6:21
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.2 multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 6a:ef:15:97:7c:08
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
```

---

### Post by crispy_chunks on 2009-03-28
I solved it. Turns out it was hardware related. My ram were placed in a bad order in the dimms (had been playing around earlier).

Heres how I found out:

Ssh into the machine -> Kill kdm -> net working fine -> install xfce to see if kde was the problem -> same problem -> weird network manager? -> wicd to test instead of nm-applet -> same problem -> video driver? -> test different nvidia drivers -> same problem, but vesa works -> what can cause this? Half wild guess sorted it! HUZZAH!

---

