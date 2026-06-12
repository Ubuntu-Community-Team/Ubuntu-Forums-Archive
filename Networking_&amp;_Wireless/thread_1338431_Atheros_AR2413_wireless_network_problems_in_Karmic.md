---
title: "Atheros AR2413 wireless network problems in Karmic Koala"
date: 2009-11-26
forum: Networking &amp; Wireless
---

### Post by Mentalor on 2009-11-26
I'm using a Toshiba Satellite Pro L20 laptop, with a built-in AR2413 wireless network card.  It is a dual-boot setup of Ubuntu with Windows XP.

Wireless networking works fine under Windows and Ubuntu 9.04, but since upgrading to 9.10 I am no longer able to connect to my WPA encrypted wireless network.  If I remove encryption, I can connect OK...WPA or WEP, nothing.

I've tried installing 9.10 from scratch, installing the madwifi drivers and following many other tutorials as to how to connect Ubuntu to a wireless network.  All to no avail.

I've also installed wicd, which can see my wireless network fine (and several others), but just sits at 'Obtaining IP address...' when I try to connect to it (unless I remove encryption).

Please help.  Its driving me nuts.



ifconfig output -
```
ath0      Link encap:Ethernet  HWaddr 00:11:f5:ba:e4:b3  
          inet6 addr: fe80::211:f5ff:feba:e4b3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wifi0     Link encap:UNSPEC  HWaddr 00-11-F5-BA-E4-B3-30-30-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:23465 errors:0 dropped:0 overruns:0 frame:1384
          TX packets:29417 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:280 
          RX bytes:3727511 (3.7 MB)  TX bytes:1497712 (1.4 MB)
          Interrupt:22
```

iwconfig output -
```
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"MentalWall"  Nickname:""
          Mode:Managed  Frequency:2.452 GHz  Access Point: 00:0E:2E:54:67:54   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:162  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

lshw -C network output -
```
  *-network:1
       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 4
       bus info: pci@0000:09:04.0
       logical name: wifi0
       version: 01
       serial: 00:11:f5:ba:e4:b3
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=96 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11g
       resources: irq:22 memory:c0200000-c020ffff
```

---

### Post by drpjkurian on 2009-11-27
> **Mentalor said:**
> I'm using a Toshiba Satellite Pro L20 laptop, with a built-in AR2413 wireless network card.  It is a dual-boot setup of Ubuntu with Windows XP.

Wireless networking works fine under Windows and Ubuntu 9.04, but since upgrading to 9.10 I am no longer able to connect to my WPA encrypted wireless network.  If I remove encryption, I can connect OK...WPA or WEP, nothing.

I've tried installing 9.10 from scratch, installing the madwifi drivers and following many other tutorials as to how to connect Ubuntu to a wireless network.  All to no avail.

I've also installed wicd, which can see my wireless network fine (and several others), but just sits at 'Obtaining IP address...' when I try to connect to it (unless I remove encryption).

Please help.  Its driving me nuts.



ifconfig output -
```
ath0      Link encap:Ethernet  HWaddr 00:11:f5:ba:e4:b3  
          inet6 addr: fe80::211:f5ff:feba:e4b3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wifi0     Link encap:UNSPEC  HWaddr 00-11-F5-BA-E4-B3-30-30-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:23465 errors:0 dropped:0 overruns:0 frame:1384
          TX packets:29417 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:280 
          RX bytes:3727511 (3.7 MB)  TX bytes:1497712 (1.4 MB)
          Interrupt:22
```

iwconfig output -
```
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"MentalWall"  Nickname:""
          Mode:Managed  Frequency:2.452 GHz  Access Point: 00:0E:2E:54:67:54   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:162  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

lshw -C network output -
```
  *-network:1
       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 4
       bus info: pci@0000:09:04.0
       logical name: wifi0
       version: 01
       serial: 00:11:f5:ba:e4:b3
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=96 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11g
       resources: irq:22 memory:c0200000-c020ffff
```

Hi 
Please give a try to my thread
[http://ubuntuforums.org/showthread.php?t=1309072](http://ubuntuforums.org/showthread.php?t=1309072)

With regards
Dr Kurian

---

### Post by Mentalor on 2009-11-27
WOOHOO!  Many, many thanks drpjkurian, the instructions on your thread did the trick (after a bit of minor confusion on my part between the characters ` and ').  I also had to change the WPA Supplicant driver from MadWifi to wext (as suggested by someone in your thread).

Great job.  Thanks again.

---

### Post by drpjkurian on 2009-11-27
> **Mentalor said:**
> WOOHOO!  Many, many thanks drpjkurian, the instructions on your thread did the trick (after a bit of minor confusion on my part between the characters ` and ').  I also had to change the WPA Supplicant driver from MadWifi to wext (as suggested by someone in your thread).

Great job.  Thanks again.

Hi Mentalor

You are most welcome.
I am happy to know that your wireless is back to life again

With regards
Dr Kurian

---

