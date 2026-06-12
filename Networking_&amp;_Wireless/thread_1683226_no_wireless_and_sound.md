---
title: "no wireless and sound"
date: 2011-02-07
forum: Networking &amp; Wireless
---

### Post by piymon on 2011-02-07
Here are some details about my laptop:

When running lspci -v:

> piyush@piyush-laptop:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Device 0044 (rev 02)
    Subsystem: Hewlett-Packard Company Device 1425
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation Device 0046 (rev 02)
    Subsystem: Hewlett-Packard Company Device 1425
    Flags: bus master, fast devsel, latency 0, IRQ 7
    Memory at 90000000 (64-bit, non-prefetchable) [size=4M]
    Memory at 80000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 4050 [size=8]
    Capabilities: <access denied>

00:16.0 Communication controller: Intel Corporation Ibex Peak HECI Controller (rev 06)
    Subsystem: Hewlett-Packard Company Device 1425
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at 94406100 (64-bit, non-prefetchable) [size=16]
    Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation Ibex Peak USB2 Enhanced Host Controller (rev 05) (prog-if 20)
    Subsystem: Hewlett-Packard Company Device 1425
    Flags: bus master, medium devsel, latency 0, IRQ 16
    Memory at 94405c00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation Ibex Peak High Definition Audio (rev 05)
    Subsystem: Hewlett-Packard Company Device 1425
    Flags: bus master, fast devsel, latency 0, IRQ 22
    Memory at 94400000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation Ibex Peak PCI Express Root Port 1 (rev 05)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: 93400000-943fffff
    Prefetchable memory behind bridge: 0000000090400000-00000000913fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation Ibex Peak PCI Express Root Port 2 (rev 05)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: 92400000-933fffff
    Prefetchable memory behind bridge: 0000000091400000-00000000923fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation Ibex Peak USB2 Enhanced Host Controller (rev 05) (prog-if 20)
    Subsystem: Hewlett-Packard Company Device 1425
    Flags: bus master, medium devsel, latency 0, IRQ 21
    Memory at 94405800 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5) (prog-if 01)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=32
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation Ibex Peak LPC Interface Controller (rev 05)
    Subsystem: Hewlett-Packard Company Device 1425
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>

00:1f.2 SATA controller: Intel Corporation Ibex Peak 4 port SATA AHCI Controller (rev 05) (prog-if 01)
    Subsystem: Hewlett-Packard Company Device 1425
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 2296
    I/O ports at 4048 [size=8]
    I/O ports at 405c [size=4]
    I/O ports at 4040 [size=8]
    I/O ports at 4058 [size=4]
    I/O ports at 4020 [size=32]
    Memory at 94405000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation Ibex Peak SMBus Controller (rev 05)
    Subsystem: Hewlett-Packard Company Device 1425
    Flags: medium devsel, IRQ 10
    Memory at 94406000 (64-bit, non-prefetchable) [size=256]
    I/O ports at 4000 [size=32]
    Kernel modules: i2c-i801

00:1f.6 Signal processing controller: Intel Corporation Ibex Peak Thermal Subsystem (rev 05)
    Subsystem: Hewlett-Packard Company Device 1425
    Flags: bus master, fast devsel, latency 0, IRQ 10
    Memory at 94404000 (64-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>

02:00.0 Network controller: Broadcom Corporation Device 4727 (rev 01)
    Subsystem: Hewlett-Packard Company Device 1483
    Flags: bus master, fast devsel, latency 0, IRQ 10
    Memory at 93400000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>

03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
    Subsystem: Hewlett-Packard Company Device 1425
    Flags: bus master, fast devsel, latency 0, IRQ 2295
    I/O ports at 2000 [size=256]
    Memory at 91410000 (64-bit, prefetchable) [size=4K]
    Memory at 91400000 (64-bit, prefetchable) [size=64K]
    Expansion ROM at 91420000 [disabled] [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169

ff:00.0 Host bridge: Intel Corporation Device 2c62 (rev 02)
    Subsystem: Hewlett-Packard Company Device 1425
    Flags: bus master, fast devsel, latency 0

ff:00.1 Host bridge: Intel Corporation Device 2d01 (rev 02)
    Subsystem: Hewlett-Packard Company Device 1425
    Flags: bus master, fast devsel, latency 0

ff:02.0 Host bridge: Intel Corporation Device 2d10 (rev 02)
    Subsystem: Hewlett-Packard Company Device 1425
    Flags: bus master, fast devsel, latency 0

ff:02.1 Host bridge: Intel Corporation Device 2d11 (rev 02)
    Subsystem: Hewlett-Packard Company Device 1425
    Flags: bus master, fast devsel, latency 0

ff:02.2 Host bridge: Intel Corporation Device 2d12 (rev 02)
    Subsystem: Hewlett-Packard Company Device 1425
    Flags: bus master, fast devsel, latency 0

ff:02.3 Host bridge: Intel Corporation Device 2d13 (rev 02)
    Subsystem: Hewlett-Packard Company Device 1425
    Flags: bus master, fast devsel, latency 0



---

### Post by chili555 on 2011-02-07
Your question is, I assume, how do I get my wireless working.> 02:00.0 Network controller: Broadcom Corporation Device 4727 (rev 01)
Subsystem: Hewlett-Packard Company Device 1483
Flags: bus master, fast devsel, latency 0, IRQ 10
Memory at 93400000 (64-bit, non-prefetchable) [size=16K]
Capabilities: <access denied>Your device works with the module wl. Please walk the laptop over to the router, hook up an ethernet cable and get a wired ethernet connection. Open a terminal and do:```
sudo apt-get install bcmwl-kernel-source
```After it's installed, along with a dependency or two, detach the ethernet cable and reboot. Your wireless should be working.

---

### Post by piymon on 2011-02-07
> piyush@piyush-laptop:~$ sudo apt-get install bcmwl-kernel-source
[sudo] password for piyush: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package bcmwl-kernel-source
piyush@piyush-laptop:~$ 


still not working

what to do now

---

### Post by chili555 on 2011-02-07
> E: Couldn't find package bcmwl-kernel-sourceWhat Ubuntu version are you running?```
uname -r
```Under System > Administration > Synaptic > Settings > Repositories, do you have main, universe, restricted and multiverse checked? If so, press the Reload button and look for and install bcmwl-kernel-source.

---

### Post by piymon on 2011-02-07
> **chili555 said:**
> What Ubuntu version are you running?```
uname -r
```Under System > Administration > Synaptic > Settings > Repositories, do you have main, universe, restricted and multiverse checked? If so, press the Reload button and look for and install bcmwl-kernel-source.

2.6.28-19-generic

nothing new, all r checked
bcmwl-kernel-source is nowhere to be found

---

### Post by piymon on 2011-02-07
> **piymon said:**
> 2.6.28-19-generic

nothing new, all r checked
bcmwl-kernel-source is nowhere to be found

hi chilli555 r u there.. i had one more problem when i m connecting speakers then the sound is comming but inbuilt speakers r numb. can't hear anything..
this is same for wifi. if i m connecting a usb wifi device then the connection is fine but internal devices r not working..
moreover i doubt that the microphone suffers d same thing

---

### Post by chili555 on 2011-02-07
> hi chilli555 r u thereThis isn't instant messaging. I occasionally have to talk on the phone or brew a cup of tea. I am not quite sure how to install the wl driver on a system as old as yours; it would be a lot easier if you installed Ubuntu 10.10. Post back if you are unable to do so, I'll look for another solution.

As for your sound issue, you will have better luck in here: [http://ubuntuforums.org/forumdisplay.php?f=331](http://ubuntuforums.org/forumdisplay.php?f=331)

Be sure to post the make and model of your laptop in the title of the thread, for example, "Sound problem in Klingon X99 laptop."

---

### Post by piymon on 2011-02-07
sorry for
Quote:
 	 	 		 			 				hi chilli555 r u there 			 		
asi said earlier i m new 2 dis forum so apologies

---

### Post by piymon on 2011-02-07
[http://ubuntuforums.org/showthread.php?p=10436264#post10436264](http://ubuntuforums.org/showthread.php?p=10436264#post10436264)
the new thread for sound problem link given

---

### Post by chili555 on 2011-02-07
I think you need to amend the title of the thread you posted in General Help to specify the brand and exact model of laptop. HP perhaps? What model? Also, what about this?> I am not quite sure how to install the wl driver on a system as old as yours; **it would be a lot easier if you installed Ubuntu 10.10**. Post back if you are unable to do so, I'll look for another solution.

---

### Post by piymon on 2011-02-07
well i m trying to download 10.10 from torrent. Do u have a better way to upgrade from 9.04 jaunty to the desired version.

---

### Post by chili555 on 2011-02-07
Nope. The torrent is the way I recommend. Post back when you're ready. I'll brew another cup and see you soon.

---

### Post by piymon on 2011-02-08
> **chili555 said:**
> Nope. The torrent is the way I recommend. Post back when you're ready. I'll brew another cup and see you soon.

well i have downloaded ubuntu 10.10  desktop version. all the other issues are solved but the wireless still persist. now what to do

---

### Post by piymon on 2011-02-08
Here are some details about my laptop:

When running lspci -v:
> piyush@piyush-HP:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
	Subsystem: Hewlett-Packard Company Device 1425
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02) (prog-if 00 [VGA controller])
	Subsystem: Hewlett-Packard Company Device 1425
	Flags: bus master, fast devsel, latency 0, IRQ 44
	Memory at 90000000 (64-bit, non-prefetchable) [size=4M]
	Memory at 80000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 4050 [size=8]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915

00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
	Subsystem: Hewlett-Packard Company Device 1425
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at 94406100 (64-bit, non-prefetchable) [size=16]
	Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05) (prog-if 20 [EHCI])
	Subsystem: Hewlett-Packard Company Device 1425
	Flags: bus master, medium devsel, latency 0, IRQ 16
	Memory at 94405c00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
	Subsystem: Hewlett-Packard Company Device 1425
	Flags: bus master, fast devsel, latency 0, IRQ 45
	Memory at 94400000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: 93400000-943fffff
	Prefetchable memory behind bridge: 0000000090400000-00000000913fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: 92400000-933fffff
	Prefetchable memory behind bridge: 0000000091400000-00000000923fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05) (prog-if 20 [EHCI])
	Subsystem: Hewlett-Packard Company Device 1425
	Flags: bus master, medium devsel, latency 0, IRQ 21
	Memory at 94405800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=32
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
	Subsystem: Hewlett-Packard Company Device 1425
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05) (prog-if 01 [AHCI 1.0])
	Subsystem: Hewlett-Packard Company Device 1425
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 43
	I/O ports at 4048 [size=8]
	I/O ports at 405c [size=4]
	I/O ports at 4040 [size=8]
	I/O ports at 4058 [size=4]
	I/O ports at 4020 [size=32]
	Memory at 94405000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
	Subsystem: Hewlett-Packard Company Device 1425
	Flags: medium devsel, IRQ 10
	Memory at 94406000 (64-bit, non-prefetchable) [size=256]
	I/O ports at 4000 [size=32]
	Kernel modules: i2c-i801

00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
	Subsystem: Hewlett-Packard Company Device 1425
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at 94404000 (64-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: intel ips
	Kernel modules: intel_ips

02:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g LP-PHY (rev 01)
	Subsystem: Hewlett-Packard Company Device 1483
	Flags: bus master, fast devsel, latency 0, IRQ 10
	Memory at 93400000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
	Subsystem: Hewlett-Packard Company Device 1425
	Flags: bus master, fast devsel, latency 0, IRQ 42
	I/O ports at 2000 [size=256]
	Memory at 91410000 (64-bit, prefetchable) [size=4K]
	Memory at 91400000 (64-bit, prefetchable) [size=64K]
	Expansion ROM at 91420000 [disabled] [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169

ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
	Subsystem: Hewlett-Packard Company Device 1425
	Flags: bus master, fast devsel, latency 0

ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
	Subsystem: Hewlett-Packard Company Device 1425
	Flags: bus master, fast devsel, latency 0

ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
	Subsystem: Hewlett-Packard Company Device 1425
	Flags: bus master, fast devsel, latency 0

ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
	Subsystem: Hewlett-Packard Company Device 1425
	Flags: bus master, fast devsel, latency 0

ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
	Subsystem: Hewlett-Packard Company Device 1425
	Flags: bus master, fast devsel, latency 0

ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
	Subsystem: Hewlett-Packard Company Device 1425
	Flags: bus master, fast devsel, latency 0

piyush@piyush-HP:~$ 


---

### Post by chili555 on 2011-02-08
Now is bcmwl-kernel-source available in Synaptic?

---

### Post by piymon on 2011-02-08
> **chili555 said:**
> Now is bcmwl-kernel-source available in Synaptic?

yes its available should i install that
installed bcmwl-kernel-source
now what

---

### Post by chili555 on 2011-02-08
> installed bcmwl-kernel-source
now whatDetach the ethernet cable, if any, reboot and click the Network Manager icon and connect.

---

### Post by piymon on 2011-02-08
> **chili555 said:**
> Detach the ethernet cable, if any, reboot and click the Network Manager icon and connect.

yeah now its working fine. thanks for help..
just for the sake of learning..
what happened anyway
and what does that file in synaptic do
bcmwl..

---

### Post by piymon on 2011-02-08
there is one more thing can u help me with dis thread
[URL="http://ubuntuforums.org/showthread.php?t=1684027"]

http://ubuntuforums.org/showthread.php?t=1684027[/URL]

---

### Post by chili555 on 2011-02-08
> what does that file in synaptic do
bcmwl.. It installs the correct driver for your wireless card and the needed firmware.> here is one more thing can u help me with dis thread
[http://ubuntuforums.org/showthread.php?t=1684027](http://ubuntuforums.org/showthread.php?t=1684027)Nope, sorry. I am a networking and especially wireless guy. Rotating cubes are outside my meager area of knowledge.

I'm glad the wireless is working. Have fun.

---

### Post by piymon on 2011-02-08
thanks

---

