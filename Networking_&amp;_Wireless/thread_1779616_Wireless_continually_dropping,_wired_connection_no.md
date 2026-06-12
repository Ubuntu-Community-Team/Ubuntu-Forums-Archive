---
title: "Wireless continually dropping, wired connection not detected."
date: 2011-06-10
forum: Networking &amp; Wireless
---

### Post by askates on 2011-06-10
I'm running 11.04, and I've had nothing but problems with my network connections.

It started off with the wireless connection continually dropping and reconnecting. It would do this every couple of minutes. I asked on the forum, but didn't get any help. I then just decided to keep it on an ethernet cable and use the wired connection continually.

This worked fine for a while, but eventually would randomly disconnect me, and I would have to pull the cable out, and plug it back into my laptop for it to work. My wireless was still playing up, and it started doing this thing where the wired connection would be dropped, and suddenly I wouldn't be able to find any wireless signals, until I took the ethernet cable out and plugged it back in again, and then voila, wireless networks detected.

Now, It doesn't detect a wired connection at all, despite having the ethernet cable plugged in.

I'm seriously nearing the end of my patience here. If anyone could help, it would be extremely appreciated.

Output of lspci
```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)

```Output of iwconfig
```
eth0      Link encap:Ethernet  HWaddr 00:1e:33:8e:30:12  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:43 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:282 errors:0 dropped:0 overruns:0 frame:0
          TX packets:282 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:23762 (23.7 KB)  TX bytes:23762 (23.7 KB)

wlan0     Link encap:Ethernet  HWaddr 00:21:63:d6:4c:e9  
          inet addr:192.168.1.85  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::221:63ff:fed6:4ce9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5257 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4018 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3271074 (3.2 MB)  TX bytes:765111 (765.1 KB)

```

---

### Post by askates on 2011-06-11
It still refuses to detect an ethernet cable, and my wireless is still playing up.

Bump?

---

### Post by rva1945 on 2011-12-15
> **askates said:**
> It still refuses to detect an ethernet cable, and my wireless is still playing up.

Bump?

Hi!

Did you solve the problem?

I'm having a similar problem: the wireless works ok, the notebook picks the signal, but the desktop PC, which is connected to the router via a wired connection, stopped working. I mean it worked ok for months, and since a couple of weeks, it doesn't.

The cable is ok, I tested it connecting the notebook to the router using the cable (and disabling the wireless for this purpose).

I was considering buying a USB wireless connector (TP-LINK) but according to availeble info that's not plug'n play.

I'd appreciate any help.

Robert

---

