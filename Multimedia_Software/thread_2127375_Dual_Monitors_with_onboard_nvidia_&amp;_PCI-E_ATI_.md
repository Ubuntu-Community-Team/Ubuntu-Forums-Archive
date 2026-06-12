---
title: "Dual Monitors with onboard nvidia &amp; PCI-E ATI Card"
date: 2013-03-19
forum: Multimedia Software
---

### Post by bazsound on 2013-03-19
I just got given an ATI Radion Saphire HD 3650 card. This card does dual monitors and it apperently works in linux, but at the moment i only have 1 dvi to vga connector, im ordering another one soon, but it would be cool to be able to do this, and know how as it would mean i could potentially have 3 monitors setup.

Ive searche high and low, and found a couple of posts that it had been done, but that was way back in 8.04 and apperently after that it broke.

anyway.

Ive been trying coutnless things, different x org configs.

So far, i get onboard video on boot, then both screens blank during bootup until login screen and i get the ati card, login fine. On shutdown i get the nvidia monitor. weird.

after much playing, with ending up getting both blank screens and having to boot into safe mode, i gave up delted my xorg.conf to go back to normal (as i did previously) and now im back to the nvidia adapter, no drivers changed or installed, this did not previously do this, after deleting the xorg, id get the ati working again.

Ubuntu 12.10 64 bit
00:0d.0 VGA compatible controller: NVIDIA Corporation C61 [GeForce 6100 nForce 405] (rev a2)
02:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV630 [Radeon HD 3600 Series]

Motherboard supports both adapters at the same time, they defintaly work, as i was getig 1 adapter when logged in, then the other on shutdown.

Installing the ati drivers automatically removes the nvidia drivers, which is kind of a problem, the open source neouva is installed though.

So far, creating an xorg to define server layout, the screens and devices results in both screens blank.

```
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "InputDevice"

    # generated from default
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/psaux"
    Option        "Emulate3Buttons" "no"
    Option        "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Unknown"
    ModelName    "Unknown"
    HorizSync    28.0 - 33.0
    VertRefresh  43.0 - 72.0
    Option        "DPMS"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Monitor"
    Identifier   "0-CRT1"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1280x1024"
    Option        "TargetRefresh" "75"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Device"
    Identifier  "Device0"
    Driver      "nvidia"
    VendorName  "NVIDIA Corporation"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    Option        "Monitor-CRT1" "0-CRT1"
    BusID       "PCI:2:0:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Device0"
    Monitor    "Monitor0"
    DefaultDepth     24
    SubSection "Display"
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection


```

I dont know what the nvidia section is still doing there, this was my xorg after i installed the ATI drivers,

---

### Post by bazsound on 2013-03-20
Just an update. i really needed to start with a fresh install, so downloaded 12.04 ubuntu (not studio) Changed my card to pcie-pci-igb and installed 12.04. Well during the install while i had the installer screen on my monitor attached to the ati card, the monitor on the onboard card nvidia was showing the ubuntu splash, which was startic, and on shutdown the animation was working.

once the system booted up however, the ati card is the only working display.

I've not had a chance to start playing yet with my xorg, but since both screens were working at the same time during install, i should be able to get 2 displays working, even if its not 1 screen stretched over 2 screens, though i dont see why not.

This is the output of lshw -c video
 >  *-display               
       description: VGA compatible controller
       product: RV630 [Radeon HD 3600 Series]
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:43 memory:c0000000-cfffffff memory:dfff0000-dfffffff ioport:e000(size=256) memory:dffc0000-dffdffff
  *-display
       description: VGA compatible controller
       product: C61 [GeForce 6100 nForce 405]
       vendor: NVIDIA Corporation
       physical id: d
       bus info: pci@0000:00:0d.0
       version: a2
       width: 64 bits
       clock: 66MHz
       capabilities: pm msi vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:22 memory:de000000-deffffff memory:b0000000-bfffffff memory:dd000000-ddffffff memory:dfec0000-dfedffff




So both adapters are recognised and it appears that the onboard is using the nvidia driver.

So now that i have a fressh install, i just need to build an xorg config file that hopefully doesnt break x.

---

### Post by bazsound on 2013-03-20
The best i managed was to get lightdm running on 1 screen, and a terminal in the other.

but as far as getting both screens to show the gui, well im getting good at blank screens.

It would be helpfull if i could look at my xorg configuration in its current working state with the ati card running so i can have a reference, but there is no xorg.conf. and ive searched and searched on how to find it.

also i booted up in a live usb stick, and ran Xorg-config, which generated an xorg file, but with 8 cards 8 monitors and 8 screens. i deleted all the non relevent ones to leave just the nivida card, and radeon card, and deleted the extra screens and monitors, made sure all the identiefers mached up. this actually broke my system to the point i couldnt even boot up in safe graphics mode. I had to use the live cd to bootup and remove the bad xorg.conf

There must be a way, both adapters are present at the same time, they have shown to work at the same time, or be able to switch from 1 to the other somehow.

If this is in the wrong section, could a mod move it to the right forum?

---

### Post by bazsound on 2013-03-21
Ok so after much playing  i have gotten both screens working at the same time however, first screen is my desktop works fine, the 2nd screen is a terminal, i had this before execpt the 2nd screen would only come up when ctr alt f to a tty consol then my first screen would go blank and the 2nd would have a terminal, then ctr alt f7 to go back to my desktop, the 2nd screen would freeze but still show the terminal.

So i played with xorg, changed the driver to nv, and now both screens are active, but 2nd screen is a terminal and my keyboard works in the 2nd while also in the first. changing to tty doesnt blank my first display, and is still active.

so keyboard and mouse is working in both screenss. but 2nd screen has no desktop just terminal.

So yay they both work at the same time.

> Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
    Screen           "nvidiascreen" Rightof "aticonfig-Screen[0]-0"
        
EndSection

Section "Module"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection



Section "Monitor"
    Identifier   "0-CRT1"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1280x1024"
    Option        "TargetRefresh" "75"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection


Section "Monitor"
        Identifier   "nvidiamonitor"
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    BusID       "PCI:2:0:0"
EndSection

Section "Device"
    Identifier   "nvidiadevice"
    Driver        "nv"
    BusId        "PCI:0:13:0"
EndSection    

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    Monitor       "0-CRT1"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "nvidiascreen"
    Device     "nvidiadevice"
        Monitor    "nvidiamonitor"
    DefaultDepth     24
    SubSection "Display"
        Depth     24
    EndSubSection
EndSection



---

### Post by bazsound on 2013-03-23
Ok so i got another DVI-vga connector, installed fglrx-legacy drivers for my card and i know have dual monitors working perfectly with the ATI, at the moment onboard nvidia is disabled. i have also upgraded my ram from 3gb (1gb and 2gb module) to 4gh dual channel (2 x 2gb sticks).

So im not really bothered about being able to stretch across 3 monitors. But it would be nice to have a third monitor even if its running as a seperate desktop. It would co me in handy for recording, having a screen facing the other way to display lyrics.

---

### Post by Mark Phelps on 2013-03-23
Just so you know ... AMD dropped restricted Linux driver support for their HD 2x/3x/4x series last summer.  The release you're running now (12.04) is the last one that will support AMD restricted drivers.  They are not supported in 12.10 due to a change in the X-server version.

---

### Post by bazsound on 2013-03-23
yeah i found that out, i was running 12.10 and had to use a repo to downgrade the x-server, i had to do the same in 12.04 aswell and downgrade x.

I havnt tried enabling my onboard video yet, since theres not much point without another vga cable. I cant seem to find very much information, but the information i have found has suggested it is posisble to run displays with at & nvidia power screens on the same linux machine, though nothing specific to my configuration, as im wanting to power 2 monitors form the ati (which is already setup) and power a 3rd form the onboard nvidia.

both adapters are able to be present without conflicting, it is however tricky with drivers, since nvidia propriety drivers will not co exist with ati. i have now moved to xfce instead of unity, so maybe ill actually get a display instead of just being able to get a terminal with the nvidia adapter.

---

