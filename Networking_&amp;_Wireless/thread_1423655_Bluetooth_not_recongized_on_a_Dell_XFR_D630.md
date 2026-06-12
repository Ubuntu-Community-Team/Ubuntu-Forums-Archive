---
title: "Bluetooth not recongized on a Dell XFR D630"
date: 2010-03-06
forum: Networking &amp; Wireless
---

### Post by xtjacob on 2010-03-06
I have a Dell XFR D630 and I want to usee my bluetooth, but when I open up the bluetooth manager it says there are no devices. I know there is a bluetooth device because websites say there is and the output of dmesg is:
```
[    1.067470] Bluetooth: L2CAP ver 2.13
[    1.067472] Bluetooth: L2CAP socket layer initialized
[    1.067475] Bluetooth: SCO (Voice Link) ver 0.6
[    1.067477] Bluetooth: SCO socket layer initialized
[    1.067507] Bluetooth: RFCOMM TTY layer initialized
[    1.067510] Bluetooth: RFCOMM socket layer initialized
[    1.067511] Bluetooth: RFCOMM ver 1.11

```
The output of lspci is:
```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
03:01.0 CardBus bridge: O2 Micro, Inc. Cardbus bridge (rev 21)
03:01.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

```
Also the output of lsusb is:
```
Bus 007 Device 004: ID 0b97:7772 O2 Micro, Inc. OZ776 CCID Smartcard Reader
Bus 007 Device 003: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 007 Device 002: ID 0b97:7761 O2 Micro, Inc. Oz776 1.1 Hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 0eef:0001 D-WAV Scientific Co., Ltd eGalax TouchScreen
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 04b4:6560 Cypress Semiconductor Corp. CY7C65640 USB-2.0 "TetraHub"
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by Steve White on 2010-05-11
I have the same network card on my Dell D420, and with today's updates of Lucid, see the same problem.

The init script /etc/init.d/bluetooth (of the bluez package) seems not to do anything. After starting it, it shows status "not running", and blueman-manager says "Bluez daeman not running".

If I run bluetoothd (from the bluez package) the blueman-applet icon shows on the Gnome menu bar, and functions at least to turn my bluetooth radio light on and off.

Also bluetooth-properties (of the gnome-bluetooth package) in any case always shows "bluetooth disabled".  The "Turn on Bluetooth" button reacts but the bluetooth radio light status is unchanged.

Maybe a bug report is in order.

---

