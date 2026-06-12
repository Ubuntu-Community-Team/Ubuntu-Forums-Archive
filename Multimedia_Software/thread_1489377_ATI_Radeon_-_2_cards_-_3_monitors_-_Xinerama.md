---
title: "ATI Radeon - 2 cards - 3 monitors - Xinerama"
date: 2010-05-21
forum: Multimedia Software
---

### Post by MACscr on 2010-05-21
OK, so after working on trying to get my 3 monitors to work with Ubuntu 10.4 and my ATI Radeon HD3200 (IGP) and HD4850 cards, I just had to share the xorg.conf. Major thanks to the #radeon guys. I am using the default open source drivers that came with 10.4 and I kept KMS enabled (it wouldnt work without it). Here is my conf:

```

Section "ServerLayout"
        Identifier     "X.org Configured"
        Screen      0  "4850-2-Screen"
        Screen      1  "4850-1-Screen" RightOf "4850-2-Screen"
        Screen      2  "3200-Screen" RightOf "4850-1-Screen"
        InputDevice    "Mouse0" "CorePointer"
        InputDevice    "Keyboard0" "CoreKeyboard"
        Option         "Xinerama" "on"
        #OPtion          "Clone" "off"
EndSection

Section "ServerFlags"
        Option          "RandR" "false"
EndSection

Section "Files"
        ModulePath   "/usr/lib/xorg/modules"
        FontPath     "/usr/share/fonts/X11/misc"
        FontPath     "/usr/share/fonts/X11/cyrillic"
        FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath     "/usr/share/fonts/X11/Type1"
        FontPath     "/usr/share/fonts/X11/100dpi"
        FontPath     "/usr/share/fonts/X11/75dpi"
        FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
        FontPath     "built-ins"
EndSection

Section "Module"
        Load  "dbe"
        Load  "dri"
        Load  "extmod"
        Load  "dri2"
        Load  "record"
        Load  "glx"
EndSection

Section "InputDevice"
        Identifier  "Keyboard0"
        Driver      "kbd"
EndSection

Section "InputDevice"
        Identifier  "Mouse0"
        Driver      "mouse"
        Option      "Protocol" "auto"
        Option      "Device" "/dev/input/mice"
        Option      "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
        #DisplaySize      380   300     # mm
        Identifier   "Monitor1"
        VendorName   "DELL"
        ModelName    "DELL 1907FP"
        Option      "DPMS"
EndSection

Section "Monitor"
        #DisplaySize      380   300     # mm
        Identifier   "Monitor2"
        VendorName   "DELL"
        ModelName    "DELL 1907FP"
        Option      "DPMS"
EndSection

Section "Monitor"
        Identifier   "Monitor3"
        VendorName   "DELL"
        ModelName    "DELL 1905FP"
        Option          "DPMS"
EndSection

Section "Device"
        Option     "ZaphodHeads"   "DVI-0"
        Identifier  "R3200Card"
        Driver      "radeon"
        VendorName  "ATI Technologies Inc"
        BoardName   "Radeon HD 3200 Graphics"
        BusID       "PCI:1:5:0"
        #Screen  0
EndSection

Section "Device"
        Option     "ZaphodHeads" "DVI-0"
        Identifier  "R4850Card"
        Driver      "radeon"
        VendorName  "ATI Technologies Inc"
        BoardName   "RV770 [Radeon HD 4850]"
        BusID       "PCI:2:0:0"
        Screen  1
EndSection

Section "Device"
        Option     "ZaphodHeads"  "DVI-1"
        Identifier  "R4850Card-2"
        Driver      "radeon"
        VendorName  "ATI Technologies Inc"
        BoardName   "RV770 [Radeon HD 4850]"
        BusID       "PCI:2:0:0"
        Screen  0
EndSection

Section "Screen"
        Identifier "3200-Screen"
        Device     "R3200Card"
        Monitor    "Monitor1"
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

Section "Screen"
        Identifier "4850-1-Screen"
        Device     "R4850Card"
        Monitor    "Monitor3"
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

Section "Screen"
        Identifier "4850-2-Screen"
        Device     "R4850Card-2"
        Monitor    "Monitor2"
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection


```

---

### Post by K.Mandla on 2010-05-22
Moved to Multimedia and Video.

---

### Post by idallen on 2010-07-08
Yes, the "ZaphodHeads" trick is needed.  Here's the working xorg.conf for my three monitor system:

```
Section "ServerLayout"
	Identifier   "Ian"
	Screen       "Screen Left" 0 0
	Screen       "Screen Middle"  RightOf "Screen Left"
	Screen       "Screen Right"  RightOf "Screen Middle"
	Option       "Xinerama"
EndSection

Section "Screen"
	Identifier "Screen Left"
	Device     "Device Left"
	# this isn't absolutely necessary but it helps window placement
	SubSection "Display"
		Virtual 1600 1200
	EndSubSection
EndSection

Section "Screen"
	Identifier "Screen Middle"
	Device     "Device Middle"
	# this isn't absolutely necessary but it helps window placement
	SubSection "Display"
		Virtual 1600 1200
	EndSubSection
EndSection

Section "Screen"
	Identifier "Screen Right"
	Device     "Device Right"
	# this isn't absolutely necessary but it helps window placement
	SubSection "Display"
		Virtual 1600 1200
	EndSubSection
EndSection

Section "Device"
	Identifier  "Device Left"
	Driver      "radeon"
	VendorName  "ATI Technologies Inc"
	BoardName   "FireMV 2250"
	BusID       "PCI:4:0:0"
	Option	    "ZaphodHeads" "DVI-0"
	Screen	    0
EndSection

Section "Device"
	Identifier  "Device Middle"
	Driver      "radeon"
	VendorName  "ATI Technologies Inc"
	BoardName   "FireMV 2250"
	BusID       "PCI:4:0:0"
	Option	    "ZaphodHeads" "DVI-1"
	Screen	    1
EndSection

Section "Device"
	Identifier  "Device Right"
	Driver      "nv"
	VendorName  "nVidia Corporation"
	BoardName   "G86 [GeForce 8300 GS]"
	BusID       "PCI:5:0:0"
	Screen	    0
EndSection
```

---

### Post by arivero on 2010-09-08
Is your version of the driver contemplating the patches

[http://cgit.freedesktop.org/xorg/driver/xf86-video-ati/commit/?id=0ba73e040b94590867f8b1071a26da2526a3c375](http://cgit.freedesktop.org/xorg/driver/xf86-video-ati/commit/?id=0ba73e040b94590867f8b1071a26da2526a3c375)
and
[http://cgit.freedesktop.org/xorg/driver/xf86-video-ati/commit/?id=433c8617341f5768255826435a2b09afba684f02](http://cgit.freedesktop.org/xorg/driver/xf86-video-ati/commit/?id=433c8617341f5768255826435a2b09afba684f02)

Because if I read correctly, they avoid the conflict between the names of similar outputs from different cards.

I have two radeon cards and xrandr -q shows that they have different names for the output: DVI-0, VGA-0 in a card, and DVI-1, VGA-1 in the other.

---

### Post by rainbowwarrior on 2010-09-15
Hi,

i try about days to run my Ubuntu with 2 ATI cards and 3 Monitors. I tried a lot of configurations, without success. 


[LIST]
[*]2x ATI Radeon X1900 XT
[*]1x ATI Radeon HD 4350
[/LIST]

[LIST]
[*]2x 23" TFT ( middle and right )
[*]1x 32" Toshiba LCD ( left )
[/LIST]
When i think i'll be successfully soon, i get this error message:

```
(EE) Screen 0 deleted because of no matching config section.
```

After my tries, i use exactly (!) the same xorg.conf as the last 2 posts, with except the PCI-Bus ID. 
Anyway i get the error..I don't know whats wrong. I hope someone can help me. 

I show you one trie by myself:

The Second Screen have to be right and the Third Screen have to be on the left. The Main Screen should be middle. But it's not working.

```

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen       0   "Main Screen" 0 0 
    Screen       1   "Second Screen" RightOf "Main Screen"
    Screen       2   "Third Screen" RightOf "Second Screen"
    Option  "Xinerama" "true"
EndSection

Section "Device"
    Identifier    "Radeon X1900 XT 1"
    Driver    "radeon"
    BusID    "PCI:1:0:0"
EndSection

Section "Device"
    Identifier    "Radeon X1900 XT 2"
    Driver    "radeon"
    BusID    "PCI:1:0:1"
EndSection

Section "Device"
    Identifier    "Radeon HD 4350"
    Driver    "radeon"
    BusID       "PCI:2:0:0" 
EndSection

Section "Screen"
    Identifier    "Main Screen"
    Device        "Radeon X1900 XT 1"
    Monitor        "Main Monitor"
    DefaultDepth    24
    SubSection "Display"
        Depth        1
        Modes        "1024x768"
    EndSubSection
EndSection
 
Section "Screen"
    Identifier    "Second Screen"
    Device        "Radeon X1900 XT 2"
    Monitor        "Second Monitor"
    DefaultDepth    24
    SubSection "Display"
        Depth        1
        Modes        "1024x768"
    EndSubSection
EndSection

Section "Screen"
    Identifier    "Third Screen"
    Device        "Radeon HD 4350"
    Monitor        "Third Monitor"
    DefaultDepth    24
    SubSection "Display"
        Depth        1
        Modes        "1024x768"
    EndSubSection
EndSection

```

The first xorg.conf from this thead, only with the change on my bus-ids. 
```

#pci:1:0:0
#ist middle
#
#pci:1:0:1
#ist right
#
#pci:2:0:0 
#ist left


Section "ServerLayout"
        Identifier     "X.org Configured"
        Screen      0  "4850-2-Screen"
        Screen      1  "4850-1-Screen" RightOf "4850-2-Screen"
        Screen      2  "3200-Screen" RightOf "4850-1-Screen"
        InputDevice    "Mouse0" "CorePointer"
        InputDevice    "Keyboard0" "CoreKeyboard"
        Option         "Xinerama" "on"
        #OPtion          "Clone" "off"
EndSection

Section "ServerFlags"
        Option          "RandR" "false"
EndSection

Section "Files"
        ModulePath   "/usr/lib/xorg/modules"
        FontPath     "/usr/share/fonts/X11/misc"
        FontPath     "/usr/share/fonts/X11/cyrillic"
        FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath     "/usr/share/fonts/X11/Type1"
        FontPath     "/usr/share/fonts/X11/100dpi"
        FontPath     "/usr/share/fonts/X11/75dpi"
        FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
        FontPath     "built-ins"
EndSection

Section "Module"
        Load  "dbe"
        Load  "dri"
        Load  "extmod"
        Load  "dri2"
        Load  "record"
        Load  "glx"
EndSection

Section "InputDevice"
        Identifier  "Keyboard0"
        Driver      "kbd"
EndSection

Section "InputDevice"
        Identifier  "Mouse0"
        Driver      "mouse"
        Option      "Protocol" "auto"
        Option      "Device" "/dev/input/mice"
        Option      "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
        #DisplaySize      380   300     # mm
        Identifier   "Monitor1"
        VendorName   "DELL"
        ModelName    "DELL 1907FP"
        Option      "DPMS"
EndSection

Section "Monitor"
        #DisplaySize      380   300     # mm
        Identifier   "Monitor2"
        VendorName   "DELL"
        ModelName    "DELL 1907FP"
        Option      "DPMS"
EndSection

Section "Monitor"
        Identifier   "Monitor3"
        VendorName   "DELL"
        ModelName    "DELL 1905FP"
        Option          "DPMS"
EndSection

Section "Device"
        Option     "ZaphodHeads"   "DVI-0"
        Identifier  "R3200Card"
        Driver      "radeon"
        VendorName  "ATI Technologies Inc"
        BoardName   "Radeon HD 3200 Graphics"
        BusID       "PCI:1:0:0"
        #Screen  0
EndSection

Section "Device"
        Option     "ZaphodHeads" "DVI-0"
        Identifier  "R4850Card"
        Driver      "radeon"
        VendorName  "ATI Technologies Inc"
        BoardName   "RV770 [Radeon HD 4850]"
        BusID       "PCI:2:0:0"
        Screen  1
EndSection

Section "Device"
        Option     "ZaphodHeads"  "DVI-1"
        Identifier  "R4850Card-2"
        Driver      "radeon"
        VendorName  "ATI Technologies Inc"
        BoardName   "RV770 [Radeon HD 4850]"
        BusID       "PCI:1:0:1"
        Screen  0
EndSection

Section "Screen"
        Identifier "3200-Screen"
        Device     "R3200Card"
        Monitor    "Monitor1"
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

Section "Screen"
        Identifier "4850-1-Screen"
        Device     "R4850Card"
        Monitor    "Monitor3"
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

Section "Screen"
        Identifier "4850-2-Screen"
        Device     "R4850Card-2"
        Monitor    "Monitor2"
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

```

---

### Post by Zombie13 on 2010-11-02
Ok, so I got this working on 10.10, but I have a problem.  I have several applications that kill my Xsession.  Virtualbox, for example.  The program runs, but as soon as the mouse touches the program part of the window (as opposed to the window decor part) the entire Xsession dies and sends me to a login prompt.

Any ideas?

I didn't see any messages in /var/log/Xorg.0.log or .xsession-errors.

Thanks.

Z.

---

### Post by idallen on 2010-11-02
> **Zombie13 said:**
> Ok, so I got this working on 10.10, but I have a problem.  I have several applications that kill my Xsession

Yes.  Me too, under Ubuntu 10.10.
2.6.35-22-generic #35-Ubuntu SMP Sat Oct 16 20:45:36 UTC 2010 x86_64 GNU/Linux

If you run Xorg from a command line, you will see the X server die with
a segmentation fault.  The simplest case that reproduces this is:

- install the Image Magick package that contains "import"
- as root, shut down your X11 display and go to command line
  - # /etc/init.d/gdm stop
- on the console, log in as root (or use su or sudo), and start Xorg:
  - # /usr/bin/Xorg
- on a different console (CTRL-ALT-F2) log in and do this:
  $ DISPLAY=:0
  $ export DISPLAY
  $ xload &
  $ import /tmp/x.png
- switch back to the X11 screen (ALT-F7 or F8 )
  and use the mouse to select the xload window to dump by import.
- BOOM.  Xorg dies with a segfault, which you will see on your F1 console.

Other things trigger this too, such as the vtwm window manager.
I'm not sure where to report it.

Here's the segfault seen from running Xorg inside gdb:

Program received signal SIGSEGV, Segmentation fault.
PanoramiXTranslateCoords (client=0xb147a0) at ../../Xext/panoramiXprocs.c:637
637     ../../Xext/panoramiXprocs.c: No such file or directory.
        in ../../Xext/panoramiXprocs.c
(gdb) where
#0  PanoramiXTranslateCoords (client=0xb147a0)
    at ../../Xext/panoramiXprocs.c:637
#1  0x000000000042c2d9 in Dispatch () at ../../dix/dispatch.c:432
#2  0x000000000042184b in main (argc=2, argv=0x7fffffffe4c8, 
    envp=<value optimized out>) at ../../dix/main.c:291

Here's what it looks like outside of gdb:

# /usr/bin/Xorg :4

X.Org X Server 1.9.0
Release Date: 2010-08-20
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
Current Operating System: Linux ian 2.6.35-22-generic #35-Ubuntu SMP Sat Oct 16 20:45:36 UTC 2010 x86_64
Kernel command line: BOOT_IMAGE=/vmlinuz-2.6.35-22-generic root=UUID=e2fb2eaa-3c3b-47cf-8143-68a7b0b09b81 ro resume=/dev/sda2
Build Date: 16 September 2010  06:18:41PM
xorg-server 2:1.9.0-0ubuntu7 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.18.4
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.4.log", Time: Wed Nov  3 02:46:33 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
(II) [KMS] Kernel modesetting enabled.
(II) [KMS] Kernel modesetting enabled.
(II) [KMS] Kernel modesetting enabled.
(EE) RADEON(1):  reusing fd for second head

Backtrace:
0: /usr/bin/Xorg (xorg_backtrace+0x28) [0x4a0fa8]
1: /usr/bin/Xorg (0x400000+0x60fcd) [0x460fcd]
2: /lib/libpthread.so.0 (0x7fadf39ea000+0xfb40) [0x7fadf39f9b40]
3: /usr/bin/Xorg (0x400000+0xbb22f) [0x4bb22f]
4: /usr/bin/Xorg (0x400000+0x2c2d9) [0x42c2d9]
5: /usr/bin/Xorg (0x400000+0x2184b) [0x42184b]
6: /lib/libc.so.6 (__libc_start_main+0xfe) [0x7fadf2955d8e]
7: /usr/bin/Xorg (0x400000+0x213d9) [0x4213d9]
Segmentation fault at address 0x4

Caught signal 11 (Segmentation fault). Server aborting

Please consult the The X.Org Foundation support 
         at [http://wiki.x.org](http://wiki.x.org)
 for help. 
Please also check the log file at "/var/log/Xorg.4.log" for additional information.

 ddxSigGiveUp: Closing log
Exit 1

---

### Post by MACscr on 2010-11-04
yeah, my setup is ganked since upgrading to 10.10 as well. Only can use two monitors now. What a pain.

---

### Post by Zombie13 on 2010-11-09
If I need to create a new thread, I will.  I am having a problem with my 3 monitor setup.  I have 2 samsung monitors and a Dell monitor in the middle.  The left samsung is Xrandr'ed with the Dell, and the right samsung is a separate screen.  Everything works as designed except this: when I move the mouse to the right most edge of the Dell, when it should just to the left edge of the second screen, it jumps to the left most edge instead.  Then when returning back to screen 0, it jumps to the right edge of the other samsung monitor, completely bypassing the dell monitor all together. 

I am sure that it is something I misconfigured, but for the life of me I can't figure out what.

Any ideas would be helpful.

Z.

---

### Post by bartek on 2010-11-17
i'm the same boat and it appears to be a typo in the code.
Check out this discussion:
[https://bbs.archlinux.org/viewtopic.php?pid=841628](https://bbs.archlinux.org/viewtopic.php?pid=841628)
hth

---

### Post by Zombie13 on 2010-11-24
I applied the patch refered to in the previous link and it works.  The only problem I have seen so far is that Aisleriot doesn't run.  Big deal.  Otherwise, there is some artifacting when moving windows but it repaints just fine so it's not a problem.

I love having my 3 monitors back again....

Z.

---

### Post by dsjstc on 2010-12-16
Worked for me too.   Bug report:
[https://bugs.launchpad.net/ubuntu/+source/qt4-x11/+bug/650539](https://bugs.launchpad.net/ubuntu/+source/qt4-x11/+bug/650539)

PPA with fixed xorg:
[https://launchpad.net/~jared-bunting/+archive/xorg-xserver-650539](https://launchpad.net/~jared-bunting/+archive/xorg-xserver-650539)

---

### Post by dsjstc on 2011-01-05
Have any of you multiple-card guys figured out how to force your better card to be the renderer?

My post has gone unanswered, and I'd sure love some help.
[http://ubuntuforums.org/showthread.php?t=1647540](http://ubuntuforums.org/showthread.php?t=1647540)

---

