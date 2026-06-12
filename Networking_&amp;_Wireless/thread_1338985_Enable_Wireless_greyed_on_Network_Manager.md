---
title: "Enable Wireless greyed on Network Manager"
date: 2009-11-27
forum: Networking &amp; Wireless
---

### Post by JohnnythePirate on 2009-11-27
Similar problem here. I've been golden with my wireless since 9.04, and now I disabled it via right-clicking the network manager, and the checkbox is greyed out. I have a wireless on/off switch (LED toggle), but it's been off (logged off blue, logged on orange, has been ever since) since I installed 8.10 when that came out. 

Specs: Presario C700
lspci shows
```
01:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
        Subsystem: Hewlett-Packard Company Device 137a
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at 91300000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: [40] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [60] Express Legacy Endpoint, MSI 00
        Capabilities: [90] MSI-X: Enable- Mask- TabSize=1
        Capabilities: [100] Advanced Error Reporting <?>
        Capabilities: [140] Virtual Channel <?>
        Kernel driver in use: ath5k
        Kernel modules: ath5k

02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Hewlett-Packard Company Device 30d9
        Flags: bus master, medium devsel, latency 64, IRQ 16
        I/O ports at 1000 [size=256]
        Memory at 91200000 (32-bit, non-prefetchable) [size=256]
        Capabilities: [50] Power Management version 2
        Kernel driver in use: 8139too
        Kernel modules: epl, 8139too, 8139cp

```iwconfig shows
```
lo        no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

```ifconfig shows
```
eth0      Link encap:Ethernet  HWaddr 00:1e:ec:22:ac:6b  
          inet addr:192.168.1.112  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:ecff:fe22:ac6b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5537 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5051 errors:0 dropped:0 overruns:0 carrier:0
          collisions:1946 txqueuelen:1000 
          RX bytes:5279250 (5.2 MB)  TX bytes:934860 (934.8 KB)
          Interrupt:16 Base address:0x1000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

```Please help me.

---

