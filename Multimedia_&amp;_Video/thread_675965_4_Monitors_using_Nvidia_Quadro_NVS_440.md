---
title: "4 Monitors using Nvidia Quadro NVS 440"
date: 2008-01-23
forum: Multimedia &amp; Video
---

### Post by quake101 on 2008-01-23
Hello,

I'm currently having problems enabling multiple monitors using a Nvidia Quadro NVS 440 video card. I've installed the "new" nvidia driver and configured xorg.conf (please see below) but I'm only able to use 1 monitor successfully. :( I hope you guys and help me out, I'm starting to go crosseyed looking at the xorg.conf

**lspci | grep -i vga**:
```

09:00.0 VGA compatible controller: nVidia Corporation Quadro NVS 440 (rev a2)
0a:00.0 VGA compatible controller: nVidia Corporation Quadro NVS 440 (rev a2)

```

**Non-working xorg.conf (trying to get 2 monitors working)**:
```

Section "ServerLayout"
	Identifier	"Default Layout"
	screen 0 "Default Screen" 0 0
	screen 1 "Screen1" rightof "Default Screen"
	Option		"Xinerama"	"true"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
EndSection

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
EndSection

Section "Monitor"
    Identifier     "DELL 1708FP 0"
    HorizSync       30.0 - 70.0
    VertRefresh     50.0 - 160.0
    Option         "DPMS"
EndSection

Section "Device"
	Identifier	"NVIDIA Quadro NVS 440 0"
	Busid		"PCI:10:0:0"
	Driver		"nvidia"
	Screen	0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Quadro NVS 440 0"
	Monitor		"DELL 1708FP 0"
	Defaultdepth	24
	Option		"UseFBDev"	"true"
	SubSection "Display"
		Depth	24
	        Modes      "1280x1024" "1024x768" "800x600"
	EndSubSection
EndSection

Section "Monitor" 
	Identifier	"DELL 1708FP 1"
	HorizSync       30.0 - 70.0
	VertRefresh     50.0 - 160.0
	Option		"DPMS"
EndSection

Section "Device" 
	Identifier	"NVIDIA Quadro NVS 440 1"
	Busid		"PCI:10:0:0"
	Driver		"nvidia"
	Screen	1
EndSection

Section "Screen" 
	Identifier	"Screen1"
	Device		"NVIDIA Quadro NVS 440 1"
	Defaultdepth	24
	Monitor		"DELL 1708FP 1"
	Option		"UseFBDev" "true"
	SubSection "Display"
		Depth	24
	Modes		"1280x1024" "1024x768" "800x600"
	EndSubSection
EndSection

#Section "Monitor"
#	Identifier	"DELL 1708FP 2"
#	HorizSync       30.0 - 70.0
#	VertRefresh     50.0 - 160.0
#	Option		"DPMS"
#EndSection

#Section "Device" 
#	Identifier	"NVIDIA Quadro NVS 440 2"
#	Boardname	"NVIDIA Quadro NVS 440"
#	Busid		"PCI:9:0:0"
#	Driver		"nvidia"
#	Screen	0
#EndSection

#Section "Screen" 
#	Identifier	"Screen2"
#	Device		"NVIDIA Quadro NVS 440 2"
#	Defaultdepth	24
#	Monitor		"DELL 1708FP 2"
#	Option		"UseFBDev" "true"
#	SubSection "Display"
#		Depth	24
#	Modes		"1280x1024" "1024x768" "800x600"
#EndSection

```

**Current working xorg.conf (1 Monitor)**:
```

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
    Identifier     "DELL 1708FP"
    HorizSync       30.0 - 70.0
    VertRefresh     50.0 - 160.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Quadro NVS 440"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Quadro NVS 440"
    Monitor        "DELL 1708FP"
    DefaultDepth    24
    Option         "UseFBDev" "true"
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600"
    EndSubSection
EndSection

```

---

### Post by quake101 on 2008-01-23
I have fixed my problem... ](*,)

After reviewing my Xorg.0.log file, I quickly noticed that PCI:9:0:0 is GPU0 and should be used for my first 2 monitors and PCI:10:0:0 should be used as my 2nd 2 monitors. (doh) Once I change that around and logged out, POOF I had my first 2 monitors. :)

](*,) ](*,)

---

### Post by quake101 on 2008-01-29
Today I got around to hooking up the 3rd and 4th monitors and was unsuccessful getting them to work. I believe the problem is with the BusID PCI (0a:00.0), I have tried PCI:10:0:0 in the xorg.conf with no success. Please see below.

From Xorg.0.log
```

(WW) NVIDIA: No matching Device section for instance (BusID PCI:10:0:0) found

```

lspci | grep -i vga
```

09:00.0 VGA compatible controller: nVidia Corporation Quadro NVS 440 (rev a2)
0a:00.0 VGA compatible controller: nVidia Corporation Quadro NVS 440 (rev a2)

```

---

### Post by quake101 on 2008-01-29
Just adding more info to the thread.

cat /proc/driver/nvidia/cards/*
```

Model:           Quadro NVS 440
IRQ:             16
Video BIOS:      05.43.02.88.03
Card Type:       PCI-E
DMA Size:        39 bits
DMA Mask:        0x7fffffffff
Bus Location:    09.00.0

Model:           Quadro NVS 440
IRQ:             17
Video BIOS:      05.43.02.88.03
Card Type:       PCI-E
DMA Size:        39 bits
DMA Mask:        0x7fffffffff
Bus Location:    0a.00.0

```

---

### Post by quake101 on 2008-01-29
cat /proc/interrupts
```

           CPU0       CPU1       CPU2       CPU3       
  0:      34618      34331      34090      34105   IO-APIC-edge      timer
  1:          0          2          0          0   IO-APIC-edge      i8042
  6:          1          2          2          0   IO-APIC-edge      floppy
  8:          0          0          0          0   IO-APIC-edge      rtc
  9:          0          0          0          0   IO-APIC-fasteoi   acpi
 14:       2795       2825       2824       2817   IO-APIC-edge      libata
 15:          0          0          0          0   IO-APIC-edge      libata
 16:       5724       5679       5938       5813   IO-APIC-fasteoi   eth0, HDA Intel, nvidia
 17:         58         61         59         63   IO-APIC-fasteoi   nvidia
 18:        250        244        263        242   IO-APIC-fasteoi   uhci_hcd:usb4
 20:          0          0          0          0   IO-APIC-fasteoi   ahci
 21:       1429       1486       1461       1472   IO-APIC-fasteoi   uhci_hcd:usb1, ehci_hcd:usb3
 22:        189        149        150        150   IO-APIC-fasteoi   uhci_hcd:usb2
 23:          0          0          0          0   IO-APIC-fasteoi   uhci_hcd:usb5
 24:       2252       2264       2256       2316   IO-APIC-fasteoi   ioc0
NMI:          0          0          0          0 
LOC:     137003     136987     136959     136675 
ERR:          0

```

Looks like eth0 and the 2nd video head are on the same IRQ (16). Now I gotta fix it.

---

### Post by quake101 on 2008-01-30
Ok, I'm really lost now. I removed and eth0 from the machine and still no go. I don't think it's an IRQ thing now. Any help? :confused:

Btw, here is my current xorg.conf (I commented out the 3rd and 4th monitors and only running the first 2 monitors)
```

Section "ServerLayout"
	Identifier	"Default Layout"
	screen 0 "Default Screen" 0 0
	screen 1 "Screen1" rightof "Default Screen"
#	screen 2 "Screen2" rightof "Screen1"
#	screen 3 "Screen3" rightof "Screen2"
	Option		"Xinerama"	"true"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
EndSection

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
EndSection

Section "Monitor"
    Identifier     "DELL 1908FP 0"
    HorizSync       30.0 - 70.0
    VertRefresh     50.0 - 160.0
    Option         "DPMS"
EndSection

Section "Device"
	Identifier	"NVIDIA Quadro NVS 440 0"
	Busid		"PCI:9:0:0"
	Driver		"nvidia"
	Screen	0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Quadro NVS 440 0"
	Monitor		"DELL 1908FP 0"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
	        Modes      "1280x1024" "1024x768" "800x600"
	EndSubSection
EndSection

Section "Monitor" 
	Identifier	"DELL 1908FP 1"
	HorizSync       30.0 - 70.0
	VertRefresh     50.0 - 160.0
	Option		"DPMS"
EndSection

Section "Device" 
	Identifier	"NVIDIA Quadro NVS 440 1"
	Busid		"PCI:9:0:0"
	Driver		"nvidia"
	Screen	1
EndSection

Section "Screen" 
	Identifier	"Screen1"
	Device		"NVIDIA Quadro NVS 440 1"
	Defaultdepth	24
	Monitor		"DELL 1908FP 1"
	SubSection "Display"
		Depth	24
	Modes		"1280x1024" "1024x768" "800x600"
	EndSubSection
EndSection

#Section "Monitor"
#	Identifier	"DELL 1908FP 2"
#	HorizSync       30.0 - 70.0
#	VertRefresh     50.0 - 160.0
#	Option		"DPMS"
#EndSection

#Section "Device" 
#	Identifier	"NVIDIA Quadro NVS 440 2"
#	Busid		"PCI:10:0:0"
#	Driver		"nvidia"
#	Screen	0
#EndSection

#Section "Screen"
#	Identifier	"Screen2"
#	Device		"NVIDIA Quadro NVS 440 2"
#	Defaultdepth	24
#	Monitor		"DELL 1908FP 2"
#	SubSection "Display"
#		Depth	24
#	Modes		"1280x1024" "1024x768" "800x600"
#EndSection

#Section "Monitor"
#	Identifier	"DELL 1908FP 3"
#	HorizSync       30.0 - 70.0
#	VertRefresh     50.0 - 160.0
#	Option		"DPMS"
#EndSection

#Section "Device" 
#	Identifier	"NVIDIA Quadro NVS 440 3"
#	Busid		"PCI:10:0:0"
#	Driver		"nvidia"
#	Screen	1
#EndSection

#Section "Screen" 
#	Identifier	"Screen3"
#	Device		"NVIDIA Quadro NVS 440 3"
#	Defaultdepth	24
#	Monitor		"DELL 1908FP 3"
#	SubSection "Display"
#		Depth	24
#	Modes		"1280x1024" "1024x768" "800x600"
#EndSection

```

---

### Post by quake101 on 2008-01-30
I fixed it and feel like a fool now. I used "Nvidia Settings" to configure my screens and it worked the first time. :)

---

