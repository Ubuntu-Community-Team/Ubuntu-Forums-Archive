---
title: "lost wifi after upgrade to 11.04 (Acer Aspire 3500)"
date: 2011-06-18
forum: Networking &amp; Wireless
---

### Post by maphew on 2011-06-18
Hi Folks,

I have an Acer Aspire 3500 laptop which has been running Ubuntu since 9.04 or thereabouts. When I upgraded to 11.04 the wifi stopped working reliably for a time ([http://ubuntuforums.org/showpost.php?p=10879733&postcount=1](http://ubuntuforums.org/showpost.php?p=10879733&postcount=1)), and now doesn't work at all. In the toolbar applet dropdown there are no available wireless networks shown. If use "connect to hidden" and type in the appropriate details the icon changes to a pulsing wave and after a minute or so shows the "wireless connection requires a password" dialog. Lather, rinse, repeat indefinitely. For a time (see prev. link) if I just kept trying it would sometimes show networks, and sometimes connect. That is no longer true. 

I've verified the hardware is good. Booting from a sysrescue cd the wifi "just works": I click on the network applet, see a half dozen networks to choose from, select mine, enter password, surf the net. 

As per instructions in "HOWTO post a Wireless issue (ticket)", system details follow. Your assistance is greatly appreciated; I've wasted far more hours on this than I care to think about!

-matt
-----
Acer Aspire 3500 (Model 3502LCI, Mfg. Date 0504)

```

$ lspci |grep Ethernet
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:0b.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)

```
```

$ ifconfig
...snip...
wlan0     Link encap:Ethernet  HWaddr 00:0e:9b:a4:9f:cf  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```
```

$ iwconfig wlan0
wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```
```

$ lsmod | grep ath
ath5k                 144412  0 
ath                    19141  1 ath5k
mac80211              257001  1 ath5k
cfg80211              156212  3 ath5k,ath,mac80211

```
```

$ dmesg |grep ath
...snip...
[   15.649562] ath5k 0000:00:0b.0: enabling device (0010 -> 0012)
[   15.649594] ath5k 0000:00:0b.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   15.649676] ath5k 0000:00:0b.0: registered as 'phy0'
[   16.486517] ath: EEPROM regdomain: 0x63
[   16.486522] ath: EEPROM indicates we should expect a direct regpair map
[   16.486529] ath: Country alpha2 being used: 00
[   16.486532] ath: Regpair used: 0x63
[   16.524368] ath5k phy0: Atheros AR2413 chip found (MAC: 0x78, PHY: 0x45)

```
```

$ sudo lshw -C network
    *-network:0             
       description: Ethernet interface
       ...snip...
    *-network:1
       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: b
       bus info: pci@0000:00:0b.0
       logical name: wlan0
       version: 01
       serial: 00:0e:9b:a4:9f:cf
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=2.6.38-8-generic firmware=N/A latency=168 link=no maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:e2010000-e201ffff

```
```

$ iwlist scan 
...snip...
wlan0     No scan results

```
```

$ lsb_release -d
Description:	Ubuntu 11.04

```
```

$ uname -mr
2.6.38-8-generic i686

```
```

$ sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                                                    [ OK ]

```

---

