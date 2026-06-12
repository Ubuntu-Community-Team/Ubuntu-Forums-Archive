---
title: "upgrade to 10.10 breaks nvidia driver"
date: 2010-12-19
forum: Mythbuntu
---

### Post by 4dognight on 2010-12-19
SO, I have 2 servers I am upgrading, to 10.10 from 9.04. One is the master backend(mbe) and the other is a slave backend(sbe). 

The mbe has a builtin nvidia 7050PV graphics. The sbe has a builtin nvidia 7025PV graphics. Both very close to being identical. The mbe is an ABIT AN-M2HD(7050PV) and the sbe is ABIT AN-M2(7025PV) .

I first upgraded the sbe going from 9.04 to 10.04 then to 10.10. This all went fine. 

The mbe hasn't been so cooperative. It would boot only to a command prompt. The xorg log would say something about no usuable device found or something.

I have fiddled with it till I have now gone numb. I cant even recall all the different stuff I have tried. In a nutshell, I have tried several different nvidia driver versions. Monkeyed around with xorg.conf. Which I also found out isnt actually used anymore. But if you do have one it will use it. 

I am now at the point where I have the original driver for 10.10 from the repository. Still doing the exact same command prompt only login. 

One thing that I think may be the problem is it is might not be identifying the BusID correctly for the video. I seemed to recall in 9.04 I had to change the xorg,conf with the correct BusID. The line was ,

BusID  "PCI:00:18:0", which was not what lspci reported. It was reporting it to be PCI:00:12:0" . So  I think I had changed it to 12, and my video then worked in 9.04. Its been awhile and my memory could be wrong.

 I tried adding that same line , but it still doesnt work. I could very well have more than one problem here. What I think might be happening, is , the newer nvidia driver tries to automatically configure itself, and is getting the wrong BusID? Here is the relevent lines from the 2 xorg logs, from the 2 servers.

sbe - video driver loads - 
```

[    24.996] (II) Loader magic: 0x81f8e00
[    24.996] (II) Module ABI versions:
[    24.996]    X.Org ANSI C Emulation: 0.4
[    24.996]    X.Org Video Driver: 8.0
[    24.996]    X.Org XInput driver : 11.0
[    24.996]    X.Org Server Extension : 4.0
[    24.996] (--) PCI:*(0:0:18:0) 10de:053e:147b:1c2f rev 162, Mem @ 0xfb000000/16777216, 0xe0000000/268435456, 0xfc000000/16777216, BIOS @ 0x????????/131072
[    24.996] (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
[    24.996] (II) LoadModule: "extmod"
```


And, from the mbe - video driver fails to load


```
[    19.270] (II) Loader magic: 0x81fa7c0
[    19.270] (II) Module ABI versions:
[    19.270]    X.Org ANSI C Emulation: 0.4
[    19.270]    X.Org Video Driver: 8.0
[    19.270]    X.Org XInput driver : 11.0
[    19.270]    X.Org Server Extension : 4.0
[    19.271] (--) PCI:*(0:0:18:0) 10de:053b:147b:1c2e rev 162, Mem @ 0xfb000000/16777216, 0xd0000000/268435456, 0xfc000000/16777216, BIOS @ 0x????????/131072
[    19.271] (--) PCI: (0:1:10:0) 4444:0803:0070:4000 rev 1, Mem @ 0xe0000000/67108864
[    19.271] (--) PCI: (0:2:8:0) 4444:0016:0070:e807 rev 1, Mem @ 0xe8000000/67108864
[    19.271] (--) PCI: (0:2:9:0) 4444:0016:0070:e817 rev 1, Mem @ 0xe4000000/67108864
[    19.272] (II) Open ACPI successful (/var/run/acpid.socket)
[    19.272] (II) LoadModule: "extmod"
```



HEre are the lspci listings from both servers.

mbe - lspci

```
00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0e.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0f.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:10.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:11.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation C68 [GeForce 7050 PV / nForce 630a] (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
01:09.0 PCI bridge: Hint Corp HB6 Universal PCI-PCI bridge (non-transparent mode) (rev 11)
01:0a.0 Multimedia video controller: Internext Compression Inc iTVC15 MPEG-2 Encoder (rev 01)
02:08.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
02:09.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
```


sbe - lspci

```
00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0e.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0f.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:10.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:11.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation C68 [GeForce 7025 / nForce 630a] (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:09.0 FireWire (IEEE 1394): Agere Systems FW322/323 (rev 61)
01:0a.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
```

---

### Post by 4dognight on 2010-12-21
I remember now what the difference in the PCI bus setting was. lspci reports in hex (12) which is decimal 18. xorg.conf uses decimal, so thats why it looked wrong, but it is actually correct.

Anyhow, I seems to be a little further. Now it seems to detect everything, but seg faults. :sad:

```
 24.125] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    24.125] (==) NVIDIA(0): RGB weight 888
[    24.125] (==) NVIDIA(0): Default visual is TrueColor
[    24.125] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    24.125] (**) NVIDIA(0): Enabling RENDER acceleration
[    24.125] (II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
[    24.125] (II) NVIDIA(0):     enabled.
[    24.681] (II) NVIDIA(0): NVIDIA GPU GeForce 7050 PV / nForce 630a (C68) at PCI:0:18:0
[    24.681] (II) NVIDIA(0):     (GPU-0)
[    24.681] (--) NVIDIA(0): Memory: 524288 kBytes
[    24.681] (--) NVIDIA(0): VideoBIOS: 05.67.32.24.03
[    24.681] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    24.681] (--) NVIDIA(0): Connected display device(s) on GeForce 7050 PV / nForce 630a
[    24.681] (--) NVIDIA(0):     at PCI:0:18:0
[    24.681] (--) NVIDIA(0):     HannStar Display Corp HannStar U171 (CRT-0)
[    24.681] (--) NVIDIA(0):     SAMSUNG (DFP-0)
[    24.681] (--) NVIDIA(0): HannStar Display Corp HannStar U171 (CRT-0): 350.0 MHz maximum
[    24.681] (--) NVIDIA(0):     pixel clock
[    24.681] (--) NVIDIA(0): SAMSUNG (DFP-0): 155.0 MHz maximum pixel clock
[    24.681] (--) NVIDIA(0): SAMSUNG (DFP-0): Internal Single Link TMDS
[    24.681] (WW) NVIDIA(0): The EDID for HannStar Display Corp HannStar U171 (CRT-0)
[    24.681] (WW) NVIDIA(0):     contradicts itself: mode "640x360" is specified in the
[    24.681] (WW) NVIDIA(0):     EDID; however, the EDID's valid HorizSync range
[    24.681] (WW) NVIDIA(0):     (30.000-80.000 kHz) would exclude this mode's HorizSync
[    24.682] (WW) NVIDIA(0):     (26.2 kHz); ignoring HorizSync check for mode "640x360".
[    24.682] (II) NVIDIA(0): Assigned Display Device: CRT-0
[    24.682] (==) NVIDIA(0): 
[    24.682] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    24.682] (==) NVIDIA(0):     will be used as the requested mode.
[    24.682] (==) NVIDIA(0): 
[    24.682] (II) NVIDIA(0): Validated modes:
[    24.682] (II) NVIDIA(0):     "nvidia-auto-select"
[    24.682] (II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
[    24.686] (--) NVIDIA(0): DPI set to (95, 96); computed from "UseEdidDpi" X config
[    24.686] (--) NVIDIA(0):     option
[    24.687] (==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
[    24.687] (--) Depth 24 pixmap format is 32 bpp
[    24.687] (II) NVIDIA(0): Initialized GPU GART.
[    24.693] (II) NVIDIA(0): Setting mode "nvidia-auto-select"
[    24.851] 
Backtrace:
[    24.853] 0: /usr/bin/X (xorg_backtrace+0x3b) [0x80c970b]
[    24.853] 1: /usr/bin/X (0x8048000+0x5e56d) [0x80a656d]
[    24.853] 2: (vdso) (__kernel_rt_sigreturn+0x0) [0x6e740c]
[    24.853] Segmentation fault at address 0x24
[    24.853] 
Caught signal 11 (Segmentation fault). Server aborting
[    24.853] 
Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
[    24.853] Please also check the log file at "/var/log/Xorg.5.log" for additional information.
[    24.853] 
[    24.859]  ddxSigGiveUp: Closing log
```

Any suggestions?

---

### Post by 4dognight on 2010-12-22
Problem solved.

These msgs were in the kern.log.

NVRM: RmInitAdapter failed! (0x23:0xffffffff:641)
NVRM: rm_init_adapter(0) failed
vmap allocation for size 16781312 failed: use vmalloc=<size> to increase size

Which, when googled, led me to this posting.

[http://mandriva.598463.n5.nabble.com/Bug-59271-kernel-NEW-Kernel-desktop-miss-pae-option-which-increase-vmalloc-to-256m-this-prevent-nvids-td713928.html](http://mandriva.598463.n5.nabble.com/Bug-59271-kernel-NEW-Kernel-desktop-miss-pae-option-which-increase-vmalloc-to-256m-this-prevent-nvids-td713928.html)


So, I added 'vmalloc=256m' to /etc/defaults/grub to the line , as such.

GRUB_CMDLINE_LINUX="vga=771 vmalloc=256m"

then a 'sudo update-grub'


And voila! It works.

Thanks, for everyones help!:lolflag:

---

