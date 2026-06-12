---
title: "Unichrome Graphics not working"
date: 2006-06-23
forum: Multimedia &amp; Video
---

### Post by phyre-x on 2006-06-23
hi, im not having alot of Joy with the unichrome drivers for my card after trying a few things from the forum to try and get it working. Sadly its a laptop so i dont have much idea about the specific hardware, only that it is an S3 Unichrome Pro IGP. ive installed the driver from synaptic, edited my xorg.conf but when i try and use the via driver i get an error saying "no screens" , i was wondering which graphics chipset i had but the output from lspci doesnt seem to help me much. this is when ive added pci=conf1 which another thread suggested.

```

phyre@ubuntu:~$ lspci
0000:00:00.0 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
0000:00:00.1 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
0000:00:00.2 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
0000:00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
0000:00:00.4 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
0000:00:00.7 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
0000:00:0c.0 CardBus bridge: Texas Instruments: Unknown device 8039
0000:00:0c.2 Mass storage controller: Texas Instruments: Unknown device 803b
0000:00:0c.3 0805: Texas Instruments: Unknown device 803c
0000:00:0e.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
0000:00:0f.0 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
0000:01:00.0 VGA compatible controller: VIA Technologies, Inc.: Unknown device 3344 (rev 01)
0000:02:00.0 Network controller: RaLink Ralink RT2500 802.11 Cardbus Reference Card (rev 01)

```

this is my xorg section when the x server fails to start and reports the error

Section "Device"
Identifier "VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter"
Driver "via"
BusID "PCI:1:0:0"
Option "DisableIRQ"
Option "EnableAGPDMA"
EndSection


Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1280x768"
	EndSubSection
EndSection

does anyone have any suggestions to getting this working or atleast point me in the right direction ? i cant stand the devestating graphics performace i get from the vesa driver any longer, even fullscreen video gets about 4 fps.

thanks

---

### Post by Tomy on 2006-06-24
I see your vga device id is 3344. Back on February 13th in a different thread you  would find this post.

[quote=dracflamloc]From what I've been told by the developer of the via driver, the chipset I have is not supported and probably wont be until someone can provide it to the developers to test.
 
 My card's device id is 3344 so if you've got that type of card you're out of lluck for now it seems. 
 
This kind of stinks, I was hoping that getting a card other than ati/nvidia would mean its easier to get to work in linux, not harder! Oh well...Vesa works fairly well for the time being.[/quote] 

I don't know if this has been fixed yet.

good luck 
Tomy

---

