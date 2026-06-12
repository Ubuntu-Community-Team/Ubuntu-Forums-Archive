---
title: "Giada N20 ethernet port"
date: 2011-06-01
forum: Networking &amp; Wireless
---

### Post by nrune on 2011-06-01
I bought this Giada N20 to run XBMC and Boxee. The unit is less than 30 days old and I am getting a "link not ready" on eth0.  You good folks are my last hope before an RMA back to newegg. 

here's the stuff!
ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:e0:40:68:ec:39  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:43 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1205 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1205 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:279994 (279.9 KB)  TX bytes:279994 (279.9 KB)

wlan0     Link encap:Ethernet  HWaddr e0:b9:a5:48:fb:bb  
          inet addr:192.168.1.112  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::e2b9:a5ff:fe48:fbbb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:397906 errors:0 dropped:0 overruns:0 frame:0
          TX packets:291721 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:404463066 (404.4 MB)  TX bytes:65756226 (65.7 MB)

```

dmesg | grep -e eth0 -e bcm
```
[    8.410054] r8169 0000:02:00.0: eth0: RTL8168d/8111d at 0xf8006000, 00:e0:40:68:ec:39, XID 083000c0 IRQ 43
[   21.080603] r8169 0000:02:00.0: eth0: link down
[   21.081912] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 7103.155452] r8169 0000:02:00.0: eth0: link down
[ 7103.155922] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 7121.781144] r8169 0000:02:00.0: eth0: link down
[ 7121.781626] ADDRCONF(NETDEV_UP): eth0: link is not ready
```

mike@mike-Giada-N20:~$ sudo mii-tool eth0
eth0: no link

I have swapped out cables, I have verfied that cables are good.  I have swapped out routers.  
I have verified that pins are not damaged in the port
I have booted to Ubuntu via thumb drive with the same result. 

Any ideas? 

Mike

---

### Post by nrune on 2011-06-01
The way to fix this is to totally shut the machine down.  Unplug and then plug and boot. 

If you are affected see this bug

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/573259](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/573259)

Mike

---

