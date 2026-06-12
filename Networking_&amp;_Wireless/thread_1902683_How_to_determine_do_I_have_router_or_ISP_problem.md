---
title: "How to determine do I have router or ISP problem?"
date: 2011-12-31
forum: Networking &amp; Wireless
---

### Post by NexusStar on 2011-12-31
I recently changed my router at home with new one due to some VPN problems with the old one.
The new router is TP-LINK TL-WR1043ND and is still with its original firmware :) But I now experience from time to time slow connections and ISP deny that it have anything to do with them so how could I determine do I have problem with the hardware at home or all come from the provider. 
Here is some information about my system:
```

>>iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"Nikol"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: F8:D1:11:24:B4:A4   
          Bit Rate=48 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=58/70  Signal level=-52 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:62  Invalid misc:258   Missed beacon:0

``` 
```
 >> uname -r
3.0.0-14-generic

```
```
>>lspci -v
06:05.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
	Subsystem: AMBIT Microsystem Corp. TravelMate 2410
	Flags: bus master, fast devsel, latency 32, IRQ 21
	Memory at b0100000 (32-bit, non-prefetchable) [size=8K]
	Kernel driver in use: b43-pci-bridge
	Kernel modules: ssb

06:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
	Subsystem: Acer Incorporated [ALI] Device 006a
	Flags: bus master, medium devsel, latency 32, IRQ 20
	I/O ports at 3000 [size=256]
	Memory at b0102000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: 8139too
	Kernel modules: 8139too, 8139cp

```

---

