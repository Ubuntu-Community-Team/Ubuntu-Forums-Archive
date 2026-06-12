---
title: "Wifi Problem Ralink RT2700E (with Lucid)"
date: 2011-06-28
forum: Networking &amp; Wireless
---

### Post by camilomusic on 2011-06-28
Hi everyone.

I'm relatively new to Ubuntu and am experiencing a problem that I haven't been able to solve yet. Been looking around and there's no threads (to my knowledge) that treat with my specific situation:

I'm using Ubuntu 10.04 and I can't get the wireless to work properly. When I log in for the first time it connects just fine, but it only lasts for about five minutes, and then the connection drops down. Then it asks me for the wifi password and I type it (I'm 100% sure I've typed it right); it tries to connect again, and then again I get asked for the password. That goes on forever, and the connection never comes back.

The internet is working fine, as I can use it with the cable. Also, the wifi works OK with Ubuntu 9.10. I'm using a Packard Bell Easynote NJ32, and my wireless card is Ralink RT2700E. 

Here's the info that gets displayed with lspci (in case it may be needed):

```
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:04.0 PCI bridge: ATI Technologies Inc Device 7914
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
02:00.0 Network controller: RaLink RT2860
04:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)

```

One more thing. My password is encrypted in WPA.

¡Thank you!

[email]camilomusic71@gmail.com[/email]

---

### Post by chili555 on 2011-06-28
Dr. Chili takes his stethoscope from his lab coat pocket and says, please open a terminal and run and post:```
lsmod | grep rt2
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by camilomusic on 2011-06-28
Here it is doc:

camilo@camilo-laptop:~$ lsmod | grep rt2
rt2860sta             481561  1

---

### Post by chili555 on 2011-06-28
Hmmm. Nothing wrong with that as there often is. Let's now see:```
dmesg | grep -i rt2
```So far, I see nothing wrong that we can fix.

---

