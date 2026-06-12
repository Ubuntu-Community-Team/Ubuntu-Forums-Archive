---
title: "No WiFi without XP"
date: 2010-07-08
forum: Networking &amp; Wireless
---

### Post by mytaz on 2010-07-08
I have an old usb Atmel dongle which works correctly under XP, but it does not work with ubuntu 10.04...
But if I boot under XP, activate the dongle, reboot under Ubuntu, it works fine ??? I cannot understand what happen (the same with network-manager or wicd)
With prior booting under XP, ifconfig, iwconfig, iwlist wlan0 scan, net surfing, etc... OK ; direct booting with Ubuntu : error messages in dmesg :

uname : 2.6.32-23-generic #37-Ubuntu SMP

lsusb
Bus 002 Device 003: ID 03eb:7614 Atmel Corp. AT76c505a Wireless Adapter
Bus 002 Device 002: ID 058f:9254 Alcor Micro Corp. Hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 2770:905c NHJ, Ltd Che-Ez Snap SNAP-U/Digigr8/Soundstar TDC-35
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

ndiswrapper -l
netv5a8 : driver installed
    device (03EB:7614) present (alternate driver: at76c50x_usb)

dmesg | grep ndisw
[   26.912626] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)

[   27.997224] ndiswrapper: driver netv5a8 (ATMEL,12/5/2003,4.10.9.424) loaded


[ 3137.136026] usb 2-1: new full speed USB device using uhci_hcd and address 6
[ 3137.290337] usb 2-1: configuration #1 chosen from 1 choice
[ 3137.416033] usb 2-1: reset full speed USB device using uhci_hcd and address 6
[ 3138.588023] ndiswrapper (wrap_reset_port:1093): locking failed: -16
[ 3140.772023] ndiswrapper (wrap_reset_port:1093): locking failed: -16
[ 3140.775483] ndiswrapper (mp_init:219): couldn't initialize device: C0000001
[ 3140.775493] ndiswrapper (pnp_start_device:435): Windows driver couldn't initialize the device (C0000001)
[ 3140.775511] ndiswrapper (mp_halt:262): device dd7e9ba0 is not initialized - not halting
[ 3140.775517] ndiswrapper: device eth%d removed
[ 3140.775556] ndiswrapper: probe of 2-1:1.0 failed with error -22

I cannot find infos on these errors (16 & 22) and on the message "windows driver couldn't initialize the device"
When I have installed Lucid, this dongle was not OK & that is why I used ndiswrapper ...
If any good genius has good ideas : 1000 thanks !!!

---- Oups : forget : PC Dell workstation 530 bi-xeon ----

---

