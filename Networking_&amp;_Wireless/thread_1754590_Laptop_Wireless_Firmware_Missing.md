---
title: "Laptop Wireless Firmware Missing?"
date: 2011-05-10
forum: Networking &amp; Wireless
---

### Post by Shilver on 2011-05-10
Hello, I recently put Ubuntu on my old laptop. But, my wireless internet isn't working. All it says is "firmware is missing". I plugged my laptop into an ethernet to get the additional drivers (because that's what I did on this computer), but no other drivers show up. I look through Ubuntu Software Center and none of those work either. I don't have much of an idea on what to do, help would be very much appreciated.

I don't know the command to show you all what my wireless card is, so just ask and I'll tell you asap.

---

### Post by iponeverything on 2011-05-10
run:

```
sudo apt-get install linux-firmware-nonfree
```

and it might solve your problem.

---

### Post by Shilver on 2011-05-10
Ok, I did that and I still doesn't work. It all installed fine though.

---

### Post by Shilver on 2011-05-10
bump

---

### Post by mikewhatever on 2011-05-10
Can you post the output of **lspci** from a terminal window to identify your wireless card.

---

### Post by josephmills on 2011-05-10
could you open your terminal so we can see ```
lspci -nn 
```
```
rfkill list 
``` thanks

---

### Post by Shilver on 2011-05-10
Here's my lscpi

```
trevor@trevor-MX6025:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3580] (rev 02)
00:00.1 System peripheral [0880]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3584] (rev 02)
00:00.3 System peripheral [0880]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3585] (rev 02)
00:02.0 VGA compatible controller [0300]: Intel Corporation 82852/855GM Integrated Graphics Device [8086:3582] (rev 02)
00:02.1 Display controller [0380]: Intel Corporation 82852/855GM Integrated Graphics Device [8086:3582] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 [8086:24c2] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 [8086:24c4] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller [8086:24cd] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 83)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge [8086:24cc] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801DBM (ICH4-M) IDE Controller [8086:24ca] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller [8086:24c3] (rev 03)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller [8086:24c5] (rev 03)
00:1f.6 Modem [0703]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller [8086:24c6] (rev 03)
02:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
02:02.0 CardBus bridge [0607]: Texas Instruments PCIxx21/x515 Cardbus Controller [104c:8031]
02:02.2 FireWire (IEEE 1394) [0c00]: Texas Instruments OHCI Compliant IEEE 1394 Host Controller [104c:8032]
02:02.3 Mass storage controller [0180]: Texas Instruments PCIxx21 Integrated FlashMedia Controller [104c:8033]
02:02.4 SD Host controller [0805]: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller [104c:8034]
02:04.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)

```

rfkillist:

```
 phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

Thanks guys :)

---

### Post by josephmills on 2011-05-10
please see post number 44 [http://ubuntuforums.org/showthread.php?t=1748245&page=5](http://ubuntuforums.org/showthread.php?t=1748245&page=5)

---

### Post by mikewhatever on 2011-05-10
You need to install the **b43-fwcutter** package from the software center.
If you use the latest version of Ubuntu, aka 11.04 - Natty Narwhal, you also need to install the **firmware-b43-installer** package.

---

### Post by Shilver on 2011-05-11
> **mikewhatever said:**
> You need to install the **b43-fwcutter** package from the software center.
If you use the latest version of Ubuntu, aka 10.04 - Natty Narwhal, you also need to install the **firmware-b43-installer** package.

This worked! Thanks so much! I can't believe you guys do this for free, and you're still better then M$ support :D

---

