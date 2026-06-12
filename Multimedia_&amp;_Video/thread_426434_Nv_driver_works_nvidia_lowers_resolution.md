---
title: "Nv driver works nvidia lowers resolution"
date: 2007-04-28
forum: Multimedia &amp; Video
---

### Post by Tim Hollen on 2007-04-28
OK my set up with dual monitors works with the "nv" driver. Both give all the resolutions which are supposed to work with the cards and the monitors. But if I just switch the "nv" with "nvidia" in the xorg.conf then my Geforce2 gets only the 800 x 600 resolution. I have added the screen horizontal and vertical rates to the xorg.conf which was needed for the higher resolutions on the Geforce2. They just dont seem to be accepted under nvidia.
any suggestions?
TIm

 lspci -n | grep 0300
01:08.0 0300: 10de:0110 (rev b2)
02:00.0 0300: 10de:00f3 (rev a2)

 lspci | grep VGA
01:08.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)
02:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6200] (rev a2)

and Xorg.log 
(II) NVIDIA(1): NVIDIA GPU GeForce2 MX/MX 400 at PCI:1:8:0 (GPU-1)
(--) NVIDIA(1): Memory: 32768 kBytes
(--) NVIDIA(1): VideoBIOS: 03.11.01.50.23
(--) NVIDIA(1): Interlaced video modes are not supported on this GPU
(--) NVIDIA(1): Connected display device(s) on GeForce2 MX/MX 400 at
(--) NVIDIA(1):     PCI:1:8:0:
(--) NVIDIA(1):     @@@ (CRT-0)
(--) NVIDIA(1): @@@ (CRT-0): 350.0 MHz maximum pixel clock
(II) NVIDIA(1): Assigned Display Device: CRT-0
(WW) NVIDIA(1): No valid modes for "1280x1024"; removing.
(WW) NVIDIA(1): No valid modes for "1152x864"; removing.
(WW) NVIDIA(1): No valid modes for "1024x768"; removing.
(WW) NVIDIA(1): No valid modes for "800x600"; removing.
(WW) NVIDIA(1): No valid modes for "640x480"; removing.
(WW) NVIDIA(1): 
(WW) NVIDIA(1): Unable to validate any modes; falling back to the default mode
(WW) NVIDIA(1):     "nvidia-auto-select".
(WW) NVIDIA(1): 
(II) NVIDIA(1): Validated modes:
(II) NVIDIA(1):     "nvidia-auto-select"
(II) NVIDIA(1): Virtual screen size determined to be 800 x 600
(**) NVIDIA(1): DPI set to (65, 65); computed from "DisplaySize" Monitor
(**) NVIDIA(1):     section option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  Yes, I do.
(II) resource ranges after preInit:
	[0] 0	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B]
	[1] 0	0	0xe3000000 - 0xe3ffffff (0x1000000) MX[B]
	[2] 1	0	0xe1000000 - 0xe1ffffff (0x1000000) MX[B]
	[3] 1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B]
	[4] 1	0	0xe0000000 - 0xe0ffffff (0x1000000) MX[B]
	[5] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[6] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[7] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[8] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[9] -1	0	0xe5000000 - 0xe5000fff (0x1000) MX[B]
	[10] -1	0	0xe5005000 - 0xe5005fff (0x1000) MX[B]
	[11] -1	0	0xe5004000 - 0xe50040ff (0x100) MX[B]
	[12] -1	0	0xe5003000 - 0xe5003fff (0x1000) MX[B]
	[13] -1	0	0xe5002000 - 0xe5002fff (0x1000) MX[B]
	[14] -1	0	0xd8000000 - 0xd7ffffff (0x0) MX[B]O
	[15] -1	0	0xe1000000 - 0xe1ffffff (0x1000000) MX[B](B)
	[16] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[17] -1	0	0xe0000000 - 0xe0ffffff (0x1000000) MX[B](B)
	[18] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[19] -1	0	0xe3000000 - 0xe3ffffff (0x1000000) MX[B](B)
	[20] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[21] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[22] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[23] 1	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[24] 1	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[25] 1	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[26] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[27] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[28] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[29] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[30] -1	0	0x0000d800 - 0x0000d87f (0x80) IX[B]
	[31] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[32] -1	0	0x0000d000 - 0x0000d007 (0x8) IX[B]
	[33] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[34] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[35] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
	[36] 1	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[37] 1	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Setting mode "1280x1024"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(==) RandR enabled
(II) NVIDIA(1): Setting mode "nvidia-auto-select"
(II) NVIDIA(1): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(1): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(1): Backing store disabled

---

### Post by Tim Hollen on 2007-04-28
No one loves me :(

---

### Post by Jeremy Jackins on 2007-04-29
I'm having the same problem

---

### Post by TheDoulos on 2007-04-29
Similar problem...loaded the nvidia-glx-legacy drivers and did "sudo nvidia-glx-config enable"...xorg.conf looks okay as far as I can tell, but I'm stuck 800x600.  Xorg.log shows no validated 1024x768 modes.

The wierd thing is I still have Edgy on another partition, and I've got the nvidia driver running at 1024x768 over there...I just wish I could remember all the steps I did to get that one going...maybe I got the driver from the nvidia website?

The only thing I noticed different between my Edgy and Feisty xorg.conf files was that Edgy has the following options:

    Option         "AddARGBGLXVisuals" "True"
    Option         "AllowGLXWithComposite" "True"
    Option         "RenderAccel" "True"

I added those to the Feisty file, but it didn't help.

Tim - how/where did you add the horiz & vert rates to xorg.conf?  I've got a set of depths and resolutions in there, but I don't see any rates in my xorg.conf file.

I'm following [this thread]("http://ubuntuforums.org/showthread.php?t=417716") for more information.

---

### Post by Tim Hollen on 2007-04-30
well first I looked up the settings for the monitor. Then up then in xorg.conf like this.

Section "Monitor"
    Identifier     "Dell"
    Option         "DPMS"
    HorizSync	30 - 85
    VertRefresh	48 - 120
    DisplaySize 312 234
   
EndSection

a discription of what the peramaters should be can be found in the help file under xorg

---

