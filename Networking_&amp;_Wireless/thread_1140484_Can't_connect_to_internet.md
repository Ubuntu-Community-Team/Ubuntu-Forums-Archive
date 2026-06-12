---
title: "Can't connect to internet"
date: 2009-04-27
forum: Networking &amp; Wireless
---

### Post by Lemuel111 on 2009-04-27
Hi everyone, 

I'm totally new to Linux but was shown Ubunto the other week and liked it. Have downloaded 9.04 onto disc and am trying it out from disc before converting to it. However I can't get connected to the internet. Help says to use Network Manager but I don't appear to have it. In Add/remove Network Manager is ticked but I can't 'apply'. 
I have a Talktalk MT882 modem and my desktop connects to it through Belkin wireless router. I have no idea about settings to type e.g. post, ssh or anything. If poss can anyone take me through from the begining in simple language???

Thanks (hopefully)

Lemuel:confused:

---

### Post by zebobo on 2009-04-27
> **Lemuel111 said:**
> Hi everyone, 

I'm totally new to Linux but was shown Ubunto the other week and liked it. Have downloaded 9.04 onto disc and am trying it out from disc before converting to it. However I can't get connected to the internet. Help says to use Network Manager but I don't appear to have it. In Add/remove Network Manager is ticked but I can't 'apply'. 
I have a Talktalk MT882 modem and my desktop connects to it through Belkin wireless router. I have no idea about settings to type e.g. post, ssh or anything. If poss can anyone take me through from the begining in simple language???

Thanks (hopefully)

Lemuel:confused:
Hi,
what is your wlan-card? You probably don't have the drivers installed for the wlan-card.
The standard way of installing wlan drivers is "converting" the windows-drivers to linux-drivers using a program called ndiswrapper. Get the right drivers for your card on another computer and put them - together with ndiswrapper binaries, on an usb-stick and put them into your computer and install the drivers to use wlan. 
Google linux ubuntu ndiswrapper for more info on ndiswrapper. Good luck

---

### Post by Lemuel111 on 2009-04-28
Sorry to sound daft but was is a wlan-card? What are the names of the drivers I am looking for & where do I find them? What are ndiswrapper binaries & what type do I get & where from? Then how do I install them to my wlan? Sorry I am totally new to linux and the detailed computer talk.
Thanks.

---

### Post by ktechman on 2009-04-28
Here are some links to get started with 

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")  

 [http://www.linuxquestions.org/linux/answers/Networking/NdisWrapper_The_Ultimate_Guide/]("http://www.linuxquestions.org/linux/answers/Networking/NdisWrapper_The_Ultimate_Guide/") 

You are going to have to do some reading but everything is pretty much laid out for you after you have experimented with these come back and ask any questions you may have.

                   Cheers ktechman

---

### Post by Lemuel111 on 2009-05-05
Still struggling I'm afraid. My chipset is detailed below but I can't find the right driver to download? :confused:

System
Manufacturer : ASUSTek Computer INC.
Model : A7S8X-MX
Version : 1.xx
Serial Number : 123456789000
ID : 11111111-11111111-11111111-11111111

System Chassis
Manufacturer : ASUSTek Computer INC.
Type : Desktop
Can be locked : No
Version : Chassis Version
Serial Number : EVAL
Asset Tag : 123456789000

Mainboard
Manufacturer : ASUSTek Computer INC.
Multi-Processor (MP) Support : 1 Processor(s)
MPS Version : 1.40
Model : A7S8X-MX
Version : 1.xx
Serial Number : 123456789000
System BIOS : 10/06/2004-SiS741GX-A7S8X-MX-00

System Memory Controller
Location : Mainboard
Error Correction Capability : None
Number of Memory Slots : 2
Maximum Installable Memory : 4GB
Bank0/1 - A0 : None None None None DIMM 256MB
Bank2/3 - A1 : None None None None DIMM 256MB

Chipset 1
Model : ASUSTeK Computer Inc SiS741 CPU to PCI Bridge
Revision : A4
Bus : DEC/AMD EV6/HSTL+
Front Side Bus Speed : 2x 167MHz (334MHz data rate)
Maximum FSB Speed : 2x 200MHz (400MHz data rate)
Width : 64-bit
I/O Queue Depth : 7 request(s)
Maximum Bus Bandwidth : 2672MB/s (estimated)

Chipset 1 Hub Interface
Type : MUTOL
Width : 16-bit
Full Duplex : No
Multiplier : 2/1x

Logical/Chipset 1 Memory Banks
Bank 0 : 256MB DDR-SDRAM 2.5-3-3-6 (tCL-tRCD-tRP-tRAS) CR2
Bank 1 : 256MB DDR-SDRAM 2.5-3-3-6 (tCL-tRCD-tRP-tRAS) CR2
Shared Memory : 32MB
Supported Memory Types : SDRAM DDR-SDRAM Registered
Channels : 1
Memory Bus Speed : 2x 133MHz (266MHz data rate)
Maximum Memory Speed : 2x 200MHz (400MHz data rate)
Multiplier : 4/5x
Width : 64-bit
Memory Controller in Processor : No
Refresh Rate : 15.60µs
Power Save Mode : No
Fixed Hole Present : No
Maximum Memory Bus Bandwidth : 2128MB/s (estimated)

APIC 1
Version : 1.04
Multiplier : 1/2x
Maximum Interrupts : 24
IRQ Handler Engaged : Yes
Enhanced Support : Yes

Memory Module 1
Manufacturer : Kingston
Model : K
Serial Number : 90232281
Type : 256MB DDR-SDRAM
Technology : 8x(32Mx8)
Speed : PC3200U DDR-200
Standard Timings : 3.0-3-3-8 (tCL-tRCD-tRP-tRAS)
Date of Manufacture : 11 November 2004
Memory DC Line : 2.5V
Set Timing @ 200MHz : 3.0-3-3-8 (tCL-tRCD-tRP-tRAS)
Set Timing @ 167MHz : 2.5-2-2-7 (tCL-tRCD-tRP-tRAS)
Set Timing @ 133MHz : 2.0-2-2-5 (tCL-tRCD-tRP-tRAS)

Memory Module 2
Manufacturer : Samsung
Model : M3 68L3223DTL-CB0
Serial Number : 4408F42F
Type : 256MB DDR-SDRAM
Technology : 8x(32Mx8)
Speed : PC2100U DDR-133
Standard Timings : 2.5-3-3-6 (tCL-tRCD-tRP-tRAS)
Date of Manufacture : 22 April 2003
Memory DC Line : 2.5V
Set Timing @ 133MHz : 2.5-3-3-6 (tCL-tRCD-tRP-tRAS)
Set Timing @ 100MHz : 2.0-2-2-5 (tCL-tRCD-tRP-tRAS)

Environment Monitor 1
Model : Winbond W83697HF ISA
Version : 6.00
Mainboard Specific Support : No

Temperature Sensor(s)
Board Temperature : 42.0°C / 107.6°F
CPU Temperature : 40.5°C / 104.9°F

Cooling Device(s)
Auto Fan Speed Control : Yes
CPU Fan : 2464rpm

Voltage Sensor(s)
CPU DC Line : 1.59V
+3.3V DC Line : 3.19V
+5V DC Line : 4.85V
+12V DC Line : 11.88V
-12V DC Line : 1.32V
-5V DC Line : 2.31V

AGP Bus(es) on Hub 1
Version : 3.05
Speed : 8x
Fast-Writes Enabled : No
Fast-Writes Support : Yes
Isochronous Mode Enabled : No
Addressing Enabled : 32-bit

PCI Bus(es) on Hub 1
Version : 2.10
Number of Bridges : 1
PCI Bus 0 : PCI (1/1x PCIClk)

LPC Hub Controller 1
Model : Silicon Integrated Systems (SiS) PCI to ISA Bridge
Revision : D7
ACPI Power Management Enabled : Yes
Multiplier : 1/4x

---

