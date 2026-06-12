---
title: "Serious AMD Video Trouble"
date: 2008-04-09
forum: Multimedia &amp; Video
---

### Post by metalguy639 on 2008-04-09
I have some serious troubles with my on board video for my new motherboard. First to describe what the trouble is. I have lines going down my screen in a vertical fashion. This is really annoying especially since I work as a web designer. I have tried many things but nothing has worked yet and I want to try all I can software wise before I have to go out and buy a new video card and spend money. I am hoping this is a software fix and that someone here has an idea how to fix it. I would post  a screen shot of what it looks like but the lines do not show up in a screen shot.

My System info:

 ECS GOAL3+ AMD Sempron 3000+ 754 SiS 761 GX Micro ATX Motherboard/CPU Combo - Retail
All in one - motherboard with CPU

1.5 gig memory on board
on board sound, video etc. 

This is an AMD64

What I have tried already:

1. Reloading Ubuntu 7.10 in the AMD (Switched from Intel to AMD)
2. Upgrading to Ubuntu 8.04

I still currently running Ubuntu 8.04

Please help! 

Thanks

---

### Post by deadgobby on 2008-04-09
Are you running the 64 bit kernel or the 32 bit kernel?
Gobby

---

### Post by metalguy639 on 2008-04-09
> **deadgobby said:**
> Are you running the 64 bit kernel or the 32 bit kernel?
Gobby

Yes that is what I installed on the machine  and still had the lines.  I installed the alternative because someone said in another thread that it fixed video problems. It did not :( Then I updated to Ubuntu 8.04. It did not give me a choice of whether to install the 64 bit one or not, so I guessing that maybe it did because it detected the correct system or it installed whatever. Either way the video still did the same thing :(

Is it possible that this may be some kind of driver issue? I could not find drivers for my motherboard for linux anywhere.

I not sure if you can post links to a PC web site that sells stuff so I just going to copy & paste the mobo info here.

> GOAL3+ supports the latest AMD Athlon64/Sempron, K8 CPUs, up to 800MHz FSB, DDR400, two Serial ATA and 8 USB 2.0 ports. With embedded Ultra256 3D Graphic engine, 64M share memory ,one PCI ExpressX16 slot, all these advance supports, we believe your computer can run with best performance and bring you the greatest value and enjoyment.


  	CPU 	
 	Socket 754 for AMD Athlon64(K8)/Sempron processor
  	FSB 	
 	800 MHz
  	Chipset 	
 	SiS 761GX/965L
  	VGA 	
 	Embedded Mirage Graphics with 128MB share memory
  	Memory 	
 	2 x 184-pin DIMM sockets support two 2.5V DDR SDRAMs (DDR333/266/200)
 	Maximum: 2GB
  	Expansion Slots 	
 	1 x PCI Express x 16 slots
 	2 x PCI slots
 	1 x CNR slot
  	LAN 	
 	Realtek RTL8201CL 10/100Mbps Fast Ethernet PHY
  	Audio 	
 	AD 1888 6-channel audio Codec
 	Compliant with AC'97 2.3 specification
  	IDE 	
 	2 x UltraDMA 133/100/66
  	Back Panel I/O Ports 	
 	1 x PS/2 keyboard
 	1 x PS/2 mouse
 	1 x Parallel Port
 	1 x Serial Port
 	1 x VGA port
 	4 x USB 2.0 Ports
 	1 x RJ 45 Port
 	1 x Audio I/O (Line-in, Line-out and Mic-in)
  	Internal I/O Connectors & Headers 	
 	24-pin ATX Power Supply connector
 	4-pin ATX 12V power supply connector
 	2 x USB 2.0 header support additional 4 USB2.0 ports
 	2 x Serial ATA connectors
 	1 x Front panel switch/LED header
 	1 x Front panel audio header
 	CPU / SYS FAN headers
 	1 x IrDA for SIR header
 	1 x Speaker header
 	1 x CD in header
 	1 x Floppy connector-support 360K~2.88M Byte, 3 Mode FDDs or LS120
 	1 x SPDIF out header
  	System BIOS 	
 	AMI 4Mb Flash ROM
 	Supports Plug and Play 1.0A, APM 1.2, Multi Boot, DMI
 	Full support for ACPI revision 1.0 specification
  	Form Factor 	
 	Micro ATX Form Factor, 244x203mm



Hopefully this info will help to know if I need a video driver or something. 

EDIT: I found a possible solution and I want to see if anyone knows about this. 

I went on the web site that I purchased the board from adn found a review that said they installed the server X64 edition of Ubuntu & base gnome and the video issue cleared right up. Does anyone know about this. Can you explain how to install base gnome so I might try this out?

Thanks

---

### Post by metalguy639 on 2008-04-11
> **deadgobby said:**
> Are you running the 64 bit kernel or the 32 bit kernel?
Gobby

Sorry I'm using the 64 bit. 

I also found a helpful link that would solve my problem if I had an intel chip. But since I have an AMD chip this does not work. 

[Here's the link]("http://www.linuxforums.org/forum/ubuntu-help/118397-new-laptop-using-ubuntu-x64-bit-question.html")

This is exactly what is happening with my PC and when I switched my desktop to 1024X768 resolution the lines cleared up, but I really need to use the 1280X1024 resolution instead. Does anyone know a possible fix for this or a install along the same lines of the one mentioned in the linked page?

---

