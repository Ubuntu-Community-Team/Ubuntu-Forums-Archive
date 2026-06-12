---
title: "iwl3945 wireless speed issue"
date: 2012-04-15
forum: Networking &amp; Wireless
---

### Post by d0ser on 2012-04-15
```
wlan0     IEEE 802.11abg  ESSID:"5MMD6"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:26:62:A3:79:C2   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=64/70  Signal level=-46 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:5850   Missed beacon:0
```


```
02:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
	Subsystem: Intel Corporation PRO/Wireless 3945ABG Network Connection [8086:1000]
	Kernel driver in use: iwl3945
	Kernel modules: iwl3945
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 01)
	Subsystem: Gateway 2000 Device [107b:0690]
	Kernel driver in use: r8169
```


I have attempted to do the /etc/modprobe.d/iwl3945.conf fix where I set the option of hw_scan to false and this did nothing to help. My speeds are as low as .2mbps and ping is around 20ms according to speedtest.net. The router is running fine and I'm not being throttled by my ISP. Any ideas on how to fix this? I am running Ubuntu 11.10.

Any other info that could help, please ask.

---

