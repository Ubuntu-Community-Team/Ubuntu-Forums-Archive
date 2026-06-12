---
title: "cannot change screen resolution  in Ubuntu 8.04"
date: 2009-08-14
forum: Multimedia Software
---

### Post by malbojet on 2009-08-14
Hello everybody, I'm new in the Linux World, I did install <Ubuntu 8.04> a couple of days ago and I feel a little lost; however reading on the Internet I have found solutions to some of my problems. (Like programs that I used to work on Windows: EMESENE and others), but the fact is that I cannot change the screen resolution, it only appears 800x600 and 600x400 options. The screen wroks good in Windows with a resolution of 1024x768.

Please somebody help me, I have been reading a lot but I still haven't found the solutions for this. I found the command: "lspci" but I don't know what to do with the console information

I attach the copy of <lspci-v> and the copy of my file <xorg.conf>

_______________________________________________

Hola a todos, soy nuevo en el mundo Linux, instalé Ubuntu 8.04 hace un par de días y me siento un poco perdido, sin embargo leyendo por la Internet he encontrado soluciones a algunos de mis problemas. El problema que me llevó a abrir éste tema es que no puedo cambiar la resolución de la pantalla en Ubuntu 8.04, está en 800x600 y 600x400 nada más. La pantalla funciona perfecto en Windows con una resolución de 1024x768.

De todo lo que he investigado encontré el comando: "lspci" pero no sé qué hacer con la información que me arroja la consola.

Adjunto la copia de <lspci-v> y la copia de mi archivo <xorg.conf> 
________________________________________

$ lspci -v
00:00.0 Host bridge: VIA Technologies, Inc. VT8375 [KM266/KL266] Host Bridge
    Subsystem: Elitegroup Computer Systems Unknown device 0a76
    Flags: bus master, 66MHz, medium devsel, latency 8
    Memory at e8000000 (32-bit, prefetchable) [size=32M]
    Capabilities: <access denied>

00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP] (prog-if 00 [Normal decode])
    Flags: bus master, 66MHz, medium devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    Memory behind bridge: ea000000-ebffffff
    Prefetchable memory behind bridge: e0000000-e7ffffff
    Capabilities: <access denied>

00:0e.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
    Subsystem: Realtek Semiconductor Co., Ltd. RT8139
    Flags: bus master, medium devsel, latency 32, IRQ 16
    I/O ports at d000 [size=256]
    Memory at ec000000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>

00:11.0 ISA bridge: VIA Technologies, Inc. VT8233A ISA Bridge
    Subsystem: Elitegroup Computer Systems Unknown device 0a76
    Flags: bus master, stepping, medium devsel, latency 0
    Capabilities: <access denied>

00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06) (prog-if 8a [Master SecP PriP])
    Subsystem: VIA Technologies, Inc. VT82C586/B/VT82C686/A/B/VT8233/A/C/VT8235 PIPC Bus Master IDE
    Flags: bus master, medium devsel, latency 32, IRQ 17
    [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
    [virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
    [virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
    [virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
    I/O ports at d400 [size=16]
    Capabilities: <access denied>

00:11.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23) (prog-if 00 [UHCI])
    Subsystem: First International Computer, Inc. VA-502 Mainboard
    Flags: bus master, medium devsel, latency 32, IRQ 18
    I/O ports at d800 [size=32]
    Capabilities: <access denied>

00:11.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23) (prog-if 00 [UHCI])
    Subsystem: First International Computer, Inc. VA-502 Mainboard
    Flags: bus master, medium devsel, latency 32, IRQ 18
    I/O ports at dc00 [size=32]
    Capabilities: <access denied>

00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 40)
    Subsystem: Elitegroup Computer Systems Unknown device 0a76
    Flags: medium devsel, IRQ 19
    I/O ports at e000 [size=256]
    Capabilities: <access denied>

00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 78)
    Subsystem: Elitegroup Computer Systems Unknown device 0a76
    Flags: medium devsel, IRQ 19
    I/O ports at e400 [size=256]
    Capabilities: <access denied>

01:00.0 VGA compatible controller: S3 Inc. VT8375 [ProSavage8 KM266/KL266] (prog-if 00 [VGA controller])
    Subsystem: Elitegroup Computer Systems Unknown device 0a76
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 11
    Memory at eb000000 (32-bit, non-prefetchable) [size=512K]
    Memory at e0000000 (32-bit, prefetchable) [size=128M]
    [virtual] Expansion ROM at ea000000 [disabled] [size=64K]
    Capabilities: <access denied>
_______________________________________
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "es"
    Option        "XkbOptions"    "lv3:ralt_switch"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Driver        "vesa"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
EndSection

---

### Post by overdrank on 2009-08-14
Hi and welcome, if you are using Hardy 8.04 you may use the alt, F2 keys and enter the command ```
gksu displayconfig-gtk
``` and adjust your resolution and monitor there.

---

### Post by malbojet on 2009-08-14
> **overdrank said:**
> Hi and welcome, if you are using Hardy 8.04 you may use the alt, F2 keys and enter the command ```
gksu displayconfig-gtk
``` and adjust your resolution and monitor there.

Hi overdrank, thanks for answer but it doesn't work

[INDENT][Pantalla]
Modelo: Plug 'n' Play
Resolucion: 640x480 720x480 720x576 800x600 848x480 848x600

[Tarjeta Gráfica]
Vesa - Generic VESA-compliant video cards
[/INDENT]
sound and video comes on the main board

---

### Post by overdrank on 2009-08-15
Ok I do not have a system with that graphics but you may try a different driver and resolution in the  [displayconfig-gtk]("https://wiki.ubuntu.com/DisplayConfigGTK").
The link I have given will show some screen shots to help you. :)

---

### Post by matthewbpt on 2009-08-15
I do believe that you aren't getting the correct resolution because you aren't running the correct driver for your graphics chipset. I'm not sure what driver the VT8375 is supposed to use but VESA is the basic fallback driver if no particular driver for the device is present, and will only allow low graphics.

---

### Post by malbojet on 2009-08-17
Hello, already I have solved the problem.

All that I had to do was to fix the file xorg.conf with the specifications of the video card of my computer and the name and reference of the monitor that I use.

I found the solution by reading in the web and I feel happy. :)

Definitively this stimulates me to go on with this Ubuntu's new experience, Regards and thank you very much for your opportune help.

---

### Post by hopwon on 2009-08-17
I'm having big problems similar to yours. Would you mind sending me a copy of your xorg.conf file to compare to mine?

Thanks

---

### Post by JavaNut13 on 2009-08-25
I'm using Ubuntu 8.10, and have the same problem.. cannot get higher than 800x600, when I used to be able to get double that.

---

