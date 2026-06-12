---
title: "EeePC Ubuntu Natty Slow Internet after Reinstall"
date: 2011-06-16
forum: Networking &amp; Wireless
---

### Post by Mieum on 2011-06-16
I had a dual install of Windows and Ubuntu working for a good week, then I reinstalled Ubuntu, completely wiping the machine. 

My connection is greatly reduced--updates take hours to install, but internet surfs okay.

Did some drivers get messed up or something? I'm new to Ubuntu, so I don't know my way around really. But here's some info that might be useful:

```


mieum@mieum-1000HE:~$ sudo ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:24:8c:29:5e:4b  
          inet addr:59.17.55.227  Bcast:59.17.55.255  Mask:255.255.255.224
          inet6 addr: fe80::224:8cff:fe29:5e4b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7600 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3586 errors:0 dropped:0 overruns:0 carrier:2
          collisions:0 txqueuelen:1000 
          RX bytes:3788675 (3.7 MB)  TX bytes:1387037 (1.3 MB)
          Interrupt:43 

mieum@mieum-1000HE:~$ rfkill unblock all
mieum@mieum-1000HE:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:24:8c:29:5e:4b  
          inet addr:59.17.55.227  Bcast:59.17.55.255  Mask:255.255.255.224
          inet6 addr: fe80::224:8cff:fe29:5e4b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8753 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4189 errors:0 dropped:0 overruns:0 carrier:2
          collisions:0 txqueuelen:1000 
          RX bytes:4307733 (4.3 MB)  TX bytes:1458996 (1.4 MB)
          Interrupt:43 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:15:af:e0:3e:e6  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

mieum@mieum-1000HE:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=17 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```

This is really frustrating, but hopefully someone has some tips...I know this is a recurring problem for folks with Asus~~

Mahalo~~~

---

### Post by mikewhatever on 2011-06-16
Updates may download slowly because of a slow or overloaded mirror, and not your internet connection. Try testing your down/up speeds with [http://speedtest.net/](http://speedtest.net/).

PS: If you want help with drivers, it makes sense mentioning which driver you use.;)

---

### Post by Mieum on 2011-06-16
my speed test says a ping of 356ms, download speed of 3.56mbps, upload of .35mbps. 

I tested just the other day and my ping was 5ms, down ~50mbps, up ~50mbps. korea has wicked fast internet, but since re-installing natty I'm not able to take advantage of that whatsoever.

I'm not sure how to check my drivers~~~ i'm not totally sure if that is the problem or not...it's just that something changed once I reinstalled.

---

### Post by Mieum on 2011-06-16
Here is about drivers and other info:

```
NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            ATL1E
  State:             connected
  Default:           yes
  HW Address:        00:24:8C:29:5E:4B

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         59.17.55.227
    Prefix:          27 (255.255.255.224)
    Gateway:         59.17.55.254

    DNS:             168.126.63.1
    DNS:             168.126.63.2


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             disconnected
  Default:           no
  HW Address:        00:15:AF:E0:3E:E6

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    jino5845:        Infra, 00:26:66:59:DD:60, Freq 2412 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    KT_WLAN_9841:    Infra, 06:1F:1F:C8:FB:49, Freq 2412 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    Unicorn:         Infra, 00:B0:0C:00:A7:48, Freq 2462 MHz, Rate 54 Mb/s, Strength 34
    iptime(boram):   Infra, 00:08:9F:50:80:FB, Freq 2417 MHz, Rate 54 Mb/s, Strength 34
    QNICS-AP1:       Infra, 00:16:01:AE:BC:E3, Freq 2462 MHz, Rate 54 Mb/s, Strength 48 WEP
    U+NetD17B:       Infra, 00:40:5A:A2:D1:79, Freq 2417 MHz, Rate 54 Mb/s, Strength 34 WPA2
    HelloWireless:   Infra, 0A:0E:DC:5D:6C:72, Freq 2427 MHz, Rate 54 Mb/s, Strength 28 WEP
    youtakit01:      Infra, 00:08:9F:AC:BE:C4, Freq 2462 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2
    KT_WLAN_19EE:    Infra, 00:1F:96:19:4E:E5, Freq 2437 MHz, Rate 54 Mb/s, Strength 38 WPA WPA2
    anygate:         Infra, 00:02:A8:9D:CE:B4, Freq 2437 MHz, Rate 54 Mb/s, Strength 37
    HelloWireless:   Infra, 00:1D:33:03:DF:85, Freq 2412 MHz, Rate 54 Mb/s, Strength 44 WEP
    minih:           Infra, 00:08:9F:40:4B:68, Freq 2412 MHz, Rate 54 Mb/s, Strength 45 WEP
    HelloSpeed:      Infra, 00:1D:33:03:DF:83, Freq 2412 MHz, Rate 54 Mb/s, Strength 45 WPA WPA2
    KT_WLAN_A329:    Infra, 00:17:C3:A3:22:A1, Freq 2412 MHz, Rate 54 Mb/s, Strength 50 WPA WPA2
    KT_WLAN_980D:    Infra, 06:1F:1F:D5:BA:B5, Freq 2462 MHz, Rate 54 Mb/s, Strength 50 WPA WPA2
    KT_WLAN_9FD5:    Infra, 00:17:C3:9F:BD:55, Freq 2432 MHz, Rate 54 Mb/s, Strength 68 WPA WPA2


```

---

### Post by mikewhatever on 2011-06-16
Very impressive, you must be paying a fortune for 50mbps. ;)
Anyway, to identify the hardware and the driver, post the output of **lshw -C network**.

---

### Post by Mieum on 2011-06-16
I'm not sure who's paying the bill for the connection--I just plugged in =b

```
*-network               
       description: Ethernet interface
       product: AR8121/AR8113/AR8114 Gigabit or Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: b0
       serial: 00:24:8c:29:5e:4b
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI duplex=full firmware=L1e ip=59.17.55.227 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:43 memory:fbfc0000-fbffffff ioport:ec00(size=128)
  *-network
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: 01
       serial: 00:15:af:e0:3e:e6
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.38-8-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:19 memory:fbef0000-fbefffff

```

---

### Post by Mieum on 2011-06-16
By the way, I did change the software source for the software center, which did speed things up, however, my total connection is still hugely reduced from what it was before the reinstall =\

---

### Post by mikewhatever on 2011-06-17
> **Mieum said:**
> I'm not sure who's paying the bill for the connection--I just plugged in =b

...


If that's the case, do you know how many more people have also plugged in? Obviously, if a dozen share a 50mbps connection, each one can't expect to get 50mbps on a speed test.

---

### Post by Ace..... on 2011-06-17
Hmmmm......
This situation looks just a little bit like mine.

[http://ubuntuforums.org/showthread.php?t=1784617](http://ubuntuforums.org/showthread.php?t=1784617)

I wonder...just a thought... but how was your first ubuntu installed?
As per my thread starter - i had a good connection then after a full install into partitions, the speed collapsed.

---

### Post by Mieum on 2011-06-17
I have checked things out a little more, and I'm starting to think that maybe nothing changed after my reinstall. I had a chance to do speedtest on my friend's computer using the same connection and the results were similar. I also just tried again on my computer this morning and the results were closer to 'normal.'

What originally caught my attention was the ridiculously slow update and software downloads, but after changing the mirror the speed has increased.

Torrents download fine even. I have a feeling that bandwidth might fluctuate here. I'm in Korea now (and I'm not Korean) so I'm not exactly sure what is going on or how it works around here.

---

