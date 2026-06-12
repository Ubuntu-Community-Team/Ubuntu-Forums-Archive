---
title: "some questions"
date: 2010-11-14
forum: Mythbuntu
---

### Post by isprins on 2010-11-14
Does Mythbuntu have a NAS function, a printer server, and Squeezebox Server?   

Does it have gui's for the mentioned functions ? 

If it has a NAS function,can it be accessed remote over the net ?

Can torrents/downloads be managed remotely ?

I know that Mythbuntu uses LIRC.
Does it exist a GUI used to set it up, and to "learn" the signals from other IR remotes ?
Something like press 1 on the remote to learn the command for digit number one and so forth.

the hardware i am planning to use is:

cabinet:
Antec Fusion Remote Sort EU


PSU
SI-A300-P3
Chieftec  Micro-ATX


Hard-drive:
270W PFC 20/24
WD10EARS
Western Digital Caviar GreenPower,1TB Sata 3 Gb/s 64MB


Motherboard:
GA-P55-USB3 Gigabyte P55 Socket-1156 DDR3,ATX GbLAN USB3.0 PCI-E


CPU (quad core):
BX80605I5760 INTEL Core I5-760 2800MHz,LGA1156 8M cache
ASAS535G  (64 bit support )

Arctic Silver 5 thermal paste

CPU cooler:
Scythe CPU-cooler Ninja Mini rev.B

RAM:
4 GB kit:
CMX4GX3M2A16Corsair XMS3 DDR3 1600MHz
Corsair XMS3 - 4 GB : 2 x 2 GB - DIMM 240-pin - DDR3
4 GB : 2 x 2 GB generic
DDR3 SDRAM
DIMM 240-pin
1600 MHz ( PC3-12800 )
 CL8 ( 8-8-8-24 )


DVD/bluray :
IHOS104-37
Lite-On Blu-Ray Reader Blu-Ray




Capture card:
Hauppauge! WinTV-HVR-2200 TV

IR:
Media Center Remote Control Kit

---

### Post by nickrout on 2010-11-14
> **isprins said:**
> Does Mythbuntu have a NAS function, a printer server, and Squeezebox Server?   

no but they are easy to add:```
sudo aptitude install cups squeezeboxserver
```

samba is already built in.

> Does it have gui's for the mentioned functions ? 


point your web browser at the server, port 9000 for squeezebox, port 631 for cups > 
If it has a NAS function,can it be accessed remote over the net ?


That's up to you.> 
Can torrents/downloads be managed remotely ?


```
sudo aptitude install rtorrent screen
```

> 
I know that Mythbuntu uses LIRC.
Does it exist a GUI used to set it up, and to "learn" the signals from other IR remotes ?
Something like press 1 on the remote to learn the command for digit number one and so forth.


no, but most common remotes have a config built in and is easy to set up via mythbuntu-control-centre
> the hardware i am planning to use is:

cabinet:
Antec Fusion Remote Sort EU


PSU
SI-A300-P3
Chieftec  Micro-ATX


Hard-drive:
270W PFC 20/24
WD10EARS
Western Digital Caviar GreenPower,1TB Sata 3 Gb/s 64MB


Motherboard:
GA-P55-USB3 Gigabyte P55 Socket-1156 DDR3,ATX GbLAN USB3.0 PCI-E


CPU (quad core):
BX80605I5760 INTEL Core I5-760 2800MHz,LGA1156 8M cache
ASAS535G  (64 bit support )

Arctic Silver 5 thermal paste

CPU cooler:
Scythe CPU-cooler Ninja Mini rev.B

RAM:
4 GB kit:
CMX4GX3M2A16Corsair XMS3 DDR3 1600MHz
Corsair XMS3 - 4 GB : 2 x 2 GB - DIMM 240-pin - DDR3
4 GB : 2 x 2 GB generic
DDR3 SDRAM
DIMM 240-pin
1600 MHz ( PC3-12800 )
 CL8 ( 8-8-8-24 )


DVD/bluray :
IHOS104-37
Lite-On Blu-Ray Reader Blu-Ray




Capture card:
Hauppauge! WinTV-HVR-2200 TV

IR:
Media Center Remote Control Kit

---

### Post by isprins on 2010-11-15
Thanks for the answers.

Maybe the functions i asked about could be included in Mythbuntu and configurable from the mythbuntu frontend?

I am pretty sure that mythbuntu will run fine on the hardware i listed.

---

### Post by nickrout on 2010-11-15
> **isprins said:**
> Thanks for the answers.

Maybe the functions i asked about could be included in Mythbuntu and configurable from the mythbuntu frontend?



Why? They have nothing to do with mythtv. And you'll never get a torrent client built in to mythtv - it leads to easily to fingers being pointed to myth as a pirate device.

---

