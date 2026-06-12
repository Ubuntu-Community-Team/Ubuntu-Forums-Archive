---
title: "Nvidia 7600GT using something other then vesa"
date: 2007-10-24
forum: Multimedia &amp; Video
---

### Post by DarthRaccoon on 2007-10-24
Has anyone been able to get X to run in ubuntu on an Nvidia 7600GT using anything other then the vesa driver? If so, could you please post what steps you took? I have been trying to resolve this issue on my machine since 7.04 came out (running 7.10 now). I've got an eVga geforce 7600gt pci-e card with a vga out, a dvi out, and an s-video out. My monitor is hooked up to the DVI out port on the card. My monitor is an Acer AL2216W 22" LCD Widescreen. The card seems to be fine as I've had windows xp running on it flawlessly for some time now.

When I run the ubuntu live cd and tell it to start/install ubuntu, I get the ubuntu progress bar as everything is loading and then once X starts it goes to black and the monitor gives me the message that its not getting a video signal. I can install ubuntu using the safe graphics mode, but this uses the vesa driver and thats not going to cut it for me. I have tried then installing the nvidia restricted driver from within ubuntu, which seems to run ok but when I reboot I'm getting the same problem. I've completely blown away my install, reinstalled ubuntu in safe graphics mode, then downloaded Nvidia's proprietary driver directly from their site and installed that, no dice. I have also tried using the Envy installer to the same result.

I'm at my wits end here. I *really* want to be running ubuntu for everything I do thats not gaming, so I'm almost ready to go out and buy a different video card but I would obviously like to avoid that option if at all possible. Any help/insight would be greatly appreciated!

---

### Post by Qwerty_ on 2007-10-25
I wonder if reconfigureing your xserver might help

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by DarthRaccoon on 2007-10-25
Unfortunately I've done that a couple of times.  I had to in order to get the precise refresh rates and resolution options for my monitor in there after installing the drivers.

---

### Post by disturbed1 on 2007-10-25
Sure, opened restricted driver manager, clicked enable for nVidia-glx, then rebooted.

```
 less Xorg.0.log | grep nVidia
(**) |   |-->Device "nVidia Corporation G70 [GeForce 7600 GT]"
(--) PCI:*(1:0:0) nVidia Corporation G70 [GeForce 7600 GT] rev 161, Mem @ 0xe0000000/24, 0xd0000000/28, 0xe1000000/24, I/O @ 0x9000/7

``````

 xvinfo
X-Video Extension version 2.2
screen #0
  Adaptor #0: "NV17 Video Texture"
    number of ports: 32
    port base: 355

``````

 glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4

``````
uname -a
Linux disturbed 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux

```

**IF I** were to troubleshoot this, I'd delete/xorg.conf, boot into single user mode, apt-get install nvidia-glx-new, reboot again into single user mode, nvidia-glx-config enable. Reboot again.

I don't believe all the reboots are needed, but it only adds 5-10 seconds, so better safe than sorry.

---

### Post by DarthRaccoon on 2007-10-25
I'll give it another go tonight.  Just out of curiosity, is your 7600GT dual head with a VGA and a DVI?  I had a thought that maybe when X is starting back up its outputting to the wrong head as i have my monitor hooked up to the DVI out, and I *think* that is the second head on the card.  I'm going to try modifying the screen option in my xorg.conf file to indicate screen 1 instead of 0 and see if that makes a difference.

---

### Post by disturbed1 on 2007-10-25
It has DE15*, DVI, and S-Video out. I use good 'ol DE15 for my CRT, never an LCD here ;).


*commonly, yet, incorrectly called DB15 :)

If it displays with the vesa driver, no need to *blindly* monkey around with xorg.conf. I find that 99.9% of peoples graphics problems come from editing this file. It's better to read ***less /var/log/Xorg.0.log*** to correctly identify the problem, than to blinding add/remove options in the xorg.conf file itself.

You could even post that file here, and someone should be able to offer a little diagnosis.

---

### Post by scorp123 on 2007-10-25
> **DarthRaccoon said:**
>  Has anyone been able to get X to run in ubuntu on an Nvidia 7600GT using anything other then the vesa driver?  Yes.

> **DarthRaccoon said:**
>  If so, could you please post what steps you took?  The "Restricted Drivers" thingie took care of everything. I don't remember that I had to do much, except adjust my xorg.conf a slight bit.

> **DarthRaccoon said:**
>  My monitor is an Acer AL2216W 22" LCD Widescreen  Mine is an Acer AL2017 widescreen, 20" LCD. Slightly smaller than what you have but other than that I guess they are very much the same?

This is my /etc/X11/xorg.conf file ... maybe this will help? (e.g. compare it to your's?)

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
        Fontpath        "/usr/share/fonts/X11/misc"
        Fontpath        "/usr/share/fonts/X11/cyrillic"
        Fontpath        "/usr/share/fonts/X11/100dpi/:unscaled"
        Fontpath        "/usr/share/fonts/X11/75dpi/:unscaled"
        Fontpath        "/usr/share/fonts/X11/Type1"
        Fontpath        "/usr/share/fonts/X11/100dpi"
        Fontpath        "/usr/share/fonts/X11/75dpi"
        # path to defoma fonts
        Fontpath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load            "i2c"
        Load            "bitmap"
        Load            "ddc"
        Load            "extmod"
        Load            "freetype"
        Load            "glx"
        Load            "int10"
        Load            "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "ch"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"        "/dev/input/mice"
        Option          "Protocol"      "ImPS/2"
        Option          "ZAxisMapping"  "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "stylus"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "eraser"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "cursor"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "Generic Video Card"
        Driver          "nvidia"
        Busid           "PCI:1:0:0"
        Option          "AddARGBVisuals"        "True"
        Option          "AddARGBGLXVisuals"     "True"
        Option          "NoLogo"        "True"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        DisplaySize     338    270
        HorizSync       29.0 - 81.0
        VertRefresh     43.0 - 76.0

EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Card"
        Monitor         "Generic Monitor"
        Option          "XAANoOffscreenPixmaps" "true"
        Option          "DRI" "true"
        Option          "AllowGLXWithComposite" "True"
        Option          "RenderAccel" "True"
        Option          "AddARGBGLXVisuals" "True"
        Defaultdepth    24
        SubSection "Display"
                Depth   1
                Modes      "1400x1050" "1280x1024" "1280x960" "1280x800" "1152x864" "1280x768" "1024x768" "1280x600" "1024x600" "800x600" "768x576" "640x480"
        EndSubSection
        SubSection "Display"
                Depth   4
                Modes      "1400x1050" "1280x1024" "1280x960" "1280x800" "1152x864" "1280x768" "1024x768" "1280x600" "1024x600" "800x600" "768x576" "640x480"
        EndSubSection
        SubSection "Display"
                Depth   8
                Modes      "1400x1050" "1280x1024" "1280x960" "1280x800" "1152x864" "1280x768" "1024x768" "1280x600" "1024x600" "800x600" "768x576" "640x480"
        EndSubSection
        SubSection "Display"
                Depth   15
                Modes      "1400x1050" "1280x1024" "1280x960" "1280x800" "1152x864" "1280x768" "1024x768" "1280x600" "1024x600" "800x600" "768x576" "640x480"
        EndSubSection
        SubSection "Display"
                Depth   16
                Modes      "1400x1050" "1280x1024" "1280x960" "1280x800" "1152x864" "1280x768" "1024x768" "1280x600" "1024x600" "800x600" "768x576" "640x480"
        EndSubSection
        SubSection "Display"
                Depth   24
                Modes      "1400x1050" "1280x1024" "1280x960" "1280x800" "1152x864" "1280x768" "1024x768" "1280x600" "1024x600" "800x600" "768x576" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"
        Inputdevice     "stylus"        "SendCoreEvents"
        Inputdevice     "cursor"        "SendCoreEvents"
        Inputdevice     "eraser"        "SendCoreEvents"
        Option          "AIGLX" "on"
EndSection

Section "DRI"
        Mode    0666
EndSection

Section "Extensions"
        Option          "Composite" "Enable"
EndSection 
```

---

