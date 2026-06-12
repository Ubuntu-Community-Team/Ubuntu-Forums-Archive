---
title: "i810 + MergedFB?"
date: 2007-03-06
forum: Multimedia &amp; Video
---

### Post by dotMatt on 2007-03-06
Hello All - I obviously have no idea what I am doing with this, but wondering if someone could shed some light for me.  I'd like to do 3D (DRI?) across two Flat Panels with the i810.  From some googling, it appears that MergedFB might get me what I want.  I am using two different Dell Flat Panels: 1707FP (Primary) and 1702FP (Secondary).  Both run fine at 1280x1024.  Xinerama works fine, but disables DRI.  Using the xorg.conf below results in the backtrace at the bottom.  Any thoughts?  Is this possible?

Feisty, all updates as of 2007-03-06
Relevant packages
```

xserver-xorg 7.2-0ubuntu3
xserver-xorg-core 1.2.0-3ubuntu3
xserver-xorg-video-i810 1.7.4-0ubuntu1

```
lspci | grep Graphics
```

00:02.0 VGA compatible controller: Intel Corporation 82Q963/Q965 Integrated Graphics Controller (rev 02)
00:02.1 Display controller: Intel Corporation 82Q963/Q965 Integrated Graphics Controller (rev 02)

```
Kernel
```

2.6.20-9-generic

```

CPU section of lshw
```

 *-cpu
          product: Intel(R) Pentium(R) D CPU 2.80GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm 
syscall x86-64 constant_tsc pni monitor ds_cpl cid cx16 xtpr lahf_lm

```

/etc/X11/xorg.conf
```

Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        FontPath        "/usr/share/fonts/X11/misc"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
        Load    "dbe"
EndSection

Section "Extensions"
        Option  "Composite" "Enable"
EndSection

Section "InputDevice"
        Identifier      "Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
        Option          "XkbOptions"    "lv3:ralt_switch"
EndSection

Section "InputDevice"
        Identifier      "Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection


Section "Device"
        Identifier      "i810"
        Driver          "i810"
        BusID           "PCI:0:2:0"
        VideoRam        71680 #70M

        Option  "DRI"                           "true"
        Option  "MergedFB"                      "true" 
        Option  "MonitorLayout"                 "DFP,CRT"
        Option  "SecondPosition"                "RightOf"
        Option  "MetaModes"                     "1280x1024-1280x1024"
EndSection

Section "Monitor"
        Identifier      "Monitor"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Screen"
        Device          "i810"
        Monitor         "Monitor
        DefaultDepth    24
        SubSection "Display"
                Depth   24
                Modes   "1280x1024"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Layout"
        Screen          "Screen"
        InputDevice     "Keyboard"
        InputDevice     "Mouse"
EndSection

Section "DRI"
        Mode    0666
EndSection

```

backtrace section of Xorg.0.log (entire log available if needed)
```

Backtrace:
0: /usr/X11R6/bin/X(xf86SigHandler+0x6d) [0x4827fd]
1: /lib/libc.so.6 [0x2b326af0ed40]
2: /usr/lib/xorg/modules/drivers//i810_drv.so(I830GetModePool+0x6f2) [0x2b326d1a4952]
3: /usr/lib/xorg/modules/drivers//i810_drv.so [0x2b326d19c2f3]
4: /usr/X11R6/bin/X(InitOutput+0x9bc) [0x4657ec]
5: /usr/X11R6/bin/X(main+0x275) [0x436e55]
6: /lib/libc.so.6(__libc_start_main+0xf4) [0x2b326aefb8e4]
7: /usr/X11R6/bin/X(FontFileCompleteXLFD+0x241) [0x436339]

```

Thanks,
-Matt

---

### Post by dotMatt on 2007-03-12
nudge?

---

### Post by themtx on 2007-03-13
Best of luck - I tried just about everything from recompiling various kernels w/i915 modular support through intel's latest i810_drv packages, all to no avail.  I've got a Dell SX280 w/i915G chipset, two Dell 1907's, and Xinerama working fine.  I got as far as getting both heads alive but cloned, or DFP alive but CRT dead (via dual out cable, 1 DVI, 1 VGA).  A few posts I googled up mentioned a bug in i810 video BIOS, and the only clue I have from Xorg.0.log is "Pipe B is connected and disabled"...

I gave up.

edit: to clarify, I see no EE messages in Xorg logs, but get no output on the CRT (VGA) head whatsoever.ctrl+alt+f(1-6) will re-activate 2nd head in tty mode, but ctrl+alt+f7 back to X and CRT head is dead again.  Really frustrating, as I'm getting decent fps in glxgears on the single head that is active.  Even Psuedo-Xinerama appears to be happy.  Just for kicks, here's my xorg.conf.

---

### Post by themtx on 2007-03-14
Well, after almost 2 weeks of on and off hacking on xorg.conf when I had time, I finally managed to get direct rendering alive w/mergedfb on an i915G using i810 driver.

Ultimately, I think I had too many entries in my display section, which was confusing mergedfb.  I commented them out, and magically got a 2560x1024 desktop.  I renamed my screens to what I believe mergedfb is expecting as well - First and Second.

I can now use compositing in xfce, but get this: the i810 won't do DRI on resolutions greater than 1024x768...  So, I can do side by side w/compositing (transparency), but no Direct Rendering enabled, though indirect thru Mesa is enabled.  However, if I switch mergedfb's "Option "SecondPosition"" flag to Above instead of LeftOf or RightOf, Beryl and hardware DRI are fine.  LOL.

Here's my working xorg.conf:

---

