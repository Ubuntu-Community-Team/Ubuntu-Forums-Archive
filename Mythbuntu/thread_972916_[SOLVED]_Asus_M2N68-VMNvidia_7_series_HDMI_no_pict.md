---
title: "[SOLVED] Asus M2N68-VM/Nvidia 7 series HDMI no picture"
date: 2008-11-06
forum: Mythbuntu
---

### Post by laffinet on 2008-11-06
Hi

I've just build my first HTPC using above motherboard and installing Mythbuntu 8.10. I'm still at the early stages but right now I'm having difficulties getting the HDMI output to work.

Mythbuntu boots up alright, screen works, but once I get past the splash screen it seems to shut off the HDMI output and my TV displays "no signal".

If I go into the nvidia settings I can pick the HDMI connection as a separate display and everything works but next time I boot I have the same problem. I suspect that the changes don't get written to the X-configuration file (is that xorg.conf ?). While there is the option of "save to X configuration file", everytime I click it the whole setup window closes, which I suspect is a crash and nothing gets written to the file. If I knew what I could edit the file manually, but I don't know what should.

But since I'm not that experienced it could be something different.

Any ideas ?

Thanks in advance.

Edit:
I launched nvidia-settings from the terminal and as soon as I hit "save to X configuration file" the application closes and the last line in the terminal is "sh: pkg-config: not found". As I said above, looks like it crashes and nothing gets written to the configuration file.

---

### Post by laffinet on 2008-11-06
Okay, I got it to work. Not exactly the sophisticated way but it did the trick: I reinstalled Mythbuntu with the HDMI connected and it detected and configured everything alright. Had to manually edit the xorg.conf to get the right resolution and aspect ratio but now everything is fine.

---

### Post by jonwestin on 2009-02-14
hey mate. i have the kinda the same problem, although nvidia settings doesnt seem to find the hdmi at all.. do you have any idea if there is an easier way of adding it cause i dont really wanna reinstall :) i guess i should add it to xorg but i dont know where to begin...

cheers
joenas

---

### Post by laffinet on 2009-02-14
Don't know how to fix it without re-installing.

Here's my xorg.conf, maybe that'll help or point you in the right direction:

```

Section "Monitor"
	Identifier     "Configured Monitor"
EndSection

Section "Screen"
	Identifier     "Default Screen"
	Device         "Configured Video Device"
	Monitor        "Configured Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth       24
		Modes      "1360x768"
	EndSubSection
EndSection

Section "Module"
	Load           "glx"
EndSection

Section "Device"
	Identifier     "Configured Video Device"
	Option         "DPI" "100x100"
	Option         "UseEvents" "true"
	Option		"XvmcUsesTextures" "false"
	Option		"NVAGP" "3"
	Option         "AddARGBVisuals" "1"
	Option         "AddARGBGLXVisuals" "1"
	Option          "ConnectedMonitor"      "TV"
	Option         "TVOutFormat" "COMPONENT"
	Option         "TVStandard" "HD1080i"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection
```

---

