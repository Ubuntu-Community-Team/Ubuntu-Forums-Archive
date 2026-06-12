---
title: "GNOME Bluetooth won't pair with Polaroid PoGo printer"
date: 2010-05-20
forum: Networking &amp; Wireless
---

### Post by philpem on 2010-05-20
Hi guys,
I'm honestly not sure if this is a Hardware & Laptops question or a Networking & Wireless question, but seeing as Bluetooth is a wireless technology, I'm going with #2.. :)

I've got a Polaroid PoGo mini-printer, which I use for printing out logic analysis traces, oscilloscope plots and so forth from a variety of test equipment. Basically, it saves me powering up the laser printer, finding a pair of scissors to cut out the print, and then looking for a Pritt-stick (glue stick) to stick the printout into my lab notebook (and then inevitably finding that the glue stick has dried out, getting covered in my fingers covered in glue or something like that).

This printer supports two communication methods: Bluetooth and Pictbridge. Obviously Pictbridge isn't an option, so I'm going to be using Bluetooth, and sending it files from my PC. The PC's job is to FTP into my logic analyser (or oscilloscope), grab /system/screen.pcx, convert that to a JPEG, then feed it to the PoGo. The JPEG files are sent as files -- what a mobile phone would call Send As Bluetooth. I think this would be the Bluetooth OBEX profile?

There is, however, a problem: the Bluetooth stack won't pair with the printer.

If I click the Bluetooth icon, then select Set Up New Device, I can see the PoGo in the device list ("Polaroid 11 03 5c"). When I select the PoGo and set the PIN number (6000) in PIN Options, I can then click "Forward". Gnome-Bluetooth grinds for a bit ("Connecting to Polaroid 11 03 5c"), then tells me it can't pair with the printer:
  "Setting up Polaroid 11 03 5c failed."

I am then left with two options: Restart Setup, and Close.

Here's the strange part.. I can pair it from the command line:
```
philpem@cheetah:~$ hcitool scan
Scanning ...
	00:1F:E4:DC:95:73	K800i
	00:04:48:11:03:5C	Polaroid 11 03 5c
philpem@cheetah:~$ hcitool cc 00:04:48:11:03:5C
Can't create connection: Operation not permitted
philpem@cheetah:~$ sudo hcitool cc 00:04:48:11:03:5C
[sudo] password for philpem:
```

When I've entered my password, I get a "Bluetooth device wants to pair with this computer, enter PIN:" requester, where I entered the PoGo's PIN (6000, same as every other PoGo). Once I've done this, the PoGo appears in Bluetooth Preferences and I can send JPEGs to it from Nautilus (and it even prints them!).

Is it possible to get a bit more debug info out of the GNOME Bluetooth software? I'd like to know why this works on the command line, yet the GUI barfs...

Thanks,
Phil.



Hardware details:
  Ubuntu 10.04 on x86_64, Intel Q6600@3GHz quadcore, 4GB DDR2 RAM, 2x500GB WD RE2 HDDs + 1x500GB Seagate, GeForce GTX260. Bluetooth adapter is a no-name purple USB thing with a Broadcom chipset, and USB ID 0a5c:200a "Broadcom Corp. Bluetooth dongle". Apparently it's based on a BCM2035 chipset.

HCITool / SDPTool dump:
```
philpem@cheetah:~$ sudo hcitool info 00:04:48:11:03:5C
Requesting information ...
	BD Address:  00:04:48:11:03:5C
	Device Name: Polaroid 11 03 5c
	LMP Version: 2.0 (0x3) LMP Subversion: 0xc5c
	Manufacturer: Cambridge Silicon Radio (10)
	Features: 0xff 0xff 0x8f 0xfa 0x9b 0xb9 0x00 0x80
		<3-slot packets> <5-slot packets> <encryption> <slot offset> 
		<timing accuracy> <role switch> <hold mode> <sniff mode> 
		<park state> <RSSI> <channel quality> <SCO link> <HV2 packets> 
		<HV3 packets> <u-law log> <A-law log> <CVSD> <paging scheme> 
		<power control> <transparent SCO> <broadcast encrypt> 
		<EDR ACL 2 Mbps> <enhanced iscan> <interlaced iscan> 
		<interlaced pscan> <inquiry with RSSI> <extended SCO> 
		<EV4 packets> <EV5 packets> <AFH cap. slave> 
		<AFH class. slave> <3-slot EDR ACL> <5-slot EDR ACL> 
		<AFH cap. master> <AFH class. master> <EDR eSCO 2 Mbps> 
		<3-slot EDR eSCO> <extended features> 

philpem@cheetah:~$ sdptool browse 00:04:48:11:03:5C
Browsing 00:04:48:11:03:5C ...
Service Name: OBEX Object Push
Service RecHandle: 0x10000
Service Class ID List:
  "OBEX Object Push" (0x1105)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 1
  "OBEX" (0x0008)
Language Base Attr List:
  code_ISO639: 0x656e
  encoding:    0x6a
  base_offset: 0x100
```

---

