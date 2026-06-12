---
title: "Can't boot with S-Video only"
date: 2010-04-26
forum: Mythbuntu
---

### Post by dragoster on 2010-04-26
I have a freshly installed mythbuntu 10.04 RC frontend. Connected to the graphics card I have an LCD monitor connected via DVI and a TV connected via S-Video. I have configured the system to only display on the TV, which is my ultimate goal. 

However, if I disconnect the LCD monitor and then restart, the system will not boot. I know the S-Video connection works because I see the Bios screens, but when ubuntu is being loaded from the hard drive, the system hangs with a blinking cursor. If I press enter I get the error "NO BOOTABLE DISK FOUND", or something similar. If the DVI monitor is connected, the Bios and initial boot (until the mouse cursor appears, which is I assume when gdm starts) happen on the monitor, and then, the video switches to the the S-Video TV. My goal is to have the system boot and display on the S-Video TV only.

I need help figuring this out, but for starters I can suspect two things:

1) Some ill configured xorg.conf where the SVideo autodetection doesn't work. Here are the pertinent sections in my xorg.conf file as of now. I tried a bunch of modifiers with no luck. If you see anything obviously wrong I would appreciate your input.

```
Section "Monitor"
    # HorizSync source: builtin, VertRefresh source: builtin
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "TV-0"
#    HorizSync       28.0 - 55.0
#    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
        BoardName      "GeForce 8600 GTS"
        Option  "TVOutFormat" "SVIDEO"
        Option  "TVStandard"    "NTSC-M"
        Option  "UseEvents"     "True"
        Option  "AddARGBVisuals"        "1"
        Option  "AddARGBGLXVisuals"     "1"
        Option  "NoLogo"        "1"
        Option  "UseDisplayDevice"      "TV"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "nvidia-auto-select +0+0"
    Option         "ConnectedMonitor"      "TV"
SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

2) Since I don't even get to see the GRUB menu when the computer is connected to the S-Video TV only, there could some misconfiguration within grub. I don't know much about grub, but here's my current default grub file.

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT=""
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```

Again, this is a fresh MythBuntu install, so if we manage to figure it out we should update some of the install defaults to prevent this to happen to others. I should mention that I've observed the same problem with the MythBuntu 9.10 version.

Thanks,
-D

---

### Post by ian dobson on 2010-04-27
Hi,

Sounds alot like a BIOS problem, the error "NO BOOTABLE DISK FOUND" means the bios has not found a bootable device.

I would check if there's a bios update available for your motherboard or maybe make a VGA dongle to fool the VGA card/motheboard into thinking a monitor is attached.

Have a look here for the wiring of a VGA dongle [http://forums.techpowerup.com/showthread.php?t=86507](http://forums.techpowerup.com/showthread.php?t=86507)

Regards
Ian Dobson

---

### Post by dragoster on 2010-04-27
Thanks Ian,

The DVI to VGA terminator was next on my list. I will steal some resistors from work and I will try the trick tonight.

D

---

### Post by ian dobson on 2010-04-27
Hi,

I have a box at work that doesn't boot if no monitor is attached. I made a VGA dongle and now it boots without a mouse/keyboard/VGA attached.

Regards
Ian Dobson

---

### Post by nickrout on 2010-04-27
Also there might be a bios setting to bypass the monitor detection. But it's probably called something obscure...

---

### Post by dragoster on 2010-04-27
Hey guys,

Although not the most elegant solution, the DVI-VGA dongle worked. Thanks!

-D

---

