---
title: "two wireless interfaces on one Atheros card Acer Aspire 5720"
date: 2009-01-14
forum: Networking &amp; Wireless
---

### Post by ubuntunewb75 on 2009-01-14
I recently upgraded a friends laptop from kernel 2.6.24-19 to 2.6.24-23.  His atheros card was working fine, now its a no-go.  I compiled the madwifi-hal-xxx-current.tar.gz and now an ifconfig looks like this:

ath0      Link encap:Ethernet  HWaddr 00:1e:4c:50:d7:0f
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth0      Link encap:Ethernet  HWaddr 00:1b:38:69:74:7b
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:38ff:fe69:747b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5088 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3639 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:6657610 (6.3 MB)  TX bytes:417433 (407.6 KB)
          Interrupt:18

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:22 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1100 (1.0 KB)  TX bytes:1100 (1.0 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-1E-4C-50-D7-0F-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:74 errors:0 dropped:0 overruns:0 frame:69
          TX packets:153 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:280
          RX bytes:5388 (5.2 KB)  TX bytes:7038 (6.8 KB)
          Interrupt:19

I am thinking it should be one or the other there for my wifi card.  I only have one entry in the restricted hardware widget for atheros proprietary cards.  there is no HAL entry.  he is running Kubuntu 8.04.  I guess the main question is I'd like to get this down to one interface.

---

### Post by Sava8420 on 2009-01-14
> **ubuntunewb75 said:**
> I recently upgraded a friends laptop from kernel 2.6.24-19 to 2.6.24-23.  His atheros card was working fine, now its a no-go.  I compiled the madwifi-hal-xxx-current.tar.gz and now an ifconfig looks like this:

ath0      Link encap:Ethernet  HWaddr 00:1e:4c:50:d7:0f
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth0      Link encap:Ethernet  HWaddr 00:1b:38:69:74:7b
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:38ff:fe69:747b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5088 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3639 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:6657610 (6.3 MB)  TX bytes:417433 (407.6 KB)
          Interrupt:18

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:22 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1100 (1.0 KB)  TX bytes:1100 (1.0 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-1E-4C-50-D7-0F-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:74 errors:0 dropped:0 overruns:0 frame:69
          TX packets:153 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:280
          RX bytes:5388 (5.2 KB)  TX bytes:7038 (6.8 KB)
          Interrupt:19

I am thinking it should be one or the other there for my wifi card.  I only have one entry in the restricted hardware widget for atheros proprietary cards.  there is no HAL entry.  he is running Kubuntu 8.04.  I guess the main question is I'd like to get this down to one interface.

Nah that is completely normal for it to show two different devices as they are the same device.  You should have a master and a physical which by your ifconfig results it appears that your ath0 is your physical device that you should be using to connect.  Run this code and post the results:
```
sudo lshw -C network
sudo iwlist ath0 scan
```

This will identify your wireless device and show if there is a driver installed correctly.  The second will test hardware.  If that is successful and either ath0 or wifi0 shows a driver installed then if you know all the info of the network you are trying to connect to then run:
```
sudo ifconfig ath0 down
sudo dhclient -r ath0
sudo ifconfig ath0 up
sudo iwconfig ath0 essid "yournetworkinquotes"
sudo iwconfig ath0 key ---------------
sudo iwconfig ath0 mode Managed 
sudo dhclient ath0
```
 
Now there are variations depending on the network mainly where key is involved,  example I listed is for a WEP key(not passphrase).  To see all the options of those commands simply run:
```
man iwconfig
man ifconfig
man iwlist
man dhclient
```
so on and so on.  Good luck, hope this helps.  The above all easiest thing you could do though is back-up his files and install 8.10 Ubuntu or Kubuntu as it has a much improved network manager and I'm sure it will support the hardware right out of the box as I have a very new HP laptop with the new Atheros AR9281 with XSPAN technology and it is supported.  Let me know if there is anything more.

---

