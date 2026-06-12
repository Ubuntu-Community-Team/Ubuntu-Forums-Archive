---
title: "Microphone won't work"
date: 2008-09-24
forum: Multimedia Software
---

### Post by indianballer24 on 2008-09-24
I have turned up all my volume controls. Can anyone help me and tell me why my microphone won't pick up sound? The hardware is not defective since I have tried it in windows and it works perfectly.

---

### Post by indianballer24 on 2008-09-24
Can anyone help?

---

### Post by Crafty Kisses on 2008-09-24
If it's USB, please post the results of this command:
```
lsusb
```

---

### Post by indianballer24 on 2008-09-24
> **Codename said:**
> If it's USB, please post the results of this command:
```
lsusb
```
It's not USB. It just goes into the regular microphone jack.

---

### Post by Crafty Kisses on 2008-09-24
Alright, I'd also like to see the results of this command:
```
lspci
```

---

### Post by indianballer24 on 2008-09-24
> **Codename said:**
> Alright, I'd also like to see the results of this command:
```
lspci
```
root@user1-laptop:/home/user1# lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
04:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
04:09.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
04:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

---

### Post by Sam Lars on 2008-10-15
I know you said you have everything turned up, but you might still find something in this howto.
[http://ubuntuforums.org/showthread.php?t=385739&highlight=microphone+jack](http://ubuntuforums.org/showthread.php?t=385739&highlight=microphone+jack)
Are you using Hardy or Intrepid?  You could give Intrepid a go to see if it works, at least from LiveCD.

---

