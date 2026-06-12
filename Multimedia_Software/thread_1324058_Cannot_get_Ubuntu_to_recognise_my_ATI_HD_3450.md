---
title: "Cannot get Ubuntu to recognise my ATI HD 3450"
date: 2009-11-12
forum: Multimedia Software
---

### Post by The Foz on 2009-11-12
I have a Dell SC1430. It has an ATI ES1000 video card on the motherboard, which is total rubbish, so I bought a new ATI HD 3450. 

Today I installed the card (no mean feat, as the SC1430 has PCI-Express x4 slots, and the ATI card is a x8 ). 

The problem is that the system doesn't see the card at all. I tried 'lspci', and then 'lspci -M -H1'. What I got is shown below.

```

00:00.0 Host bridge: Intel Corporation 5000V Chipset Memory Controller Hub (rev 92)
00:02.0 PCI bridge: Intel Corporation 5000 Series Chipset PCI Express x4 Port 2 (rev 92)
## 00.02:0 is a bridge from 00 to 02-06
00:03.0 PCI bridge: Intel Corporation 5000 Series Chipset PCI Express x4 Port 3 (rev 92)
## 00.03:0 is a bridge from 00 to 07-07
00:08.0 System peripheral: Intel Corporation 5000 Series Chipset DMA Engine (rev 92)
00:10.0 Host bridge: Intel Corporation 5000 Series Chipset FSB Registers (rev 92)
00:10.1 Host bridge: Intel Corporation 5000 Series Chipset FSB Registers (rev 92)
00:10.2 Host bridge: Intel Corporation 5000 Series Chipset FSB Registers (rev 92)
00:11.0 Host bridge: Intel Corporation 5000 Series Chipset Reserved Registers (rev 92)
00:13.0 Host bridge: Intel Corporation 5000 Series Chipset Reserved Registers (rev 92)
00:15.0 Host bridge: Intel Corporation 5000 Series Chipset FBD Registers (rev 92)
00:16.0 Host bridge: Intel Corporation 5000 Series Chipset FBD Registers (rev 92)
00:1c.0 PCI bridge: Intel Corporation 631xESB/632xESB/3100 Chipset PCI Express Root Port 1 (rev 09)
## 00.1c:0 is a bridge from 00 to 01-01
00:1d.0 USB Controller: Intel Corporation 631xESB/632xESB/3100 Chipset UHCI USB Controller #1 (rev 09)
00:1d.1 USB Controller: Intel Corporation 631xESB/632xESB/3100 Chipset UHCI USB Controller #2 (rev 09)
00:1d.2 USB Controller: Intel Corporation 631xESB/632xESB/3100 Chipset UHCI USB Controller #3 (rev 09)
00:1d.3 USB Controller: Intel Corporation 631xESB/632xESB/3100 Chipset UHCI USB Controller #4 (rev 09)
00:1d.7 USB Controller: Intel Corporation 631xESB/632xESB/3100 Chipset EHCI USB2 Controller (rev 09)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d9)
## 00.1e:0 is a bridge from 00 to 08-08
00:1f.0 ISA bridge: Intel Corporation 631xESB/632xESB/3100 Chipset LPC Interface Controller (rev 09)
00:1f.1 IDE interface: Intel Corporation 631xESB/632xESB IDE Controller (rev 09)
00:1f.2 IDE interface: Intel Corporation 631xESB/632xESB/3100 Chipset SATA IDE Controller (rev 09)
01:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 21)
02:00.0 PCI bridge: Intel Corporation 6311ESB/6321ESB PCI Express Upstream Port (rev 01)
## 02.00:0 is a bridge from 02 to 03-05
02:00.3 PCI bridge: Intel Corporation 6311ESB/6321ESB PCI Express to PCI-X Bridge (rev 01)
## 02.00:3 is a bridge from 02 to 06-06
03:00.0 PCI bridge: Intel Corporation 6311ESB/6321ESB PCI Express Downstream Port E1 (rev 01)
## 03.00:0 is a bridge from 03 to 04-04
03:01.0 PCI bridge: Intel Corporation 6311ESB/6321ESB PCI Express Downstream Port E2 (rev 01)
## 03.01:0 is a bridge from 03 to 05-05
08:02.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
08:09.0 VGA compatible controller: ATI Technologies Inc ES1000 (rev 02)

Summary of buses:

00: Primary host bus
	1e.0 Bridge to 08-08
	1c.0 Bridge to 01-01
	03.0 Bridge to 07-07
	02.0 Bridge to 02-06
01: Entered via 00:1c.0
02: Entered via 00:02.0
	00.3 Bridge to 06-06
	00.0 Bridge to 03-05
03: Entered via 02:00.0
	01.0 Bridge to 05-05
	00.0 Bridge to 04-04
08: Entered via 00:1e.0

```

I did check the BIOS set-up to make sure that there were no clashes with the new card: it has a unique IRQ.

This is clearly not a driver issue, but something more basic. Does anyone have any ideas?

Of course, there is the chance that I damaged the card during installation, but I am pretty certain that is not the case.

---

### Post by xzero1 on 2009-11-12
To diagnose a possible hw issue try another os or a different Ubuntu release. Also examining xorg and system logs could be useful.

I also notice that your motherboard card is still recognized. Could that be the problem?

---

### Post by markbuntu on 2009-11-12
I have a HD3450 PCI and have had zero problems with it. Did you reinstall the driverY you need to do that to get the card detected and so the driver can set up properly for it.

---

### Post by Yellow Pasque on 2009-11-12
> Did you reinstall the driverY you need to do that to get the card detected and so the driver can set up properly for it.
If lspci doesn't recognize the device, then the problem runs deeper than lack of a driver.

> I did check the BIOS set-up to make sure that there were no clashes with the new card: it has a unique IRQ.
Did you see any options to disable the onboard IGP or "prefer" a discrete card?

---

### Post by The Foz on 2009-11-15
The problem is solved. The only problem is that I don't know what fixed it.

I removed all the cards (the Radeon video card, and an audio card), and then added them back in (first the video card).

The HD3450 was recognised, and continued to work after I added the audio card.

I haven't made any changes at all top the xorg.conf file (the embedded video controller is also an ATI), but I now have good enough graphics performance to meet my needs.

---

