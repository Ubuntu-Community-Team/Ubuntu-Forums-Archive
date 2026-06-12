---
title: "NVidia Card Not Working"
date: 2010-02-20
forum: Multimedia Software
---

### Post by josesanders on 2010-02-20
I had to replace my video card.  When I put the new one in, I uninstalled the old NVidia driver and installed the new driver automatically.  It won't start the X server.

Here is the relevant section of xorg.conf:

Section "Device"
        Identifier      "Configured Video Device"
        Boardname       "vesa"
        Busid           "PCI:0:2:0"
        Driver          "nvidia"
        Screen  0
        Option          "NoLogo"        "True"
EndSection


Here is the relevant section when I run the command lspci -v:

01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 420] (rev a3) (prog-if 00 [VGA controller])
	Subsystem: nVidia Corporation Unknown device 015a
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at f1000000 (32-bit, non-prefetchable) [size=16M]
	Memory at f4000000 (32-bit, prefetchable) [size=64M]
	Memory at f3d00000 (32-bit, prefetchable) [size=512K]
	[virtual] Expansion ROM at f3d80000 [disabled] [size=128K]
	Capabilities: <access denied>


I'm not new to linux, but with this video stuff, I'm totally lost.  Any suggestions at all would be greatly appreciated.

---

### Post by rsnow on 2010-02-20
I don't know if this will help but I just resolved this issue on 2 of my machines so here is what I did:

Click on System/Administration/Hardware Drivers

When the window opens showing your choices of nvidia drivers, select one and click on enable this driver.

Note: I had better luck not using the recommended driver. Apparently my cards are too old to work well with the latest greatest drivers. Anyway both machines are doing good now. Oh, and I also made sure not to have Compiz activated. Hope this helps.

---

### Post by josesanders on 2010-02-20
Thanks for the response.  Unfortunately, when I try to enable the hardware driver that way, it just gives me one option, and it doesn't work.  I also tried to install it with Envy.

---

