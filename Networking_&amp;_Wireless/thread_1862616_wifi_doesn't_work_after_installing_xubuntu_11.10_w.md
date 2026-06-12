---
title: "wifi doesn't work after installing xubuntu 11.10 with Atheros"
date: 2011-10-16
forum: Networking &amp; Wireless
---

### Post by OOHHOO on 2011-10-16
hi, i hope i can get help for this. i have an old asus eeepc netbook 1000he with Atheros Communications AR8121/AR8113/AR8114 

i've had ubuntu 10.04 to 11.10 on it with no other operating system. everytime i've updated i would have issues, either no wifi or i could connect and then get dropped. but i was always able to find a workaround on google to make it work.

after upgrading to ubuntu 11.10, the wifi worked fine. then i decided to get xubuntu installed. i didn't do a fresh install, i downloaded the "xubuntu desktop system" via the ubuntu software center.

when i restarted and logged in with xubuntu, i no longer had wifi. i even restarted back into ubuntu and i no longer had wifi in that setup either.

i've searched and found some posts regarding the Atheros driver, but it was for earlier versions of ubuntu. so i was afraid to try it. i was wondering if there are any newer solutions to get wifi working in xubuntu 11.10?

i truly appreciate any help i can get. thank you.  :)

here is some terminal output stuff:

----------------------------------------------------------
ohhoo@ohhoo-laptop:~$ lspci -vnn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GME Express Memory Controller Hub [8086:27ac] (rev 03)
    Subsystem: ASUSTeK Computer Inc. Device [1043:8340]
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel

00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GME Express Integrated Graphics Controller [8086:27ae] (rev 03) (prog-if 00 [VGA controller])
    Subsystem: ASUSTeK Computer Inc. Device [1043:8340]
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at f7f00000 (32-bit, non-prefetchable) [size=512K]
    I/O ports at dc00 [size=8]
    Memory at d0000000 (32-bit, prefetchable) [size=256M]
    Memory at f7ec0000 (32-bit, non-prefetchable) [size=256K]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: intelfb, i915

00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
    Subsystem: ASUSTeK Computer Inc. Device [1043:8340]
    Flags: bus master, fast devsel, latency 0
    Memory at f7f80000 (32-bit, non-prefetchable) [size=512K]
    Capabilities: <access denied>

00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device [1043:834a]
    Flags: bus master, fast devsel, latency 0, IRQ 43
    Memory at f7eb8000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: 7fa00000-7fbfffff
    Prefetchable memory behind bridge: 000000007fc00000-000000007fdfffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: fbf00000-fbffffff
    Prefetchable memory behind bridge: 000000007f800000-000000007f9fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.3 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 4 [8086:27d6] (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=02, sec-latency=0
    I/O behind bridge: 00001000-00001fff
    Memory behind bridge: f8000000-fbefffff
    Prefetchable memory behind bridge: 00000000f0000000-00000000f6ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 [8086:27c8] (rev 02) (prog-if 00 [UHCI])
    Subsystem: ASUSTeK Computer Inc. Device [1043:830f]
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at d400 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02) (prog-if 00 [UHCI])
    Subsystem: ASUSTeK Computer Inc. Device [1043:830f]
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at d480 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02) (prog-if 00 [UHCI])
    Subsystem: ASUSTeK Computer Inc. Device [1043:830f]
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at d800 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02) (prog-if 00 [UHCI])
    Subsystem: ASUSTeK Computer Inc. Device [1043:830f]
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at d880 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02) (prog-if 20 [EHCI])
    Subsystem: ASUSTeK Computer Inc. Device [1043:830f]
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at f7eb7c00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=32
    Capabilities: <access denied>

00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device [1043:830f]
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: leds-ss4200, iTCO_wdt, intel-rng

00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller [8086:27c4] (rev 02) (prog-if 80 [Master])
    Subsystem: ASUSTeK Computer Inc. Device [1043:830f]
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at ffa0 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: ata_piix

03:00.0 Ethernet controller [0200]: Atheros Communications AR8121/AR8113/AR8114 Gigabit or Fast Ethernet [1969:1026] (rev b0)
    Subsystem: ASUSTeK Computer Inc. Device [1043:8324]
    Flags: bus master, fast devsel, latency 0, IRQ 44
    Memory at fbfc0000 (64-bit, non-prefetchable) [size=256K]
    I/O ports at ec00 [size=128]
    Capabilities: <access denied>
    Kernel driver in use: ATL1E
    Kernel modules: atl1e


---------------------------------------------------
ohhoo@ohhoo-laptop:~$ rfkill list all
0: asus-wlan: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
1: asus-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no


----------------------------------------------
ohhoo@ohhoo-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GME Express Memory Controller Hub [8086:27ac] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GME Express Integrated Graphics Controller [8086:27ae] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 02)
00:1c.3 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 4 [8086:27d6] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller [8086:27c4] (rev 02)
03:00.0 Ethernet controller [0200]: Atheros Communications AR8121/AR8113/AR8114 Gigabit or Fast Ethernet [1969:1026] (rev b0)



thanks again

---

### Post by OOHHOO on 2011-10-17
ok i found the problem. i searched here some more and read about it being soft blocked

this is what i had in the terminal when i put in:
sudo rfkill list all

------------------------------------
0: asus-wlan: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
1: asus-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
------------------------------------


so i opened the terminal and put in:
sudo rfkill unblock all

now when i run this command:
sudo rfkill list all


i get this:

-------------------------------------
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: asus-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
------------------------------------

and now my wifi works :KS


hope this helps someone else. :)

---

### Post by Mr_Mxyzptlk on 2012-06-04
> **OOHHOO said:**
> ok i found the problem. i searched here some more and read about it being soft blocked

this is what i had in the terminal when i put in:
sudo rfkill list all

------------------------------------
0: asus-wlan: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
1: asus-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
------------------------------------


so i opened the terminal and put in:
sudo rfkill unblock all

now when i run this command:
sudo rfkill list all


i get this:

-------------------------------------
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: asus-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
------------------------------------

and now my wifi works :KS


hope this helps someone else. :)
It helped me! Thank you.

Of course, why Wi-Fi should be blocked in a fresh install is beyond me. I've previously installed Ubuntu and Lubuntu, and Wi-Fi worked right off the bat - although there were other problems with these distros that eventually led to my uninstalling them.

Linux will be great when it's finished... :)

---

