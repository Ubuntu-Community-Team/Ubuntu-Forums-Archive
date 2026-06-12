---
title: "Broadcom BCM4306 was working but quit. Any ideas?"
date: 2008-12-06
forum: Networking &amp; Wireless
---

### Post by JAYCEE1 on 2008-12-06
My Dell Latitude C400 (7.04 Feisty) has a BCM4306 Broadcom inside. I had it working for a good while but then it quit on me. It still shows up under network manager with good signal strength, but when I try to join, it just sets there spinning. I never get a connection.

sudo lshw -C network
```

  *-network:0             
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth2
       version: 78
       serial: 00:06:5b:b6:4c:e5
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=full latency=32 link=yes maxlatency=10 mingnt=10 multicast=yes port=MII speed=100MB/s
       resources: ioport:ec80-ecff iomemory:fafffc00-fafffc7f irq:11
  *-network:1 DISABLED
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@02:03.0
       logical name: wlan0
       version: 03
       serial: 00:90:96:f8:64:2a
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper driverversion=1.38 firmware=Linksys,07/17/2003, 3.30.15.0 latency=32 link=yes multicast=yes wireless=IEEE 802.11g
       resources: iomemory:faffc000-faffdfff irq:11

```


ifconfig 
```

eth2      Link encap:Ethernet  HWaddr 00:06:5B:B6:4C:E5  
          inet addr:192.168.0.5  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::206:5bff:feb6:4ce5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:2150 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1834 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2348108 (2.2 MiB)  TX bytes:285068 (278.3 KiB)
          Interrupt:11 Base address:0x6c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:86 errors:0 dropped:0 overruns:0 frame:0
          TX packets:86 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7502 (7.3 KiB)  TX bytes:7502 (7.3 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:90:96:F8:64:2A  
          inet6 addr: fe80::290:96ff:fef8:642a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:85 errors:0 dropped:0 overruns:0 frame:0
          TX packets:84 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:16347 (15.9 KiB)  TX bytes:8846 (8.6 KiB)
          Interrupt:11 Memory:faffc000-faffe000 



```


iwconfig
```

lo        no wireless extensions.

eth2      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"NETGEAR"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:09:5B:FA:F1:D6   
          Bit Rate=54 Mb/s   Tx-Power:14 dBm   
          RTS thr=2347 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:84/100  Signal level:-42 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```



ndiswrapper -l
```

bcmwl5 : driver installed
        device (14E4:4320) present (alternate driver: bcm43xx)

```


I noticed Network 1 is shown as disabled so I went into the BIOS to enable it. I couldn't find Wifi enable/disable in the BIOS. So I rebooted and ran sudo lshw -C network again and it no longer shows disabled:

```

  *-network:0             
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth2
       version: 78
       serial: 00:06:5b:b6:4c:e5
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=full ip=192.168.0.5 latency=32 link=yes maxlatency=10 mingnt=10 multicast=yes port=MII speed=100MB/s
       resources: ioport:ec80-ecff iomemory:fafffc00-fafffc7f irq:11
  *-network:1
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@02:03.0
       logical name: wlan0
       version: 03
       serial: 00:90:96:f8:64:2a
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper driverversion=1.38 firmware=Linksys,07/17/2003, 3.30.15.0 latency=32 link=yes multicast=yes wireless=IEEE 802.11g
       resources: iomemory:faffc000-faffdfff irq:11

```


I've gone through several of the BCM43xx fixes but none has done any good. Any ideas?

Thanks!

---

### Post by superprash2003 on 2008-12-06
have you tried using static ip?? or connecting manually?? instead of using roaming mode..[http://prash-babu.blogspot.com/2008/10/wifi-tip-always-better-to-disable.html](http://prash-babu.blogspot.com/2008/10/wifi-tip-always-better-to-disable.html) you could either set it to DHCP , if that doesnt work choose static and try by entering static ip

---

### Post by JAYCEE1 on 2008-12-07
> **superprash2003 said:**
> have you tried using static ip?? or connecting manually?? instead of using roaming mode..[http://prash-babu.blogspot.com/2008/10/wifi-tip-always-better-to-disable.html](http://prash-babu.blogspot.com/2008/10/wifi-tip-always-better-to-disable.html) you could either set it to DHCP , if that doesnt work choose static and try by entering static ip

Thanks for that easy trick superprash2003. It didn't work but I had not tried it before.

When I disabled roaming, I was no longer able to see my network under Network Manager. Wireless networks went completely away. So I then went back to roaming mode. My wireless network came back AND I was finally able to join the wireless network. I was not able to load a webpage or ping google even though my signal strength was in the high-nineties to 100%.

Another strange thing is that network manager shows both my wired network and my wireless network connected at the same time. (I have a dot next to both networks under Network Manager.) 

I ran these when I was joined to the wireless network "NETGEAR."

iwconfig
```

lo        no wireless extensions.

eth2      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"NETGEAR"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:09:5B:FA:F1:D6   
          Bit Rate=54 Mb/s   Tx-Power:14 dBm   
          RTS thr=2347 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:100/100  Signal level:-27 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

 sudo lshw -C network
```

Password:
  *-network:0             
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth2
       version: 78
       serial: 00:06:5b:b6:4c:e5
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=half latency=32 link=no maxlatency=10 mingnt=10 multicast=yes port=MII speed=10MB/s
       resources: ioport:ec80-ecff iomemory:fafffc00-fafffc7f irq:11
  *-network:1
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@02:03.0
       logical name: wlan0
       version: 03
       serial: 00:90:96:f8:64:2a
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper driverversion=1.38 firmware=Linksys,07/17/2003, 3.30.15.0 latency=32 link=yes multicast=yes wireless=IEEE 802.11g
       resources: iomemory:faffc000-faffdfff irq:11

```


ifconfig -a
```

 
eth2      Link encap:Ethernet  HWaddr 00:06:5B:B6:4C:E5  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0xec00 

eth2:avah Link encap:Ethernet  HWaddr 00:06:5B:B6:4C:E5  
          inet addr:169.254.8.136  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:11 Base address:0xec00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:194 errors:0 dropped:0 overruns:0 frame:0
          TX packets:194 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:17050 (16.6 KiB)  TX bytes:17050 (16.6 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:90:96:F8:64:2A  
          inet6 addr: fe80::290:96ff:fef8:642a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:60 (60.0 b)  TX bytes:2340 (2.2 KiB)
          Interrupt:11 Memory:faffc000-faffe000 



```

ping google.com
```

ping: unknown host google.com

```

What would cause this?

Thanks!

---

### Post by Ayuthia on 2008-12-07
By any chance, have you checked your router to see if anything changed?  Or have you tried resetting your router to see if the router was having problems?

---

### Post by JAYCEE1 on 2008-12-07
> **Ayuthia said:**
> By any chance, have you checked your router to see if anything changed?  Or have you tried resetting your router to see if the router was having problems?

I restarted the router, and I have another wireless computer connected through the same router.

I was going to try a Live USB with 8.10 on it but the Dell C400 BIOS doesn't allow booting from a USB. (The computer has no CD/DVD.) 

I'm still stuck.

---

### Post by kevdog on 2008-12-07
Are you running encryption on the router?

What about 

sudo iwlist wlan0 scan

---

### Post by superprash2003 on 2008-12-08
when you disable roaming mode , you wont find the wifi networks when you click on the network symbol in the desktop . .you need to open your network manager and select it manually and then type in ip manually.. YOur wifi router isnt giving you an ip address.. your wlan0 isnt getting an ip.. which is why i think you arent able to get internet access..

---

