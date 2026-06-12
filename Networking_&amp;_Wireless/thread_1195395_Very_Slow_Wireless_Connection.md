---
title: "Very Slow Wireless Connection"
date: 2009-06-23
forum: Networking &amp; Wireless
---

### Post by rnschmidt on 2009-06-23
Hello, 

I just installed Ubuntu 9.04 and just about everything is working fine with the exception of my wireless internet connection.  I am able to see all of the wireless networks in range and connect to mine, however, once connected the internet is VERY slow.  After searching these forums I saw that the previous advice was to change the bit rate to 5.5M, 11M, 24M or 54M.  I tried all of these rates and nothing changed.  

Here is an lspci output:
```

00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] (rev 01)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5702X Gigabit Ethernet (rev 02)
02:01.0 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
02:01.1 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
```And here is my iwconfig output:

```

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"rns"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1D:7E:9A:95:21   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=85/100  Signal level:-42 dBm  Noise level=-64 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
```All help is greatly appreciated.


Thanks, 
Rob

---

### Post by s3MA00RRNY on 2009-06-23
Go to System > Admin > Hardware Drivers. Install the Broadcom STA driver. Should speed it right up.

---

### Post by rnschmidt on 2009-06-23
The only driver I can activate is the Broadcom B43legacy wireless driver, which I already have done. This allowed me to see wireless networks wheras before this driver was installed I couldn't even get a signal.  Now I can connect, but it's super slow.

Is there something I am missing here?

---

### Post by rnschmidt on 2009-06-24
bump

---

