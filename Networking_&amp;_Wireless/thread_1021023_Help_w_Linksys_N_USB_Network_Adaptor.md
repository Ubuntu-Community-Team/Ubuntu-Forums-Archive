---
title: "Help w/ Linksys N USB Network Adaptor"
date: 2008-12-24
forum: Networking &amp; Wireless
---

### Post by dupowdis on 2008-12-24
Okay, so I am new to the whole Linux concept. I have a relatively old computer that does not have built in networking, so I use a Linksys N Dual Band adaptor. I plug it in the USB, and it is not detected...So I used that program called ndiswrapper to detect the drivers, and I followed some other steps from another thread and I got something telling me how to make an output using ndiswrapper and i got this...
________________________________________________________________

luke@LukeCDR:~$ ndiswrapper
Usage: ndiswrapper OPTION

Manage ndis drivers for ndiswrapper.
-i inffile        Install driver described by 'inffile'
-d devid driver   Use installed 'driver' for 'devid'
-e driver         Remove 'driver'
-l                List installed drivers
-m                Write configuration for modprobe


where 'devid' is either PCIID or USBID of the form XXXX:XXXX
luke@LukeCDR:~$ lshw -c network
Hardware Lister (lshw) - B.02.12.01
usage: lshw [-format] [-options ...]
       lshw -version

	-version        print program version (B.02.12.01)

format can be
	-html           output hardware tree as HTML
	-xml            output hardware tree as XML
	-short          output hardware paths
	-businfo        output bus information

options can be
	-class CLASS    only show a certain class of hardware
	-C CLASS        same as '-class CLASS'
	-disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
	-enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
	-quiet          don't display status
	-sanitize       sanitize output (remove sensitive information like serial numbers, etc.)

luke@LukeCDR:~$ lsusb
Bus 001 Device 009: ID 054c:0243 Sony Corp. 
Bus 001 Device 008: ID 090c:6000 Feiya Technology Corp. 
Bus 001 Device 007: ID 0409:005a NEC Corp. 
Bus 001 Device 003: ID 1737:0071  
Bus 001 Device 002: ID 109f:7148 eSOL Co., Ltd 
Bus 001 Device 001: ID 0000:0000  
luke@LukeCDR:~$ lspci
00:00.0 Host bridge: Intel Corporation 82810E DC-133 (GMCH) Graphics Memory Controller Hub (rev 03)
00:01.0 VGA compatible controller: Intel Corporation 82810E DC-133 (CGC) Chipset Graphics Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801AA PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801AA ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801AA IDE Controller (rev 02)
00:1f.2 USB Controller: Intel Corporation 82801AA USB Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801AA SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801AA AC'97 Audio Controller (rev 02)
01:0d.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (rev 01)
01:0e.0 Communication controller: Conexant HSF 56k HSFi Modem (rev 01)
luke@LukeCDR:~$ 
________________________________________________________________

I dont think my Linksys was detected...any solutions, or something im doing wrong? Sorry, Im new...

---

