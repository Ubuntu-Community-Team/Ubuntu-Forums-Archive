---
title: "After 9.10 upgrade, internet stopped working.."
date: 2010-02-21
forum: Networking &amp; Wireless
---

### Post by MindFusion on 2010-02-21
I'm currently running Ubuntu 9.10.
After I updated to 9.10, my wireless connection stoppped working. 
I can access the network but I get no response or what so ever in my browser.
Downloading language support or any software doesn't work either.

Haven't changed anything to my settings and checked the router. Router works just fine.

---

### Post by KaiJordanDay on 2010-02-21
Can you connect to any other PCS on your Network?

Is it just internet access that is not working?

---

### Post by MindFusion on 2010-02-21
I'm sorry, with network, i meant wireless network, not as in: a network of other pc's with shared folders.

If you were meaning to ask if other pc's can access the internet then yes, i am currently using Windows on another pc and it works fine.

---

### Post by KaiJordanDay on 2010-02-21
Whats your Terminal output of:

> lspci -v | less

and

> iwconfig

---

### Post by MindFusion on 2010-02-21
output lspci -v | less:

```
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03) 
Subsystem: Toshiba America Info Systems Device ff10 
Flags: bus master, fast devsel, latency 0 
Capabilities: <access denied> 
Kernel modules: intel-agp 

00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 03) 
Flags: bus master, fast devsel, latency 0 
Bus: primary=00, secondary=01, subordinate=01, sec-latency=0 
I/O behind bridge: 0000c000-0000dfff 
Memory behind bridge: c0000000-cfffffff 
Prefetchable memory behind bridge: 90000000-9fffffff 
Capabilities: <access denied> 
Kernel driver in use: pcieport-driver 
Kernel modules: shpchp 

00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04) 
Flags: bus master, fast devsel, latency 0 
Bus: primary=00, secondary=02, subordinate=02, sec-latency=0 
I/O behind bridge: 0000a000-0000bfff 
Memory behind bridge: bc000000-bfffffff 
Prefetchable memory behind bridge: 000000008c000000-000000008fffffff 
Capabilities: <access denied> 
Kernel driver in use: pcieport-driver 
Kernel modules: shpchp 

00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04) 
Flags: bus master, fast devsel, latency 0 
Bus: primary=00, secondary=03, subordinate=03, sec-latency=0 
I/O behind bridge: 00008000-00009fff 
Memory behind bridge: b8000000-bbffffff 
Prefetchable memory behind bridge: 0000000088000000-000000008bffffff 
Capabilities: <access denied> 
Kernel driver in use: pcieport-driver 
Kernel modules: shpchp 

00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04) 
Subsystem: Toshiba America Info Systems Device ff10 
Flags: bus master, medium devsel, latency 0, IRQ 10 
I/O ports at 1200 [size=32] 
```

output iwconfig

```
lo no wireless extensions. 

eth0 no wireless extensions. 

eth1 IEEE 802.11g ESSID:"@Value" 
Mode:Managed Frequency:2.437 GHz Access Point: 00:15:E9:25:FC:E8 
Bit Rate:54 Mb/s Tx-Power=20 dBm Sensitivity=8/0 
Retry limit:7 RTS thr:off Fragment thr:off 
Power Management:off 
Link Quality=68/100 Signal level=-46 dBm Noise level=-86 dBm 
Rx invalid nwid:0 Rx invalid crypt:8 Rx invalid frag:0 
Tx excessive retries:0 Invalid misc:0 Missed beacon:27
```

---

### Post by KaiJordanDay on 2010-02-21
I Don't think, its even recognising your wireless card.

---

### Post by northd_tech on 2010-02-21
Can you copy/paste and post the output of the following commands when you enter them in a terminal:

```

lspci 

lsmod

sudo lshw -C network

ifconfig

iwconfig
```

---

### Post by MindFusion on 2010-02-23
Sorry I didn't reply but i took the laptop to school and there it DID work on that network... i'm clueless.

---

