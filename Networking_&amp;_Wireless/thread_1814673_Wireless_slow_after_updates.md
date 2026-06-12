---
title: "Wireless slow after updates"
date: 2011-07-29
forum: Networking &amp; Wireless
---

### Post by aikakira on 2011-07-29
Hello!

Im new to the forum and linux world so please go easy on me ^^!

Basically Ive been using Ubuntu 10.04 Lucid for a while now on my netbook (samsung NC10) been flawless and fast. After the updates earlier this evening (someone tell me where I can find a log of recent updates? =D) my wireless has been acting up. It's turned painfully slowly when im next to the router and when im further away it barely connects! Even if it does I cant expect a webpage to load either.

Heres some information that may be of use:

sudo lspci -v

02:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
	Subsystem: Askey Computer Corp. Device 7131
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at f0100000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: [40] Power Management version 2
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Capabilities: [60] Express Legacy Endpoint, MSI 00
	Capabilities: [90] MSI-X: Enable- Mask- TabSize=1
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [140] Virtual Channel <?>
	Kernel driver in use: ath5k
	Kernel modules: ath5k


sudo iwconfig:


wlan0     IEEE 802.11bg  ESSID:"half baked!"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:26:44:59:A2:43   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:7D58-EEF7-02
          Power Management:off
          Link Quality=39/70  Signal level=-71 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


Thank you for your help guys!

---

### Post by aikakira on 2011-07-30
Hey guys! 

I just looked through my update history, seems like the kernel isnt to blame. Update manager updated libsoup and libsoup-gnome which caused this problem for me.

I just downgraded back to the version and the speed & connectivity seems to have come back now.

---

