---
title: "Sitecom Wl-150 v1 001"
date: 2006-06-15
forum: Networking &amp; Wireless
---

### Post by mettallicat on 2006-06-15
I bought one pccard Sitecom WL-150 v1 001    
Ubuntu recognizes as being a Ralink (ra0) it find the Point Access, but don't obtains any IP. 

```

ricardo@Athenas:~$ lspci
0000:00:00.0 Host bridge: Intel Corporation 82845 845 (Brookdale) Chipset Host Bridge (rev 04)
0000:00:01.0 PCI bridge: Intel Corporation 82845 845 (Brookdale) Chipset AGP Bridge (rev 04)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 05)
0000:00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 05)
0000:00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 (rev 05)
0000:00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 05)
0000:00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus (rev 05)
0000:00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #2) (rev 05)
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio (rev 05)
0000:00:1f.6 Modem: Intel Corporation 82801BA/BAM AC'97 Modem (rev 05)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY
0000:02:00.0 CardBus bridge: O2 Micro, Inc. OZ6933/711E1 CardBus/SmartCardBus Controller (rev 01)
0000:02:00.1 CardBus bridge: O2 Micro, Inc. OZ6933/711E1 CardBus/SmartCardBus Controller (rev 01)
0000:02:08.0 Ethernet controller: Intel Corporation 82801BA/BAM/CA/CAM Ethernet Controller (rev 03)
0000:02:0a.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
0000:03:00.0 Network controller: RaLink: Unknown device 0401

```

```

ricardo@Athenas:~$ lspci -n
0000:00:00.0 0600: 8086:1a30 (rev 04)
0000:00:01.0 0604: 8086:1a31 (rev 04)
0000:00:1e.0 0604: 8086:244e (rev 05)
0000:00:1f.0 0601: 8086:2440 (rev 05)
0000:00:1f.1 0101: 8086:244b (rev 05)
0000:00:1f.2 0c03: 8086:2442 (rev 05)
0000:00:1f.3 0c05: 8086:2443 (rev 05)
0000:00:1f.4 0c03: 8086:2444 (rev 05)
0000:00:1f.5 0401: 8086:2445 (rev 05)
0000:00:1f.6 0703: 8086:2446 (rev 05)
0000:01:00.0 0300: 1002:4c59
0000:02:00.0 0607: 1217:6933 (rev 01)
0000:02:00.1 0607: 1217:6933 (rev 01)
0000:02:08.0 0200: 8086:2449 (rev 03)
0000:02:0a.0 0c00: 104c:8023
0000:03:00.0 0280: 1814:0401

```

So will ndiswarpper works ? How can i tell ubuntu use ndiswarpper insted Ralink driver.

---

