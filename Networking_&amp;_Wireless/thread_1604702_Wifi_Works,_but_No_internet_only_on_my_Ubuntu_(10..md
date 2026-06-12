---
title: "Wifi Works, but No internet only on my Ubuntu (10.04) Side"
date: 2010-10-24
forum: Networking &amp; Wireless
---

### Post by nik1979 on 2010-10-24
Wifi Works, but No internet
When I'm directly connected to the Wifi router, via LAN cable, I have internet (this is how I'm posting now)
I have a desktop computer, this is also the same problem. Because of this it hasn't updated to 10.04 yet. Its still at the version previous (9.??).

Any help would be very much appreciated. Thanks in advance.

*Might be relevant*.
This problem began when my wife's Mac had an update that killed her Wifi access, and we had to reset the Wifi Router. She didn't change anything, we just re-inputed all the data as before (passwords, ID).
Since then I can't access my internet even if I can connect to the wifi. 

*Other Observations*
In the office, my Laptop's ubuntu side has no problems with accessing Internet through the wifi.   
My Windows side is unaffected (both Desktop and Laptop). 
One time I can connect, but when that happened on that same day she can't. Possibly a fluke or coincidence. 
I read the post of a similar matter, where the person's Empathy still works. when I tried check if that was the case with me, after getting my Empathy to work it began to work again. But this hasn't worked in a succeeding attempt. 


Below is my system information if it may be relevant. 
[PHP]
Lenovo Ideapad Y430

cpu:                                                            
                       Intel(R) Core(TM)2 Duo CPU     T5800  @ 2.00GHz, 2000 MHz
                       Intel(R) Core(TM)2 Duo CPU     T5800  @ 2.00GHz, 800 MHz
keyboard:
  /dev/input/event5    AT Translated Set 2 keyboard
mouse:
  /dev/input/mice      Macintosh mouse button emulation
  /dev/input/mice      SynPS/2 Synaptics TouchPad
graphics card:
                       Intel Mobile 4 Series Chipset Integrated Graphics Controller
                       Intel Mobile 4 Series Chipset Integrated Graphics Controller
sound:
                       Intel 82801I (ICH9 Family) HD Audio Controller
storage:
                       Intel ICH9M/M-E SATA AHCI Controller
                       O2 Micro Integrated MS/xD Controller
network:
  wlan0                Intel PRO/Wireless 5100 AGN [Shiloh] Network Connection
  eth0                 Broadcom NetLink BCM5906M Fast Ethernet PCI Express
network interface:
  lo                   Loopback network interface
  eth0                 Ethernet network interface
  wlan0                WLAN network interface
disk:
  /dev/sda             WDC WD2500BEVS-2
partition:
  /dev/sda1            Partition
  /dev/sda2            Partition
  /dev/sda3            Partition
  /dev/sda5            Partition
  /dev/sda6            Partition
  /dev/sda7            Partition
cdrom:
  /dev/sr0             HL-DT-ST DVDRAM GSA-T50N
usb controller:
                       Intel 82801I (ICH9 Family) USB UHCI Controller #4
                       Intel 82801I (ICH9 Family) USB UHCI Controller #5
                       Intel 82801I (ICH9 Family) USB UHCI Controller #6
                       Intel 82801I (ICH9 Family) USB2 EHCI Controller #2
                       Intel 82801I (ICH9 Family) USB UHCI Controller #1
                       Intel 82801I (ICH9 Family) USB UHCI Controller #2
                       Intel 82801I (ICH9 Family) USB UHCI Controller #3
                       Intel 82801I (ICH9 Family) USB2 EHCI Controller #1
bios:
                       BIOS
bridge:
                       Intel Mobile 4 Series Chipset Memory Controller Hub
                       Intel 82801I (ICH9 Family) PCI Express Port 1
                       Intel 82801I (ICH9 Family) PCI Express Port 2
                       Intel 82801I (ICH9 Family) PCI Express Port 3
                       Intel 82801I (ICH9 Family) PCI Express Port 4
                       Intel 82801I (ICH9 Family) PCI Express Port 6
                       Intel 82801 Mobile PCI Bridge
                       Intel ICH9M LPC Interface Controller
hub:
                       Linux 2.6.32-25-generic ehci_hcd EHCI Host Controller
                       Linux 2.6.32-25-generic ehci_hcd EHCI Host Controller
                       Linux 2.6.32-25-generic uhci_hcd UHCI Host Controller
                       Linux 2.6.32-25-generic uhci_hcd UHCI Host Controller
                       Linux 2.6.32-25-generic uhci_hcd UHCI Host Controller
                       Linux 2.6.32-25-generic uhci_hcd UHCI Host Controller
                       Linux 2.6.32-25-generic uhci_hcd UHCI Host Controller
                       Linux 2.6.32-25-generic uhci_hcd UHCI Host Controller
memory:
                       Main Memory
firewire controller:
                       O2 Micro Firewire (IEEE 1394)
unknown:
                       FPU
                       DMA controller
                       PIC
                       Timer
                       Keyboard controller
                       Intel 82801I (ICH9 Family) SMBus Controller
                       O2 Micro Integrated MMC/SD Controller
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
  /dev/input/event6    Chicony Electronics Lenovo EasyCamera
[/PHP]

---

### Post by grahammechanical on 2010-10-24
When you left click on the network icon do you see a list of available wireless networks?  Is your netwrok among them? What information do you see when you enter nm-tool into a terminal? Does it say that wlan0 is connected?

Regards

---

### Post by nik1979 on 2011-11-20
Changed OS, working now. Thanks, sorry for the very late reply.

---

