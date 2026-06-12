---
title: "Xubuntu 8.10 64bit, Intel 5300agn WIFI Problems"
date: 2009-01-22
forum: Networking &amp; Wireless
---

### Post by jonny2040 on 2009-01-22
Hi,

I just bought a new laptop and have decided to finally try make the switch to linux. I instantly fall into problems with the WIFI drivers. Irritatingly I thought I had this covered with intel wifi but I suppose not. I`m running Xubuntu 8.10 64 bit ed. I think it finds the wireless card fine but I can`t find any networks. What follows is alot of terminal info that I hope might help. If I miss anything let me know.

I know there are other threads on this but I have tried what is in them to no avail.

Thanks for your help,
jonny

lspci -vv
```

05:00.0 Network controller: Intel Corporation PRO/Wireless 5300 AGN [Shiloh] Network Connection
	Subsystem: Intel Corporation Device 1001
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 2298
	Region 0: Memory at febfe000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: iwlagn
	Kernel modules: iwlagn

```
```

lok@Loks-Laptop:~$ iwconfig wlan0
wlan0     IEEE 802.11abgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=14 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

```
lok@Loks-Laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

pan0      Interface doesn't support scanning.
```

---

### Post by jonny2040 on 2009-01-24
You know those days you waste trying to fix something to no avail. Only to boot up a day later and find you computer working again.....

Turns out I installed a few other distros to try get it working, found that Mint XFCE worked. Thought it might be the WCID instead of NetworkManager. So reinstalled Xubuntu to try put WCID on instead. Then low and behold, there was my netword. Bloody turn coat.

Oh well, ignore me, problem fixed.

---

