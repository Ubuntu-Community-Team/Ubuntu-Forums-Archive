---
title: "Flash//Video? on Ubuntu(Precise) 12.04 64bit//All Versions, all browsers."
date: 2012-09-16
forum: Multimedia Software
---

### Post by AlexTepes on 2012-09-16
I seem to be having issues with Flash, it's working, but not perfectly. I'm not really having any issues with Flash video on low quality though, it's actually to do with games.

As soon as there is any movement or things happening on screen it seems to slow down quite a bit, but I can flip through dialogs quickly. There is no need for this, and I'll explain why:

CPU: AMD Phenom II 1045t x6 2.7Ghz
GPU: ATi Radeon HD 5570
Ram: 10GB

Ram info:
```
root@ubuntu:/home/l/Desktop# sudo dmidecode --type 17 | more
# dmidecode 2.11
SMBIOS 2.6 present.

Handle 0x0011, DMI type 17, 28 bytes
Memory Device
	Array Handle: 0x000F
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 4096 MB
	Form Factor: DIMM
	Set: None
	Locator: DIMM1
	Bank Locator: BANK0
	Type: DDR3
	Type Detail: Synchronous
	Speed: 1333 MHz
	Manufacturer: Manufacturer00
	Serial Number: C9271109
	Asset Tag: AssetTagNum0
	Part Number: 51264Y133I0000HYN0
Handle 0x0012, DMI type 17, 28 bytes

Memory Device
	Array Handle: 0x000F
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 2048 MB
	Form Factor: DIMM
	Set: None
	Locator: DIMM2
	Bank Locator: BANK1
	Type: DDR3
	Type Detail: Synchronous
	Speed: 1333 MHz
	Manufacturer: Samsung       
	Serial Number: E0B72A76
	Asset Tag: AssetTagNum1
	Part Number: M378B5773CH0-CH9  
	Rank: Unknown
(3 of these)

```

Graphics info: 

```

lspci -v -s `lspci | awk '/VGA/{print $1}'`
root@ubuntu:/home/l/Desktop# lspci -v -s `lspci | awk '/VGA/{print $1}'`
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Redwood PRO [Radeon HD 5500 Series] (prog-if 00 [VGA controller])
	Subsystem: Hewlett-Packard Company Device 6872
	Flags: bus master, fast devsel, latency 0, IRQ 45
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at fe9e0000 (64-bit, non-prefetchable) [size=128K]
	I/O ports at d000 [size=256]
	Expansion ROM at fe9c0000 [disabled] [size=128K]
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Legacy Endpoint, MSI 00
	Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
	Capabilities: [150] Advanced Error Reporting
	Kernel driver in use: fglrx_pci
	Kernel modules: fglrx, radeon

```

lspci

```
root@ubuntu:/home/l/Desktop# lspci
00:00.0 Host bridge: Advanced Micro Devices AMD RS880 Host Bridge
00:02.0 PCI bridge: Advanced Micro Devices AMD RS780 PCI to PCI bridge (ext gfx port 0)
00:05.0 PCI bridge: Advanced Micro Devices AMD RS780/RS880 PCI to PCI bridge (PCIE port 1)
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 5)
00:11.0 SATA controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
00:12.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.1 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0 USB OHCI1 Controller
00:12.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.1 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0 USB OHCI1 Controller
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 3c)
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Redwood PRO [Radeon HD 5500 Series]
01:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI Redwood HDMI Audio [Radeon HD 5000 Series]
02:00.0 Network controller: Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)

```


May be unrelated, but it seems Virtualbox gives me the 2D/3D options (checkboxes) but get nothing in Direct X on any of my Windows-based Guest OSes

I tried the gearbox thing after installing my graphics drivers and the 3D gearbox thing worked perfectly fine, I tried on Unity desktop with effects, without, and Gnome classic(no effects), I can't seem to get Chrome or Firefox to operate flash better. Not even with adobe's recommended version, Ubuntu's repo, or an old version. 
Even after disabling hardware acceleration.

One huge thing I notice is it's detecting 256MB of graphics memory, this GPU has 1GB GDDR5.

My reasoning is, it's a powerful PC, it's not a piece of crap by any means, it's not a Celeron, or a laptop, it's got more then enough ram/gpu, theres no reason for it to be laggy, and there is no reason why I should be having trouble, especially when Flash was fine on older versions of Ubuntu. Maybe they should stop focusing stuff like Unity and focus on Drivers/compatibility, which has always been an issue for Ubuntu.

I've decided to try uninstalling and reinstalling drivers from ATi, since obviously the crap in "Additional Drivers" doesn't seem to be giving proper info or working properly. If all else fails I'm just going to drop Ubuntu again, and definitely not recommend it anymore, with Unity being a step backwards, and them seemingly losing focus on the real issues with every new version they come up with, though I've used Ubuntu since 5, good old Hoary Hedgehog. D: Now that I think of it, I believe I used 4.10 also. Switched from Knoppix, that was fun.

After my change in graphics driver I did another gears test.

```

root@ubuntu:/usr# fgl_glxgears
Using GLX_SGIX_pbuffer
4261 frames in 5.0 seconds = 852.200 FPS
4509 frames in 5.0 seconds = 901.800 FPS
4450 frames in 5.0 seconds = 890.000 FPS
4569 frames in 5.0 seconds = 913.800 FPS
4503 frames in 5.0 seconds = 900.600 FPS

```

---

### Post by AlexTepes on 2012-09-17
After many hours of debugging, trying different drivers, versions of flash, flash-aid not working, Virtualbox not helping me on Ubuntu because of lack of proper 3D support, even though my graphics card was completely capable, and compiz effects working just fine, I found the solution to the problem with flash and the 3D driver issues. I installed Windows 7. ):P :lolflag:

I won't blame Ubuntu specifically for this choice, but the driver developers for the linux distros, and Ati.
I'll leave Ubuntu on my boot manager for a time when they decide to play nice with Ati/and vise versa.

---

### Post by drdos2006 on 2012-09-17
Adobe is no longer supporting Flash for Ubuntu. Google has taken over the role with its Chrome browser.

regards

---

### Post by AlexTepes on 2012-09-17
> **drdos2006 said:**
> Adobe is no longer supporting Flash for Ubuntu. Google has taken over the role with its Chrome browser.

regards

Doesn't make a difference when Ubuntu's app manager doesn't install flash with Chromium, and no matter what version of flash you put in it(Yes I had flash working in Chromium too), it wouldn't give me full acceleration or an "unlaggy" experience. So, obviously by the creation of the topic and all the details I put, you'd see I exhausted all options and did my research first before giving up on it. Ati isn't making very good drivers for linux, and neither are the open source developers. 

I had a Radeon Xpress 200 series onboard card back in the day and had some wonky issues with driver support too, but managed to get it all working manually back then, now I have a more powerful PC, with a 6 core cpu, and very good, not the best, but good gpu, and it still has issues with Ati, and this is over 4-5 years later. I'm done expecting any improvements in Ubuntu in this regard, and with their new Unity desktop, I could care less for the distro now than I ever did, even I could come up with a better task management system/UI, might not be able to code it, but my ideas would definitely be much better.

---

### Post by synaptix on 2012-09-17
Have you tried the GPU override to increase flash performance in linux at all?

---

### Post by AlexTepes on 2012-09-17
> **synaptix said:**
> Have you tried the GPU override to increase flash performance in linux at all?

I've tried forcing the XAA in X11, I've tried forcing Hardware acceleration in Flash through the config, I also tried the proprietary drivers, and Ati drivers, including older versions of the driver, but only went back so far because it's a newer graphics card. I also tried Flash player 10.

---

