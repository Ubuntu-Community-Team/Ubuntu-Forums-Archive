---
title: "Solved : Creative ViBRA16C PnP  is Working"
date: 2007-10-19
forum: Multimedia &amp; Video
---

### Post by Ancient1 on 2007-10-19
For Posterity 

Creative CT 4180 , ISA 
US Robotics Sportster 33600 Modem , ISA 
FlyVideo 98 TVtuner , PCI
Creative TNT1 32Mb , AGP
on Intel 440BX Chipset  , Abit BH6 Slot1 motherboard 
Xubuntu 7.10  ( upgraded yesterday ) 

**Problem :**  Audio N/A 
in # /etc/modules: kernel modules to load at boot time. 
added the line :   sb io=0x220 irq=5 dma=1 dma16=5 
tried many variations on this line (like : dma8=1 , isapnp=1, / 0  , 0x220-0x280 ..) 
**result :** 
root@XubuntIlan:/home/ancient1# dmesg | grep pnp
[   23.760586] pnp: PnP ACPI init
[   23.760631] ACPI: bus type pnp registered
[   23.771596] pnp: PnP ACPI: found 12 devices
[   23.771610] ACPI: ACPI bus type pnp unregistered
[   23.773406] pnp: 00:00: iomem range 0xf0000-0xf3fff could not be reserved
[   23.773424] pnp: 00:00: iomem range 0xf4000-0xf7fff could not be reserved
[   23.773438] pnp: 00:00: iomem range 0xf8000-0xfbfff could not be reserved
[   23.773452] pnp: 00:00: iomem range 0xfc000-0xfffff could not be reserved
[   26.530556] isapnp: Scanning for PnP cards...
[   26.678970] pnp: SB audio device quirk - increasing port range
[   26.694157] isapnp: Card 'Creative ViBRA16C PnP'
[   26.694170] isapnp: Card 'U.S. Robotics Sportster 33600 FAX/Voice Int'
[   26.694182] isapnp: 2 Plug & Play cards detected total
[   26.902873] pnp: Device 01:02.00 activated.
[   39.736000] pnp: **Device 01:01.01 activated.**
[   39.752000] gameport: NS558 PnP **Gameport** is pnp01:01.01/gameport0, io 0x200, speed 736kHz
root@XubuntIlan:/home/ancient1# sudo modprobe snd-sb16
root@XubuntIlan:/home/ancient1# dmesg 
[ 1264.520000] pnp: Unable to assign resources to device 01:01.00.
[ 1264.520000] sb16: **AUDIO pnp configure failure** 

* note the marked lines. the card's gameport is recognised properly. 

**Solution : ** 
1. Change the line to : snd-sb16 
2. Remove the Modem. instaling again = no Audio. 

No Idea why the modem steals the SB resources (?) , but so it seems. didn't put an effort into that, as I have cables . 

Good Luck !

---

