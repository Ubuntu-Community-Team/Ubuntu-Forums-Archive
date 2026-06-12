---
title: "Built in Laptop cam not working"
date: 2011-10-16
forum: Multimedia Software
---

### Post by siddi on 2011-10-16
I have upgraded to Ububtu 11.10
It is still not detecting my built in laptop cam.
I have an acer aspire 5571

Tried changing settings on g streamer properties. not working

Please help

---

### Post by papibe on 2011-10-16
Could you post the result of these commands?
```
$ lsusb

$ lspci
```
Please paste your results using code tags (the # icon you see while editing your post).

Regards.

---

### Post by siddi on 2011-10-17
> **papibe said:**
> Could you post the result of these commands?
```
$ lsusb

$ lspci
```Please paste your results using code tags (the # icon you see while editing your post).

Regards.

siddharth@siddharth-Aspire-5570:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
siddharth@siddharth-Aspire-5570:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
0a:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0a:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
siddharth@siddharth-Aspire-5570:~$

---

### Post by no2498 on 2011-10-17
your cam should come up as a rico cam
you will need to get a driver for it

? do you need to click the fn+f4 keys to turn the cam on
in a terminal type dmesg click enter
after it stops type lsusb click enter
that should give you a number and name of the cam
use the number and name to find the driver you need
also install guvcview try the cam in it

---

### Post by siddi on 2011-10-17
[LIST]
[*]Fn + f4 key only restartted the screen
[/LIST]


[LIST]
[*]Lsusb command gave me the folllowing result
[/LIST]
            Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


[LIST]
[*]How do i find the driver i need with this?
[*]How do i install guvcview?
[/LIST]

---

### Post by papibe on 2011-10-17
I'm afraid the webcam is not even recognized.

Do you dual boot by any chance? Maybe from Windows you can get the device details.

Regards.

---

### Post by siddi on 2011-10-17
no i don't ave dual boot. its a built in cam tat was working when i first installed ubuntu. subsequently during upgrades it stopped recognising

---

### Post by papibe on 2011-10-17
Interesting.

Here's an idea for you. Try to remember which version of Ubuntu recognized your camera. Then go [here]("http://releases.ubuntu.com/") and download that version. Create a CD or USB stick with it. Then boot into that, and choose 'Try Ubuntu' (Live). Then run the commands that I asked you before.

Post your results here.

I hope it helps,
Regards.

---

