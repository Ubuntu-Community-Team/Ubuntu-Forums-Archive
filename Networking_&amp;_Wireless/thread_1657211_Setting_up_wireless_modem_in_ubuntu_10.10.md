---
title: "Setting up wireless modem in ubuntu 10.10"
date: 2010-12-31
forum: Networking &amp; Wireless
---

### Post by Robr0924 on 2010-12-31
I installed 10.10, I'm using a HP tower with a cisco usb ae1000 modem.  I have been on Linux all of 12 hours.  I had installed on a old laptop, and hard wired to the router.  I really liked the OS.  And Long short I killed the laptop, literally.  

So I partitioned the family tower, but I cannot connect wirelessly.  And to run hard wire to the router would mean a complete tear down of my desk and set up in the living room area, and that will not help out the marriage long/short term.

Can someone point me in the right direction, I have a red ! on the internet connection and I gone through the panels trying to set up the connection but no luck.  I'm running Vista and Ubuntu 10.10.   I using vista to post here now.

How do I get it to find the wireless router and set up my connection without being hardwire to the router itself.

Total newb here know just enough to really mess it up.

Thanks 

Rob

---

### Post by PatchesTheCaveman on 2010-12-31
Hi Robr0924!  Sorry you're having trouble getting connected wirelessly.

Please go to Applications > Accessories > Terminal in your top panel, type in the following, and press Enter:
```
lsmod
```
Then, copy and paste what appears into a reply to this thread.  That will tell me what drivers are presently loaded on your system.

I've looked into to your USB wireless and it uses a chipset that's known to cause some grief.  We should be able to sort it out though.

---

### Post by Robr0924 on 2010-12-31
drm                   168054  5 radeon,ttm,drm_kms_helper
joydev                  8735  0 
psmouse                59033  0 
soundcore                880  1 snd
lp                      7342  0 
serio_raw               4022  0 
agpgart                32011  2 ttm,drm
k8temp                  3132  0 
i2c_algo_bit            5168  1 radeon
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
i2c_nforce2             5179  0 
parport                31492  3 parport_pc,ppdev,lp
hid_logitech            8971  0 
ff_memless              4393  1 hid_logitech
usbhid                 36882  1 hid_logitech
hid                    67742  2 hid_logitech,usbhid
usb_storage            40172  0 
firewire_ohci          21106  0 
firewire_core          46643  1 firewire_ohci
pata_amd                8746  0 
crc_itu_t               1383  1 firewire_core
sata_nv                19420  2 
forcedeth              49433  0 


thanks

---

### Post by Robr0924 on 2010-12-31
Also here a little more, i've been digging through the forum.  I using my 4g smartphone as the modem currently, so I may get tossed.  Appreciate your help and advice

Rob 

  	 	 	 	p { margin-bottom: 0.08in; }  ob0924@rob0924-GC671AA-ABA-a6130n:~$ lspci -v  
 00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)  
 	Subsystem: Hewlett-Packard Company Device 2a61  
 	Flags: bus master, 66MHz, fast devsel, latency 0  
 	Capabilities: <access denied>  
 

 00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)  
 	Subsystem: Hewlett-Packard Company Device 2a61  
 	Flags: bus master, 66MHz, fast devsel, latency 0  
 

 00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)  
 	Subsystem: Hewlett-Packard Company Device 2a61  
 	Flags: 66MHz, fast devsel, IRQ 255  
 	I/O ports at fc00 [size=64]  
 	I/O ports at 1c00 [size=64]  
 	I/O ports at f400 [size=64]  
 	Capabilities: <access denied>  
 	Kernel driver in use: nForce2_smbus  
 	Kernel modules: i2c-nforce2  
 

 00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)  
 	Subsystem: Hewlett-Packard Company Device 2a61  
 	Flags: 66MHz, fast devsel  
 

 00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3) (prog-if 10 [OHCI])  
 	Subsystem: Hewlett-Packard Company Device 2a61  
 	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21  
 	Memory at fe02f000 (32-bit, non-prefetchable) [size=4K]  
 	Capabilities: <access denied>  
 	Kernel driver in use: ohci_hcd  
 

 00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3) (prog-if 20 [EHCI])  
 	Subsystem: Hewlett-Packard Company Device 2a61  
 	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22  
 	Memory at fe02e000 (32-bit, non-prefetchable) [size=256]  
 	Capabilities: <access denied>  
 	Kernel driver in use: ehci_hcd  
 

 00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1) (prog-if 01 [Subtractive decode])  
 	Flags: bus master, 66MHz, fast devsel, latency 0  
 	Bus: primary=00, secondary=01, subordinate=01, sec-latency=32  
 	I/O behind bridge: 0000b000-0000bfff  
 	Memory behind bridge: fde00000-fdffffff  
 	Prefetchable memory behind bridge: fa000000-fbffffff  
 	Capabilities: <access denied>  
 

 00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)  
 	Subsystem: Hewlett-Packard Company Device 2a61  
 	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22  
 	Memory at fe024000 (32-bit, non-prefetchable) [size=16K]  
 	Capabilities: <access denied>  
 	Kernel driver in use: HDA Intel  
 	Kernel modules: snd-hda-intel  
 

 00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2) (prog-if 8a [Master SecP PriP])  
 	Subsystem: Hewlett-Packard Company Device 2a61  
 	Flags: bus master, 66MHz, fast devsel, latency 0  
 	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]  
 	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]  
 	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]  
 	[virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]  
 	I/O ports at f000 [size=16]  
 	Capabilities: <access denied>  
 	Kernel driver in use: pata_amd  
 	Kernel modules: pata_amd  
 

 00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)  
 	Subsystem: Hewlett-Packard Company Device 2a61  
 	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 44  
 	Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]  
 	I/O ports at ec00 [size=8]  
 	Capabilities: <access denied>  
 	Kernel driver in use: forcedeth  
 	Kernel modules: forcedeth  
 

 00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2) (prog-if 85 [Master SecO PriO])  
 	Subsystem: Hewlett-Packard Company Device 2a61  
 	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23  
 	I/O ports at 09f0 [size=8]  
 	I/O ports at 0bf0 [size=4]  
 	I/O ports at 0970 [size=8]  
 	I/O ports at 0b70 [size=4]  
 	I/O ports at d800 [size=16]  
 	Memory at fe02c000 (32-bit, non-prefetchable) [size=4K]  
 	Capabilities: <access denied>  
 	Kernel driver in use: sata_nv  
 	Kernel modules: sata_nv  
 

 00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2) (prog-if 85 [Master SecO PriO])  
 	Subsystem: Hewlett-Packard Company Device 2a61  
 	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23  
 	I/O ports at 09e0 [size=8]  
 	I/O ports at 0be0 [size=4]  
 	I/O ports at 0960 [size=8]  
 	I/O ports at 0b60 [size=4]  
 	I/O ports at c400 [size=16]  
 	Memory at fe02b000 (32-bit, non-prefetchable) [size=4K]  
 	Capabilities: <access denied>  
 	Kernel driver in use: sata_nv  
 	Kernel modules: sata_nv  
 

 00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2) (prog-if 00 [Normal decode])  
 	Flags: bus master, fast devsel, latency 0  
 	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0  
 	I/O behind bridge: 0000a000-0000afff  
 	Memory behind bridge: fdd00000-fddfffff  
 	Prefetchable memory behind bridge: 00000000e0000000-00000000efffffff  
 	Capabilities: <access denied>  
 	Kernel driver in use: pcieport  
 	Kernel modules: shpchp  
 

 00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2) (prog-if 00 [Normal decode])  
 	Flags: bus master, fast devsel, latency 0  
 	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0  
 	I/O behind bridge: 00009000-00009fff  
 	Memory behind bridge: fdc00000-fdcfffff  
 	Prefetchable memory behind bridge: 00000000fdb00000-00000000fdbfffff  
 	Capabilities: <access denied>  
 	Kernel driver in use: pcieport  
 	Kernel modules: shpchp  
 

 00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2) (prog-if 00 [Normal decode])  
 	Flags: bus master, fast devsel, latency 0  
 	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0  
 	I/O behind bridge: 00008000-00008fff  
 	Memory behind bridge: fda00000-fdafffff  
 	Prefetchable memory behind bridge: 00000000fd900000-00000000fd9fffff  
 	Capabilities: <access denied>  
 	Kernel driver in use: pcieport  
 	Kernel modules: shpchp  
 

 00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration  
 	Flags: fast devsel  
 	Capabilities: <access denied>  
 

 00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map  
 	Flags: fast devsel  
 

 00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller  
 	Flags: fast devsel  
 

 00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control  
 	Flags: fast devsel  
 	Capabilities: <access denied>  
 	Kernel driver in use: k8temp  
 	Kernel modules: k8temp  
 

 01:05.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem  
 	Subsystem: Conexant Systems, Inc. Soft Data Fax Modem with SmartCP  
 	Flags: bus master, medium devsel, latency 0, IRQ 255  
 	Memory at fdfe0000 (32-bit, non-prefetchable) [size=64K]  
 	I/O ports at bc00 [size=8]  
 	Capabilities: <access denied>  
 

 01:06.0 Multimedia controller: ATI Technologies Inc Device 4d50  
 	Subsystem: ATI Technologies Inc Device a698  
 	Flags: bus master, medium devsel, latency 2, IRQ 255  
 	Memory at fde00000 (32-bit, non-prefetchable) [size=1M]  
 	Memory at fa000000 (32-bit, prefetchable) [size=32M]  
 	Capabilities: <access denied>  
 

 01:09.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 80) (prog-if 10 [OHCI])  
 	Subsystem: Hewlett-Packard Company Device 2a61  
 	Flags: bus master, stepping, medium devsel, latency 64, IRQ 19  
 	Memory at fdfff000 (32-bit, non-prefetchable) [size=2K]  
 	I/O ports at b800 [size=128]  
 	Capabilities: <access denied>  
 	Kernel driver in use: firewire_ohci  
 	Kernel modules: firewire-ohci, ohci1394  
 

 02:00.0 VGA compatible controller: ATI Technologies Inc RV570 [Radeon X1950 Pro] (prog-if 00 [VGA controller])  
 	Subsystem: ATI Technologies Inc Device 1002  
 	Flags: bus master, fast devsel, latency 0, IRQ 43  
 	Memory at e0000000 (64-bit, prefetchable) [size=256M]  
 	Memory at fddf0000 (64-bit, non-prefetchable) [size=64K]  
 	I/O ports at ac00 [size=256]  
 	[virtual] Expansion ROM at fdd00000 [disabled] [size=128K]  
 	Capabilities: <access denied>  
 	Kernel driver in use: radeon  
 	Kernel modules: radeon  
 

 02:00.1 Display controller: ATI Technologies Inc RV570 [Radeon X1950 Pro] (secondary)  
 	Subsystem: ATI Technologies Inc Device 1003  
 	Flags: bus master, fast devsel, latency 0  
 	Memory at fdde0000 (64-bit, non-prefetchable) [size=64K]  
 	Capabilities: <access denied>  
 

 rob0924@rob0924-GC671AA-ABA-a6130n:~$  
 

 rob0924@rob0924-GC671AA-ABA-a6130n:~$ sudo iwconfig  
 [sudo] password for rob0924:  
 lo        no wireless extensions.  
 

 eth0      no wireless extensions.  
 

 rob0924@rob0924-GC671AA-ABA-a6130n:~$

---

### Post by PatchesTheCaveman on 2010-12-31
Make sure your network adapter is plugged in and go back to the terminal and run:
```
sudo modprobe rt2800usb
```

Then run:
```
sudo lshw -C network
```

---

### Post by Robr0924 on 2011-01-01
Will do shortly. Thanks again

---

### Post by Robr0924 on 2011-01-01
rob0924@rob0924-GC671AA-ABA-a6130n:~$ sudo modprobe rt2800usb
[sudo] password for rob0924: 
rob0924@rob0924-GC671AA-ABA-a6130n:~$ sudo modprobe rt2800usb
rob0924@rob0924-GC671AA-ABA-a6130n:~$ 

Nothing

---

### Post by Robr0924 on 2011-01-01
*-network               
       description: Ethernet interface
       physical id: 1
       logical name: usb0
       serial: 76:fa:e9:99:2d:82
       capabilities: ethernet physical
       configuration: broadcast=yes driver=rndis_host driverversion=22-Aug-2005 firmware=RNDIS device ip=192.xxx.xx.xxx link=yes multicast=yes
rob0924@rob0924-GC671AA-ABA-a6130n:~$ 


second code gave me this

---

### Post by Robr0924 on 2011-01-01
Thanks again for all your help.

---

### Post by Robr0924 on 2011-01-02
lssub gave this information:  Still trying to get the wireless working

ob0924@rob0924-GC671AA-ABA-a6130n:~$ lsusb
Bus 002 Device 003: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 002 Device 002: ID 04b4:0033 Cypress Semiconductor Corp. Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 058f:6377 Alcor Micro Corp. Multimedia Card Reader
Bus 001 Device 005: ID 0bb4:0ffe High Tech Computer Corp. 
Bus 001 Device 004: ID 13b1:002f Linksys AE1000 v1 802.11n [Ralink RT2870]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by Robr0924 on 2011-01-05
Still stuck been offline for awhile could use some help.

Thanks 

Rob

---

### Post by PatchesTheCaveman on 2011-01-05
Try following the instructions I provided in this post:
[http://ubuntuforums.org/showpost.php?p=10314062&postcount=2](http://ubuntuforums.org/showpost.php?p=10314062&postcount=2)

---

### Post by Robr0924 on 2011-01-07
Thanks again, I appreciate your assistance and I let you know how it goes.

---

### Post by Robr0924 on 2011-01-08
ob0924@rob0924-GC671AA-ABA-a6130n:~$ tar -C ~/Download/ -xf ~/Download/RT3572_Linux_STA_v2.4.0.2.tar.bz2
tar: /home/rob0924/Download/RT3572_Linux_STA_v2.4.0.2.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
rob0924@rob0924-GC671AA-ABA-a6130n:~$ cd ~/Download/2010_0915_RT3572_Linux_STA_v2.4.0.2/

Still lost, I'm going to read up on linux and ubuntu and attack it again, I am to green and new to all of this and I really not advanced enough with the Pc.  I'm considering just going and buying a different wireless.  Any suggestions? 

I downloaded the driver, I just don't know what to next, or what directory to point too.  It is in the download directory currently. 

Stuck on step two is pretty pathetic.  

I appreciate your help and your time spent pointing me in the right direction.  I just hate windows vista.

Thanks

Rob

---

### Post by Robr0924 on 2011-01-08
Son of a B----ch, I plugged in an old netgear wg111v2 and I'm connected.   Why didn't try this sooner. 

Well this will work for now.

thanks again 

Rob

---

### Post by Robr0924 on 2011-02-01
Finally after reading elkin grays post, did i figure it out, and I'm working off my ae1000 usb modem.

thanks to all:guitar:

---

### Post by Robr0924 on 2011-02-01
> **PatchesTheCaveman said:**
> Try following the instructions I provided in this post:
[http://ubuntuforums.org/showpost.php?p=10314062&postcount=2](http://ubuntuforums.org/showpost.php?p=10314062&postcount=2)


I figured it out.  Thanks so much for your help.

---

### Post by steveb_77 on 2011-02-20
I'm stuck with the same problem and am running into a brick wall. Can you help ?

---

### Post by Robr0924 on 2011-02-22
What I did was edit the logs and save each step of the directions provided.  Edit the text logs and save.  and run in terminal.  It took me a month to figure it out so I'm probaly not the best one to ask for advice.
 
good luck

---

