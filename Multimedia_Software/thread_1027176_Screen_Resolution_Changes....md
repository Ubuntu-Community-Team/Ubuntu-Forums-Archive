---
title: "Screen Resolution Changes..."
date: 2009-01-01
forum: Multimedia Software
---

### Post by Gunmetal_Ghoul on 2009-01-01
When I tried to change my screen resolution to 1280X768 and apply changes the screen locks up and then turns black. I then double checked by rebooting and changing the settings again. It always freezes then turns black only when I change it to 1280X768. Also, when I change the resolution it leaves a blank space of empty screen.  What's going on here?

---

### Post by Rohan Kapoor on 2009-01-01
> **Gunmetal_Ghoul said:**
> When I tried to change my screen resolution to 1280X768 and apply changes the screen locks up and then turns black. I then double checked by rebooting and changing the settings again. It always freezes then turns black only when I change it to 1280X768. Also, when I change the resolution it leaves a blank space of empty screen.  What's going on here?
Could you please give us the specifications of your graphics card and the ammount of RAM in the system? This would help us better identify your problem. Additionally, the output of ```
lspci
``` would be helpful.

---

### Post by Gunmetal_Ghoul on 2009-01-01
-Under lspci (for anyone who can decode this!):

00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 04)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
06:05.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
06:06.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
06:06.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
06:06.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
06:06.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
06:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

-From the Sysinfo application my graphics card is an Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev4) (prog-if 00[VGA Controller])

---

### Post by overdrank on 2009-01-01
Hi and darth-vader ask another good question as to the amount of memory on the system?
If you are using Intrepid 8.10 there has been issue with the intel graphics. 
Moved to Multimedia & Video

---

### Post by Rohan Kapoor on 2009-01-01
> **overdrank said:**
> Hi and darth-vader ask another good question as to the amount of memory on the system?
If you are using Intrepid 8.10 there has been issue with the intel graphics. 
Moved to Multimedia & Video
I believe he is using 8.10 we still need to know the memory of his system but definately he is having problems due to his Intel Integrated Graphics.

---

### Post by Gunmetal_Ghoul on 2009-01-01
Actually I am using v8.04 and I have an upgraded 1024MB of RAM. My laptop is an HP Pavilion DV4000. Let me see those specs again....

---

