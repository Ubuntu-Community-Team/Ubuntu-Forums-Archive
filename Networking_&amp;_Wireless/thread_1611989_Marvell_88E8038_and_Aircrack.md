---
title: "Marvell 88E8038 and Aircrack"
date: 2010-11-02
forum: Networking &amp; Wireless
---

### Post by caspian915 on 2010-11-02
Hi all,

First time posting. I apologize if this is a totally dead topic - I have done some searching and now I'm just making sure my assumption is correct. I have a Gateway MT6705, and when I run the system info command on terminal, I get 88E8038 PCI-E Fast Ethernet Controller
vendor:	Marvell Technology Group Ltd. as the only networking device. 

1) I assume this is for both wired and wireless networking on this computer.

2) The chipset is Yukon.

3) And according to the newbie guide and compatibility list, this looks like unsupported hardware. 

Are these assumptions correct? Thanks for the help in advance.

sps

---

### Post by chili555 on 2010-11-02
> I assume this is for both wired and wireless networking on this computer.Wired only.> The chipset is Yukon.I believe the chipset is Marvell.> And according to the newbie guide and compatibility list, this looks like unsupported hardware.
I believe it's supported by the sometimes troublesome driver *sky2*.

If you'd care to post:```
lspci -nn
lsusb
```We'll be glad to review it for evidence of your wireless card, if any.

---

### Post by caspian915 on 2010-11-02
That would be really helpful. Let me know if this the correct info:

> 00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 02)
00:1f.2 SATA controller [0106]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller [8086:27c5] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 02)
02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller [11ab:4352] (rev 14)
03:09.0 CardBus bridge [0607]: Texas Instruments PCIxx12 Cardbus Controller [104c:8039]
03:09.1 FireWire (IEEE 1394) [0c00]: Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller [104c:803a]
03:09.2 Mass storage controller [0180]: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD) [104c:803b]
sps@sps-gateway:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 045e:0745 Microsoft Corp. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


---

### Post by chili555 on 2010-11-02
> Bus 001 Device 004: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 [COLOR="Red"]Wireless[/COLOR] AdapterIt is supported by the driver module rtl8187.

I have no idea whether it does aircrack.

Is it working and connecting?

---

### Post by caspian915 on 2010-11-03
Thanks so much. Now to spend the rest of the day figuring out how to get this to work.

---

### Post by chili555 on 2010-11-03
Post back if we can help.

---

