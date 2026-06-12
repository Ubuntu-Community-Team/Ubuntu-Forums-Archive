---
title: "Mint-Maya: Hardware Present: Yes (Still not working)"
date: 2012-11-13
forum: Networking &amp; Wireless
---

### Post by davethewave83 on 2012-11-13
This is for Linux Mint Maya x64 running cinnamon

[IMG]http://www.mediafire.com/conv/0107c36ba4ac4e9ca2dde935b89b5509e470b42032be7c4b9f05e6e1d77cb9fd6g.jpg[/IMG]

I'm not really sure what's going on, this card works in Windows but not in Mint apparently. 

It says it's present, but it's not working. ```
System:    Host: mint Kernel: 3.2.0-23-generic x86_64 (64 bit) Desktop: Gnome Distro: Linux Mint 13 Maya
Machine:   Mobo: ECS model: A740GM-M version: 7.0 Bios: American Megatrends version: 080014 date: 05/07/2010
CPU:       Triple core AMD Phenom 8400 -Core (-MCP-) cache: 1536 KB flags: (lm nx sse sse2 sse3 sse4a svm) 
           Clock Speeds: 1: 1050.00 MHz 2: 1050.00 MHz 3: 1050.00 MHz
Graphics:  Card: Advanced Micro Devices [AMD] nee ATI Redwood PRO [Radeon HD 5500 Series] 
           X.Org: 1.11.3 drivers: ati,radeon (unloaded: vesa,fbdev) Resolution: 1920x1080@60.0hz 
           GLX Renderer: Gallium 0.4 on AMD REDWOOD GLX Version: 2.1 Mesa 8.0.4
Audio:     Card-1: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA) driver: snd_hda_intel
           Card-2: Advanced Micro Devices [AMD] nee ATI Redwood HDMI Audio [Radeon HD 5000 Series] driver: snd_hda_intel
           Sound: Advanced Linux Sound Architecture ver: 1.0.24
Network:   Card-1: Marvell 88w8335 [Libertas] 802.11b/g Wireless 
           IF: N/A state: N/A mac: N/A
           Card-2: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 driver: tulip 
           IF: eth1 state: down mac: 00:04:5a:6a:56:06
           Card-3: Realtek RTL8101E/RTL8102E PCI Express Fast Ethernet controller driver: r8169 
           IF: eth0 state: up speed: 100 Mbps duplex: full mac: 44:87:fc:e2:e4:93

```

---

### Post by chili555 on 2012-11-13
What does this tell us?```
dmesg | grep ndis
```

---

### Post by davethewave83 on 2012-11-13
Thanks for the reply, and new command to try to add to my memory. 
```
[   10.356413] ndiswrapper version 1.57 loaded (smp=yes, preempt=no)
[   10.503678] ndiswrapper: driver mrv8335x64 (Marvell,07/01/2005,3.2.0.7) loaded
[   10.504076] ndiswrapper 0000:03:01.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   10.504978] ndiswrapper: using IRQ 21
[   10.517929] ndiswrapper (mp_init:211): couldn't initialize device: C0000001
[   10.517942] ndiswrapper (pnp_start_device:395): Windows driver couldn't initialize the device (C0000001)
[   10.517952] ndiswrapper (mp_halt:254): device ffff88012853b780 is not initialized - not halting
[   10.517956] ndiswrapper: device eth%d removed
[   10.517981] ndiswrapper 0000:03:01.0: PCI INT A disabled
[   10.518083] ndiswrapper: probe of 0000:03:01.0 failed with error -22
[   10.518291] usbcore: registered new interface driver ndiswrapper

```

---

