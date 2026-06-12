---
title: "Can't find Wireless Networks, 9.10"
date: 2010-02-04
forum: Networking &amp; Wireless
---

### Post by Zorgie on 2010-02-04
Hello. I'm new to ubuntu, and I installed it about a week ago on my 12" Laptop, brand HP. It's the 9.10 desktop version, not the netbook remix (cause that had some major problem with this computer, though that's a completely different issue)

Since the installation I haven't been able to find any network connections through my wireless card. I've been following like 5+ helpthreads in this and other forums, I've installed some extra packets from the installation USB, and tried to input the wireless network details manually, with no success.

A thing that might be something is that I can't install the proprietary driver associated with my network card. I added some packets that should make the installation possible, and the driver is visible in the "Hardware Drivers" list, but when I attempt to activate it a little progress bar pops about 1-2 seconds, and then nothing else happens. Of course I've done this and restarted Ubuntu, etc. 

Any help would be appreciated.

/Lucas

edit: Found a log about the non-working driver installation, here's the output:


2010-02-04 19:23:03,129 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-02-04 19:23:03,330 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-02-04 19:23:05,993 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-02-04 19:23:11,459 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-02-04 19:23:11,460 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2010-02-04 19:23:11,475 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted

---

### Post by bkratz on 2010-02-04
> **Zorgie said:**
> Hello. I'm new to ubuntu, and I installed it about a week ago on my 12" Laptop, brand HP. It's the 9.10 desktop version, not the netbook remix (cause that had some major problem with this computer, though that's a completely different issue)

Since the installation I haven't been able to find any network connections through my wireless card. I've been following like 5+ helpthreads in this and other forums, I've installed some extra packets from the installation USB, and tried to input the wireless network details manually, with no success.

A thing that might be something is that I can't install the proprietary driver associated with my network card. I added some packets that should make the installation possible, and the driver is visible in the "Hardware Drivers" list, but when I attempt to activate it a little progress bar pops about 1-2 seconds, and then nothing else happens. Of course I've done this and restarted Ubuntu, etc. 


Any help would be appreciated.

/Lucas



did you have a wired connection when you tried the update?

---

### Post by Zorgie on 2010-02-04
I've tried with the USB inserted, nothing inserted and with wired network connected.

---

### Post by bkratz on 2010-02-04
> **Zorgie said:**
> I've tried with the USB inserted, nothing inserted and with wired network connected.

So it is a usb adapter ( I guess I didn't read the first post well enough!). Go to the terminal (applications>>Accessories>>Terminal) and type in 
lsusb  (that is LSUSB in lowercase). Copy paste the output back here or decode the output and see what your device is. It should have a type and a designator in the form of xxxx:xxxx (which is the important part).

---

### Post by Zorgie on 2010-02-04
No, it's an integrated wireless network card, I meant the USB with the installation files to the ubuntu distribution.

---

### Post by bkratz on 2010-02-04
> **Zorgie said:**
> No, it's an integrated wireless network card, I meant the USB with the installation files to the ubuntu distribution.

In that case, type in lspci
(that is LSPCI in lowercase)
and copy/paste the output back here.

---

### Post by Zorgie on 2010-02-05
lspci output:
> 
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
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
02:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)


---

