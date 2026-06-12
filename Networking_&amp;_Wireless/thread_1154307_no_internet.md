---
title: "no internet"
date: 2009-05-09
forum: Networking &amp; Wireless
---

### Post by mold on 2009-05-09
so i tried to finally set up my wireless internet on my inspiron 1521 with ubuntu 8.10 yesterday i upgraded to the new 9.04 thinking there would be something new that would make it easier to connect but nothing.
 so i find this [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff) and do all the steps  (2x)
 now i have no ehternet connection or wireless on my laptop!!

when i look at 'connection properties' on the taskbar  the only connection in the drop down menu is 'lo' and the status is idle with 44 packets sent and receieved:confused: at one point i remember it haveing eth0 and wlan0 before following the  tutorial!

_iwconfig_
lo                  no wireless extensions.

eth0               no wireless extensions.

wmaster0       no wireless extensions.

wlan0             IEEE 802.11bg  ESSID:" "
                     Mode:Managed   Frequency:2.412GHz  Access point: Not- Associated
                     Tx-Power=20 dBm
                     Retry min limit:7   RTS thr:off    Fragment thr=2352 B
                     Power management: off
                     Link quality:0  Signal Level:0   Noise level:0
                     Rx invalid nwid:0   Rx invalid crypt:0  Rxinvalid frag:0
                     Tx excessive retries:0    Invalid misc:0    Missed beacon:0

pan0              no wireless extensions.

any help would be great:P Thanks!

---

### Post by R Clemons on 2009-05-09
stupid suggestion, but make sure everything is turned on in your BIOS

---

### Post by mold on 2009-05-09
thanks 
just checked and everything that looks like it should be on is on

---

### Post by RedSingularity on 2009-05-09
What is your lspci output?

---

### Post by mold on 2009-05-12
alex@alex-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
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
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
0b:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 01)

---

### Post by RedSingularity on 2009-05-12
You should see it in System>Admin>Hardware drivers.

---

### Post by mold on 2009-05-13
thanks
turns out it was just a problem with my router which is why i couldnt connect through ethernt

so now i went to the hardwaredrivers 
and found 2 driver there
-broadcom b43 wireless driver
-broadcom sta wireless driver

i activated the b43 driver but i cant figure out how to search for wireless networks:icon_frown:

---

### Post by RedSingularity on 2009-05-13
You should see them under the gnome network manager in the panel.  If you dont try activating the other driver.

---

