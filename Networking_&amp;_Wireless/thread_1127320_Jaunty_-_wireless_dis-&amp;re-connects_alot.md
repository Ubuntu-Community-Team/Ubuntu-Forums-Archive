---
title: "Jaunty - wireless dis-&amp;re-connects alot"
date: 2009-04-16
forum: Networking &amp; Wireless
---

### Post by detroit/zero on 2009-04-16
I just installed Jaunty Ubuntu on my acer travelmate 2480. Nm-applet keeps disconnecting and reconnecting me from my ap.

Every couple minutes, I have to stop what I'm doing and wait for the wireless to reconnect and it's a little nerve-wracking.

lspci:```

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
0a:03.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
0a:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0a:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
```iwconfig:```
ath0      IEEE 802.11g  ESSID:"XXXXXXX"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:21:29:75:8E:2A   
          Bit Rate:11 Mb/s   Tx-Power:9 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=22/70  Signal level=-70 dBm  Noise level=-92 dBm
          Rx invalid nwid:613458  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

---

### Post by Windsurfer619 on 2009-04-16
I have the same problem, and the same hardware. In fact, sometimes NetworkManager just completely dies and I have to restart it (sudo /etc/init.d/NetworkManager restart). I hope this will be fixed by the final release. These sorts of things usually are.

I should file a bug report....

---

### Post by ntos on 2009-04-16
hi guys yes Im all so having  this same problem  in jaunty and have not the same hardware but do have a atheros chip set it looks like do so this is what i do it helps a little . so pull up a terminal and enter this in.echo ath9k | sudo tee -a /etc/modules hop this help .    happy ubuntuing  ntos

---

### Post by ntos on 2009-04-16
hey I forgot to tell you need to reboot after sorry.

---

### Post by detroit/zero on 2009-04-16
> **ntos said:**
> hi guys yes Im all so having  this same problem  in jaunty and have not the same hardware but do have a atheros chip set it looks like do so this is what i do it helps a little . so pull up a terminal and enter this in.echo ath9k | sudo tee -a /etc/modules hop this help .    happy ubuntuing  ntos
That seems to help a little. I do still get the disconnects, but I notice that it seems to reconnect a little faster than it was...

Yeah, hopefully the problem is ironed out in the final release. Just a couple days to go...

---

