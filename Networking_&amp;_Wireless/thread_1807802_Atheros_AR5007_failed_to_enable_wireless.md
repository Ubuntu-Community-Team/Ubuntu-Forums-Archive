---
title: "Atheros AR5007 failed to enable wireless"
date: 2011-07-19
forum: Networking &amp; Wireless
---

### Post by message on 2011-07-19
Hey guys, i have a problem. Ubuntu recognize my wifi adapter which is Atheros AR5007, but when i open context menu to connect to wireless network it just simply shows me that wireless is disabled and even when i checked "Enable wireless" option nothing happend.

[IMG]http://habrastorage.org/storage1/36a7952e/62cbf0aa/2f4c7e9b/c78d424d.png[/IMG]

Here is information from terminal

```

$ ifconfig
eth0      Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx
          inet addr:192.168.1.7  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: xxxx::xxx:xxxx:xxxx:xxxx/xx Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9976 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5406 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14785376 (14.7 MB)  TX bytes:458029 (458.0 KB)
          Interrupt:41 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

```

There is no any wireless device, only my wired network.

```

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```

Yay, wlan0 exists but Power Management is off.

```

$ iwlist wlan0 scan
wlan0     Failed to read scan data : Network is down

```

```

$ sudo iwconfig wlan0 power on

Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device wlan0 ; Operation not supported.

```

Also i tried to install windows drivers with ndiswrapper but no any luck.

I googled all this things but there is a lot of useless information. Can somebody help me with this? 

My system is up-to-date Ubuntu 11.04

```

$ uname -a
Linux linux 2.6.38-10-generic #46-Ubuntu SMP Tue Jun 28 15:05:41 UTC 2011 i686 athlon i386 GNU/Linux

```

---

### Post by message on 2011-07-19
As usual... You need to tell somebody about your problem and you will fix it. I found solution

```

sudo rmmod -f ath5k
sudo rfkill unblock all
sudo modprobe ath5k

```

---

