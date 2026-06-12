---
title: "Can't Connect to WiFi RTL8191SEvA Ubuntu 11.10 Compaq CQ42"
date: 2012-02-04
forum: Networking &amp; Wireless
---

### Post by vincentpaca on 2012-02-04
Hi, I just recently upgraded from 11.04 to 11.10. After upgrading, I can't connect to any wireless network. I can, however, connect using ethernet.

I have tried the solutions posted here and on the web, but to no avail.

I'm posting here hoping to get some insight and help. Thank you in advance. :)

Here are my details:

**Wireless**
```

lspci | grep -i "Wireless"
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8191SEvA Wireless LAN Controller (rev 10)

```

**Interface**
```

ifconfig
eth0      Link encap:Ethernet  HWaddr c8:0a:a9:d5:bd:ad  
          inet addr:192.168.15.103  Bcast:192.168.15.255  Mask:255.255.255.0
          inet6 addr: fe80::ca0a:a9ff:fed5:bdad/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5555 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6096 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3687117 (3.6 MB)  TX bytes:993746 (993.7 KB)
          Interrupt:40 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 70:f1:a1:cc:b7:d3  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

**Modules**
```

lsmod
...
rtl8192se              94139  0 
rtlwifi                95614  1 rtl8192se
mac80211              393459  2 rtl8192se,rtlwifi
cfg80211              172427  2 rtlwifi,mac80211
...

```

**Net Config**: PCI (sysfs)

**Architecture**: 3.0.0-15-generic-pae i686

**Net Restart**
```

sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...   

```

---

