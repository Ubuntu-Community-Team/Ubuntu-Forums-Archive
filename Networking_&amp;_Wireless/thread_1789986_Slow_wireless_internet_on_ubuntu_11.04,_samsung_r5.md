---
title: "Slow wireless internet on ubuntu 11.04, samsung r530 with atheros AR9285"
date: 2011-06-24
forum: Networking &amp; Wireless
---

### Post by Rbazley on 2011-06-24
Hey, I'm having an issue here, I'm getting really slow speeds on my laptop when using the wireless, I did a speed test and it came out with 2mb/s, but when I plug it into the router it goes up to 13mb/s. Many pages also freeze and need refreshing.
My laptop has an Atheros AR9285.

ifconfig
```
wlan0     Link encap:Ethernet  HWaddr 78:e4:00:35:72:6a  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::7ae4:ff:fe35:726a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:40646 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29990 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:50617678 (50.6 MB)  TX bytes:7260210 (7.2 MB)
```iwconfig
```
wlan0     IEEE 802.11bgn  ESSID:"TALKTALK-92B6F6"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:26:5A:92:B6:F6   
          Bit Rate=135 Mb/s   Tx-Power=17 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=48/70  Signal level=-62 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:345   Missed beacon:0
```Not sure what else is needed but any help would be appreciated, I'm not too great at the moment.

---

### Post by Growlor on 2011-07-02
I suspect this is part of a known issue (I found this thread while searching to see if they have published a "real" fix for it.) In this thread, [http://ubuntuforums.org/showthread.php?t=1688173](http://ubuntuforums.org/showthread.php?t=1688173) , there is a work-around for it listed (disabling the hardware encryption or something like that.) I am not using the workaround as I have a rather long cable I can use as a backup, but it has occurred for me since 11.04 came out, so am disappointed it's not been fixed in an update yet.

---

### Post by Growlor on 2011-07-17
Looks like the latest update (I think they included a kernel update???) resolved this for me.

---

### Post by saldarji on 2011-07-26
I've enabled the proposed updates for Natty and am trying the latest kernels (2.6.38-11-generic-pae), but I'm still seeing slow speeds (~1.5M).  Windows on the same machine speedtests at ~14M. I've tried some of the workarounds in other posts, such as the nohwcrypt flag, but I have not been successful. 

It seems as if there are a few bugs filed around these wireless issues.

```
03:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
	Subsystem: Accton Technology Corporation Device e811
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at ff500000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: [40] Power Management version 3
	Capabilities: [50] MSI: Enable- Count=1/1 Maskable- 64bit-
	Capabilities: [60] Express Legacy Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [140] Virtual Channel
	Capabilities: [160] Device Serial Number 00-15-17-ff-ff-24-14-12
	Capabilities: [170] Power Budgeting <?>
	Kernel driver in use: ath9k
	Kernel modules: ath9k
```

Found a workaround: I'm using a Cisco WRT150N, and I changed the setting on it to bg-mixed.  Apparently, wireless N was the culprit.  It makes the situation liveable until a kernel/ath9k fix is released.

---

### Post by shadysamir on 2011-08-23
I had this problem right after upgrading to kernel 2.6.38-11-generic. Booting into earlier kernel (natty default one, since that was my first update) solves the problem

---

