---
title: "HTPC hardware and software questions"
date: 2012-10-30
forum: Mythbuntu
---

### Post by isprins on 2012-10-30
Hello, does anyone have any opinions on this hardware setup ?

GPU:
Sapphire Radeon HD 7750 1GB GDDR5
PCI-Express 3.0, "Ultimate Edition", DVI, native-HDMI, DisplayPort

CPU:
Intel® Core i5-3570K 
Socket-LGA1155, Quad Core, 3.4Ghz, 6MB, Boxed w/fan
(stock fan/cooler will be replaced with a SCYTHE Big Shuriken 2 Rev B)

RAM:
Corsair Vengeance DDR3 1600MHz 12GB CL9
Kit w/3x 4GB XMS3 modules, CL9-9-9-24, 1.5V, Vengeance Heatspreader, 240

Motherboard:
ASUS P8Z68-V PRO/GEN3, Socket-1155
ATX, Z68, DDR3, 3xPCIe(3.0)x16, CFX&SLI, SATA 6Gb/s,USB3.0,FW,
VGA,DVI,HDMI, EFI

HDD:
Western Digital® Desktop Black 1TB
SATA 6Gb/s (SATA 3.0), 64MB Cache, 7200RPM, 3.5",

chassis:
Silverstone Lascala LC16B-M HTPC 

PSU:
Corsair AX 850W PSU
ATX 12V V2.31, 80 Plus Gold, Modular, 4x 6+2-pin PCIe, 12x SATA
Its perhaps a bit overkill, but that results in a light load and silent
running. This PSU shuts down its fan if its running under light loads.

DVB-C card:
Digital Devices DuoFlex C&T

CAM module:
Mascom Conax CAM 
I have heard that this CAM can decode up to 4 channels simultaneous,
and works with Canal Digital smart cards even if they are paired. The
CAM module that Canal Digital sells does not have this feature.

Mythbuntu related questions:
Is it possible to watch channel B while recording channel X ?
Is it possible to switch between mythbuntu to the kubuntu desktop and back again, so Mythbuntu can record tv shows while I am chatting on facebook ?
Is the drivers for Digital Devices DuoFlex C&T included in the kernel ?

---

### Post by AlecJ on 2012-10-31
The Sapphire Radeon HD 7750 1GB GDDR5 appears to be unsupported at present,
[HTML]http://onubuntu.blogspot.co.uk/2012/05/sapphire-radeon-hd7750-ubuntu.html[/HTML]The Digital Devices DuoFlex C&T  not in Kernal as yet
[HTML]http://linuxtv.org/wiki/index.php/Digital_Devices_DuoFlex_C&T[/HTML]I would recommend 2 Hard drives, 1 for Mythbuntu system 300Gb or so, and 1 to hold your recordings and ripped DVD's etc. 1Tb is quite small as you will find out over time. I'm at 4Tb already.

Mythbuntu is 2 parts
A Backend that runs in the background and handles all the hardware and recordings
A or multiple  Frontends that can be on the same machine as the backend or remote over LAN. If you have enough tuners for the frontends, one per channel.
It is possible on DVB-S that a single tuner can stream 2 or more channels if there on the same multiplex, either to watch on a remote frontend or record simultaneously, I don't know about cable.
So yes you can watch channel A and watch channel X, maybe even record B and Y as well?
And shut down the Frontend an do Facebook etc

---

### Post by Rotak on 2012-10-31
Basically it's possible to watch channel A and record channel B (or watch on another frontend), while both channels are on the same transponder (frequency). This - at least - works on DVB-S and C. Don't know about DVB-T.

About DuoFlex....
A friend of mine bought DuoFlex card + 2 tuners (DVB-S2 + C) + CI module about a year ago. Spent several hunderet Euros.

There are Linux drivers, they said.
The cards would run smoothly, they said.
The CI module would work with Linux, they said.

None was true. CI didn't work at all. It took us 3 days to get the DVB-S tuner to work without driver freeze after 20 minutes. The experiment of using SASC + card reader with original payTV card as a replacement for the non-working CI made the driver freeze the whole system after 5 - 7 minutes.

Long story short: Friend sent them back and got a refund. 

For you, I hope they've got better with the hardware and drivers over the last year. But I am definitely cured from DuoFlex.

---

### Post by isprins on 2012-10-31
Hm.. I hope that they have updated the drivers for the Digital Devices DuoFlex C&T. A local company states that it works with linux.

GPU Alternatives:
ZOTAC GeForce GT 640 2GB PhysX CUDA
PCI-Express 3.0, "ZONE Edition", DDR3, 2xDVI, mini-HDMI, Heatsink
That card has the heattubes on the top, looks like it is to high to fit in the HTPC case.

PowerColor Radeon HD 7750 1GB GDDR5
PCI-Express 3.0, "Go! Green", DL-DVI, native-HDMI, DisplayPort, Passive edition
Thats a low profile card, it looks like its supported in linux.

---

### Post by Rotak on 2012-10-31
Well, I hope so. And it would be great if you could report back, if you got them to work. When we tried it, our idea was to have a cubic case with a mini ITX mainboard which only has one PCI slot. If your cards work, that idea could be revived, maybe. ;)

---

### Post by isprins on 2012-11-01
Quote Phoronix.com :
For now any Linux desktop users with an AMD Radeon HD 7000 series graphics card are better off using the Catalyst Linux driver until the RadeonSI support matures.

The latest driver is here:
[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx)
Latest release on 10/22/2012 .

I hope that the driver matures soon..

---

### Post by nickrout on 2012-11-01
> **isprins said:**
> Quote Phoronix.com :
For now any Linux desktop users with an AMD Radeon HD 7000 series graphics card are better off using the Catalyst Linux driver until the RadeonSI support matures.

The latest driver is here:
[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx)
Latest release on 10/22/2012 .

I hope that the driver matures soon..Don't bother with radeon, go for nvidia.

Also don't bother with tuner cards that are not supported in the standard kernel. Go to the linuxtv.org wiki and search there.

---

### Post by dannyboy79 on 2012-11-01
> **nickrout said:**
> don't bother with radeon, go for nvidia.

Also don't bother with tuner cards that are not supported in the standard kernel. Go to the linuxtv.org wiki and search there.

+1

---

### Post by brooksilg on 2012-11-02
I think ASUS still makes a fanless gpu that has hdmi out - i used on my arch htpc and it worked beautifully and quietly

---

