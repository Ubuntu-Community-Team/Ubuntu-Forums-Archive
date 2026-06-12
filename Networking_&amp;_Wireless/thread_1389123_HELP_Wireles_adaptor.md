---
title: "HELP Wireles adaptor???"
date: 2010-01-24
forum: Networking &amp; Wireless
---

### Post by SherriLynnHart on 2010-01-24
I just recently installed and have no clue how to get the drivers for my netopia 3d wireless adaptor to work! all the drivers are for windows! I have never used this OS before please someone HELP!:confused:

---

### Post by Floppyjoe on 2010-01-24
> **SherriLynnHart said:**
> I just recently installed and have no clue how to get the drivers for my netopia 3d wireless adaptor to work! all the drivers are for windows! I have never used this OS before please someone HELP!:confused:

Open a terminal window and type :
```
lsusb
``` for a usb adaptor or:
```
lspci
``` for a built in adaptor:

Post the results here.

---

### Post by lidex on 2010-01-24
You'll probably need ndiswrapper. If not installed run this command in a terminal (Applications>Accessories>Terminal):
```
sudo apt-get install ndisgtk
```
Enter your password when prompted. Press enter after each command.

Go to this section: "3.4. Installing Windows driver" on this page:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")

Use the Win XP drivers from the disk.

---

### Post by SherriLynnHart on 2010-01-25
> **Floppyjoe said:**
> Open a terminal window and type :
```
lsusb
``` for a usb adaptor or:
```
lspci
``` for a built in adaptor:

Post the results here.


00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB Controller #2 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
02:02.0 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
02:02.1 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
02:03.0 Multimedia audio controller: ESS Technology ES1988 Allegro-1 (rev 12)
02:05.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 42)




usb adaptor

---

### Post by bkratz on 2010-01-25
> **SherriLynnHart said:**
> 00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB Controller #2 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
02:02.0 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
02:02.1 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
02:03.0 Multimedia audio controller: ESS Technology ES1988 Allegro-1 (rev 12)
02:05.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 42)




usb adaptor




Was this the listing for lspci since nothing shows for the network controller? The last line says (usb adaptor). If the device is a usb device please post the output of lsusb also. Here is a link of a pdf of the devices.
[http://www.netoctopus.com/equipment/pdf/3D_R_Wireless_Adapt_DS.pdf](http://www.netoctopus.com/equipment/pdf/3D_R_Wireless_Adapt_DS.pdf)

---

### Post by Floppyjoe on 2010-01-26
Yes Sherri if you have a usb Adaptor enter:
```
lsusb
```
into a terminal and post the result here.

You will see something like this then:
> Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 064e:a102 Suyin Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 045e:00d2 Microsoft Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


---

