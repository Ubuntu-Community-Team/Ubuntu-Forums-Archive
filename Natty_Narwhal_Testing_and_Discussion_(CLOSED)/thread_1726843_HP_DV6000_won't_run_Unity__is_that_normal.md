---
title: "HP DV6000 won't run Unity :? is that normal?"
date: 2011-04-11
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by youbuntu on 2011-04-11
Just ran todays daily-live CD (amd64) and it tells me my system is not capable of running Unity... :?

I have an HP DV6000 laptop with Turion X2

---

### Post by KiwiNZ on 2011-04-11
It is probably an issue with the Nvidia  Go 7200 Chip

---

### Post by szymon_g on 2011-04-11
what is its graphic card?

---

### Post by uRock on 2011-04-11
What does it do after installing drivers? You can install them, then log out, then log in and Unity should be working with the LiveCD.

If you want help with this, then let me know wand we can move this the Natty sub-forum.

---

### Post by youbuntu on 2011-04-11
> **uRock said:**
> What does it do after installing drivers? You can install them, then log out, then log in and Unity should be working with the LiveCD.

If you want help with this, then let me know wand we can move this the Natty sub-forum.

What drivers? If I search for restricted drivers (or whatever it is called) it says nothing available :?

---

### Post by 3rdalbum on 2011-04-12
> **glossywhite said:**
> What drivers? If I search for restricted drivers (or whatever it is called) it says nothing available :?

Update your package list? Also you might find that the restricted drivers won't work on the live CD because they require a reboot first, so Additional Drivers won't offer them if you're running from a live CD.

---

### Post by tlcstat on 2011-04-12
Greetings,
I don't know how close that machine is to the Compaq 6000 which is made by HP, but the Compaq 6000 is Ubuntu Certified. 

Canonical has released it's list of certified components and machines found here....
Components  [HTML]http://www.ubuntu.com/certification/catalog[/HTML]Machines [HTML] http://www.ubuntu.com/certification[/HTML]You can do a lspci and lsusb in the terminal and get a list of components from your machine. Of course just because the component may not be in the certified list doesn't mean the firmware isn't available. My gut feeling is that Ubuntu will run just fine on your machine once the process is ironed out. Remember also that the developers are still adding support to the release.  My Intel Chipset wasn't supported on first run but couple of weeks later it came up.  Running like a champ now.
tlcstat

---

### Post by ssam on 2011-04-12
[https://wiki.ubuntu.com/DemystifyingUnityGraphicsHardwareRequirements](https://wiki.ubuntu.com/DemystifyingUnityGraphicsHardwareRequirements)

also try the command
```

ssam@oberon:~$ /usr/lib/nux/unity_support_test -p 
OpenGL vendor string:   X.Org
OpenGL renderer string: Gallium 0.4 on AMD RV635
OpenGL version string:  2.1 Mesa 7.10.1

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          yes

```
(thats a radeon hd 3650, with the open driver)

---

### Post by tlcstat on 2011-04-12
Greetings,
[B]
Original by ssam[/B]
> Also try,  /usr/lib/nux/unity_support_test -p 

Thanks, thats a good one.

tlcstat

tlcstat@tlcstat-Ubuntu:~$ /usr/lib/nux/unity_support_test -p 
OpenGL vendor string:   Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Mobile Intel® GM45 Express Chipset  x86/MMX/SSE2
OpenGL version string:  2.1 Mesa 7.10.2

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          yes
tlcstat@tlcstat-Ubuntu:~$

---

### Post by youbuntu on 2011-04-12
Okay, what does this mean?

```


OpenGL vendor string:   Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string:  2.1 Mesa 7.7.1

Not software rendered:    no
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  no
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          no

```

The actual model is "DV6231eu"

LSPCI:

```

00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 [Geforce Go 6150] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

```

---

### Post by Harry33 on 2011-04-13
Here are specs of the HP DV6231Eu Laptop:

```
Technical Details
Product Description: HP Pavilion Media Center dv6231eu Entertainment - Turion 64 X2 TL-50 - 15.4" TFT
Recommended Use: Home use
Dimensions (WxDxH): 35.7 cm x 25.7 cm x 4 cm
Weight: 3 kg
Localisation: English / United Kingdom
Windows Vista Certification: Windows Vista Premium Ready
System Type: Notebook
Built-in Devices: Stereo speakers, wireless LAN aerial
Processor: AMD Turion 64 X2 mobile technology TL-50 ( Dual-Core )
Cache Memory: 512 KB - L2 Cache
RAM: 1 GB (installed) / 2 GB (max) - DDR2 SDRAM - 667 MHz ( 2 x 512 MB )
Card Reader: 5 in 1
Hard Drive: 80 GB - Serial ATA-150 - 5400 rpm
Optical Storage: DVD±RW (+R double layer) / DVD-RAM
Display: 15.4" TFT 1280 x 800 ( WXGA )
Graphics Controller: NVIDIA GeForce Go 6150 Shared Video Memory (UMA)
Audio Output: Sound card
Telecom: Fax / modem - 56 Kbps
Networking: Network adapter - Ethernet, Fast Ethernet, IEEE 802.11b, IEEE 802.11g
Input Device: Keyboard, touchpad, QuickPlay
Battery: 6-cell Lithium Ion
```

So, the graphics card is Nvidia Geforce Go 6150.
The latest nvidia proprietary drivers (nvidia-current-270.30) in Natty repos do not support it.
Nvidia drivers support Geforce Go 7 series, but not Geforce Go 6 series.

---

### Post by ssam on 2011-04-13
> **youbuntu said:**
> Okay, what does this mean?

```


OpenGL vendor string:   Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string:  2.1 Mesa 7.7.1

Not software rendered:    no
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  no
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          no

```

The actual model is "DV6231eu"
LSPCI:
```

00:05.0 VGA compatible controller: nVidia Corporation C51 [Geforce Go 6150] (rev a2)

```

looks like you have no accelerated driver running, so it has fallen back to software rendering. this would be very slow, and also it does not support "GLX texture from pixmap" which i think is essential for compiz.

have a look in /var/log/Xorg.0.log to see if you are using nv, nouveau or vesa.

---

### Post by tlcstat on 2011-04-13
Greetings,
Patience my friend they will fix the driver when they get on of those round things!
tlcstat

---

