---
title: "Jvc camera with pinnacle doesn't work"
date: 2011-12-10
forum: Multimedia Software
---

### Post by gpfat on 2011-12-10
I have a JVC GR-D740E camera  with a usb firewire “Pinnacle 510 USB Rev: 2.0” (that works on windows xp). 

I've **ubuntu 11.10** in dual boot with windows xp. 

I've done some steps with no success:

i've installed kino. I opened Kino having the camera opened and in play. When i push the capture button kino returns that the kernel module raw1394 hasn'l loaded.

I've tried with kdenlive that stopped with an error:
# Fatal Error." "MLT's SDL module not found

If i do:
# gp@gp-desktop:~$ dvgrab 
# Error: no camera exists

I've tried to find the module:
# lsmod | grep 1394
# No results

If i do 
# gp@gp-desktop:/dev$ modprobe raw1394 
# FATAL: Module raw1394 not found. 

I put the modules needed (raw1394,dv1394,ohci1394,iee1394) in /etc/modules. 
# sudo gedit /etc/modules**
copying:
iee1394
raw1394*
video1394
dv1394

And after i've written a udev rule:
# sudo gedit /etc/udev/rules.d/40-permissions.rules

Saving the file with these lines:

KERNEL=="raw1394", GROUP="disk", MODE="0666"*
KERNEL=="dv1394*", GROUP="video", MODE="0666"*
KERNEL=="video1394*", GROUP="video", MODE="0666"

But after the reboot the modules hasn't been loaded yet (and the same error in modeprobe)

I found, at this point, that i have to load other modules: 
firewire-core, firewire-ochi and firewire-sbp2, these are the new modules.
I've installed and putting them into /etc/modules.

# gp@gp-desktop:~$ lsmod 
Module                  Size  Used by 
firewire_sbp2          18414  0 
firewire_ohci          35854  0 
firewire_core          56937  2 firewire_sbp2,firewire_ohci 

The modules has been loaded after the reboot
But Kino and dvgrab does the same errors.

i've written a udev rule changing the old module with the new. No results.

I don't know now what i've to do. Any help, please?

---

### Post by gpfat on 2011-12-10
i've forgotten other info:

gp@gp-desktop:/usr/src/pmb$ uname -r
3.0.0-13-generic


gp@gp-desktop:~$ lsmod | grep 'firewire\|1394' 
firewire_ohci          35854  0 
firewire_sbp2          18414  0 
firewire_core          56937  2 firewire_ohci,firewire_sbp2 
crc_itu_t              12627  2 rt61pci,firewire_core 

The module's loaded.

gp@gp-desktop:/usr/src/pmb$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0471:200e Philips (or NXP) 
Bus 001 Device 003: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 004: ID 05e3:0606 Genesys Logic, Inc. USB 2.0 Hub / D-Link DUB-H4 USB 2.0 Hub
Bus 001 Device 005: ID 03f0:032a Hewlett-Packard 
Bus 001 Device 006: ID 093a:2470 Pixart Imaging, Inc. SoC PC-Camera
Bus 001 Device 007: ID 046d:c050 Logitech, Inc. RX 250 Optical Mouse
Bus 001 Device 008: ID 05e3:0606 Genesys Logic, Inc. USB 2.0 Hub / D-Link DUB-H4 USB 2.0 Hub
Bus 001 Device 009: ID 2304:0223 Pinnacle Systems, Inc. DazzleTV Sat BDA Device
Bus 001 Device 010: ID 04b8:012d Seiko Epson Corp. Perfection V10/V100 (GT-S600/F650)

The system see the pinnacle 510 usb.

But if I make a dmesg it seems that the camera has not seen.

---

