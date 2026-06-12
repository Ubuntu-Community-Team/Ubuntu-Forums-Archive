---
title: "Custom resolution for TV Screen"
date: 2008-09-10
forum: Multimedia Software
---

### Post by tykos on 2008-09-10
Hi,i need to configure my media-center ubuntu box.
I've got a sony bravia kdl-32s[something], native resolution 1366x768.
I installed nvidia-config,but only resolutions available seem to be these:

   1920x1080      50.0     51.0  
   1280x720       52.0*    53.0  
   800x600        54.0  
   720x480        55.0     56.0  
   640x480        57.0     58.0  
   400x300        59.0  
   320x240        60.0  

I'm trying with 1280x720, but some pixels are missing from every side (taskbars are completely hidden).

What should i do?

thanks
Michele

---

### Post by NT4usB on 2008-09-10
(inatall and) run ```
sudo nvidia-settings
```
See if that will get you what you need.
Otherwise, we can manually configure your xorg.conf but that requires some comfort using the command line (no GUI.)

---

### Post by tykos on 2008-09-11
> **NT4usB said:**
> (inatall and) run ```
sudo nvidia-settings
```
See if that will get you what you need.
Otherwise, we can manually configure your xorg.conf but that requires some comfort using the command line (no GUI.)

I already installed nvidia-settings, but the only resolutions are the one listed above.
In windows there is a tool (nvidia, i think) that allow to redefine the visible area, without changing resolution: it works like the buttons on the monitor (or the wheels, in old monitors).

Nothing similar in linux?

Michele

---

### Post by NT4usB on 2008-09-11
Only tool I know of is nvidia-settings.
I usually go straight to modifying xorg.conf to solve video issues. I learned early on how to work in the dark (command line) so I'm comfortable with a black screen until I get it working...
nvidia-settings to get close then tweak xorg until I like what I see.
Maybe someone else will post with a GUI way to get it going.
Or, you want to learn command line?

---

### Post by tykos on 2008-09-12
> **NT4usB said:**
> Only tool I know of is nvidia-settings.
I usually go straight to modifying xorg.conf to solve video issues. I learned early on how to work in the dark (command line) so I'm comfortable with a black screen until I get it working...
nvidia-settings to get close then tweak xorg until I like what I see.
Maybe someone else will post with a GUI way to get it going.
Or, you want to learn command line?

no problem with command line.
I'll post my xorg.conf later, but i think it's a little messed-up by nvidia-settings tool.

Michele

---

### Post by cariboo on 2008-09-12
Have you tried:

```
displayconfig-gtk
```

with your tv connected?

Jim

---

### Post by tykos on 2008-09-12
> **cariboo907 said:**
> Have you tried:

```
displayconfig-gtk
```

with your tv connected?

Jim

sure, but the only available resolutions are listed above.

Here's my xorg.conf file:
```
Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "SONY TV"
    HorizSync       30.0 - 49.0
    VertRefresh     57.0 - 63.0
    Option         "DPMS"
    Option         "UseEDID" "True"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "SONY TV"
    HorizSync       14.0 - 46.0
    VertRefresh     48.0 - 62.0
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce FX 5200"
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce FX 5200"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"

# Removed Option "metamodes" "CRT: nvidia-auto-select +0+0, DFP: 1366x768 +1360+0"
# Removed Option "TwinView" "1"
# Removed Option "TwinViewXineramaInfoOrder" "DFP-0"
# Removed Option "metamodes" "CRT: 1024x768 +0+0, DFP: 1280x720 +0+0"
# Removed Option "metamodes" "CRT: 1280x768 +0+0"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "NoTwinViewXineramaInfo"
    Option         "TwinView" "1"
    Option         "metamodes" "CRT: 1280x720 +0+0, DFP: 1280x720 +0+0"
    SubSection     "Display"
        Depth       24
	Option 	    "metamodes" "DFP: 1280x720 +0+0"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "DFP: 1280x768 +0+0"
EndSection
```

My goal is to connect tv with an dvi-hdmi cable (also vga connection is available, but i would like the other one, because of quality and so on)

Michele

---

