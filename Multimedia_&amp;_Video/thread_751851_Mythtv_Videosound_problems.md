---
title: "Mythtv Video/sound problems"
date: 2008-04-10
forum: Multimedia &amp; Video
---

### Post by DarK SouL on 2008-04-10
I have been fighting with this for over two weeks and looked all around the internet for answers but none seemed to help so I think its time to ask before, God forbid, I go back to Vista.

I have hardy running on a P4 dual core, 2 gigs ram, ati radeon x1600 and a WinTV-Pvr 150

I was able to setup mythbuntu over ubuntu using synaptic, the mythtv configuration went smoothly and I am able to change channels and all that, BUT, I have an horrible flickering problem and I am 100% sure its the sound thats causing  it, but I have no idea how to solve it.

Why do I know its the sound?

When I change the Audio Output Device to NULL the flickering stops, however, if I select ALSA:xxx or /dev/dspx it flickers like hell.

Has someone ran into something like this before?

BTW, forgot to mention

I have used this, cat /dev/video0 > test.mpg and I am able to watch the video with audio and without the flickering problem, so it should be a mythtv issue, I guess...

---

### Post by DarK SouL on 2008-04-11
I ran mythfrontend  on the shell and got this

```

nievesj@ubuntu-desktop:~$ mythfrontend
2008-04-11 18:35:48.549 Using runtime prefix = /usr, libdir = /usr/lib
2008-04-11 18:35:48.864 XScreenSaver support enabled
2008-04-11 18:35:48.865 DPMS is active.
2008-04-11 18:35:48.866 Empty LocalHostName.
2008-04-11 18:35:48.866 Using localhost value of ubuntu-desktop
2008-04-11 18:35:48.878 New DB connection, total: 1
2008-04-11 18:35:48.883 Connected to database 'mythconverg' at host: localhost
2008-04-11 18:35:48.885 Closing DB connection named 'DBManager0'
2008-04-11 18:35:48.886 Primary screen 0.
2008-04-11 18:35:48.887 Connected to database 'mythconverg' at host: localhost
2008-04-11 18:35:48.888 Using screen 0, 1280x1024 at 0,0
2008-04-11 18:35:48.900 New DB connection, total: 2
2008-04-11 18:35:48.900 Connected to database 'mythconverg' at host: localhost
2008-04-11 18:35:48.903 mythfrontend version: 0.21.20080304-1 URL:www.mythtv.org
2008-04-11 18:35:48.903 Enabled verbose msgs:  important general
2008-04-11 18:35:49.000 Unable to parse themeinfo.xml for glass-wide
2008-04-11 18:35:49.000 The theme (glass-wide) is missing a themeinfo.xml file
2008-04-11 18:35:49.123 Unable to parse themeinfo.xml for glass-wide
2008-04-11 18:35:49.123 The theme (glass-wide) is missing a themeinfo.xml file
2008-04-11 18:35:49.395 Primary screen 0.
2008-04-11 18:35:49.395 Using screen 0, 1280x1024 at 0,0
2008-04-11 18:35:49.397 Switching to square mode (Iulius)
2008-04-11 18:35:49.512 Using the Qt painter
mythtv: could not open config file /home/nievesj/.lirc/mythtv
mythtv: No such file or directory
2008-04-11 18:35:49.512 Failed to read lirc config /home/nievesj/.lircrc for mythtv
2008-04-11 18:35:49.513 JoystickMenuClient Error: Joystick disabled - Failed to read /home/nievesj/.mythtv/joystickmenurc
2008-04-11 18:35:50.781 Loading from: /usr/share/mythtv/themes/Iulius/base.xml
2008-04-11 18:35:50.880 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-04-11 18:35:50.932 Registering Internal as a media playback plugin.
2008-04-11 18:36:12.142 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-04-11 18:36:12.143 Using protocol version 40
2008-04-11 18:36:12.149 TV: Attempting to change from None to WatchingLiveTV
2008-04-11 18:36:12.150 Using protocol version 40
2008-04-11 18:36:17.497 DPMS Deactivated
2008-04-11 18:36:18.348 AFD: Opened codec 0x835c990, id(MPEG2VIDEO) type(Video)
2008-04-11 18:36:18.348 AFD: codec MP2 has 2 channels
2008-04-11 18:36:18.348 AFD: Opened codec 0x835ea20, id(MP2) type(Audio)
2008-04-11 18:36:18.465 Opening audio device '/dev/dsp1'. ch 2(2) sr 48000
2008-04-11 18:36:18.465 Opening OSS audio device '/dev/dsp1'.
2008-04-11 18:36:18.575 VideoOutputXv Error: Could not find suitable XVideo surface.
2008-04-11 18:36:18.575 VideoOutputXv: Falling back to X11 video output over a network socket.
               *** May be very slow ***
2008-04-11 18:36:18.575 VideoOutputXv Error: XCreateImage failed: XJ_disp(0x83890d0) visual(0x8389610)
                        XJ_depth(24) WxH(1280x1024) bpl(3840)
2008-04-11 18:36:18.576 VideoOutputXv Error: Failed to create X buffers.
2008-04-11 18:36:18.800 Couldn't load deinterlace filter
2008-04-11 18:36:18.806 OSD Theme Dimensions W: 640 H: 480
2008-04-11 18:36:19.161 TV: Changing from None to WatchingLiveTV
2008-04-11 18:36:19.164 New DB connection, total: 3
2008-04-11 18:36:19.164 Realtime priority would require SUID as root.
2008-04-11 18:36:19.164 Connected to database 'mythconverg' at host: localhost
2008-04-11 18:36:19.260 Video timing method: USleep with busy wait 

```

Could be this the problem?

```

2008-04-11 18:36:18.575 VideoOutputXv Error: Could not find suitable XVideo surface.
2008-04-11 18:36:18.575 VideoOutputXv: Falling back to X11 video output over a network socket.
               *** May be very slow ***
2008-04-11 18:36:18.575 VideoOutputXv Error: XCreateImage failed: XJ_disp(0x83890d0) visual(0x8389610)
                        XJ_depth(24) WxH(1280x1024) bpl(3840)
2008-04-11 18:36:18.576 VideoOutputXv Error: Failed to create X buffers.
2008-04-11 18:36:18.800 Couldn't load deinterlace filter 

```

I am really lost here :(

---

### Post by warp99 on 2008-04-11
Can you do an 'lspci -v' and post the output of the TV tuner card information.

---

### Post by DarK SouL on 2008-04-12
Here it is

```

00:00.0 Host bridge: nVidia Corporation Unknown device 0070 (rev c1)
	Subsystem: ASUSTeK Computer Inc. Unknown device 8189
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: [40] HyperTransport: Host or Secondary Interface

00:00.1 RAM memory: nVidia Corporation Unknown device 007f (rev a1)
	Flags: 66MHz, fast devsel

00:00.2 RAM memory: nVidia Corporation Unknown device 0075 (rev a1)
	Flags: 66MHz, fast devsel

00:00.3 RAM memory: nVidia Corporation Unknown device 006f (rev a1)
	Flags: 66MHz, fast devsel

00:00.4 RAM memory: nVidia Corporation Unknown device 00b4 (rev a1)
	Flags: bus master, 66MHz, fast devsel, latency 0

00:01.0 RAM memory: nVidia Corporation Unknown device 0076 (rev a1)
	Flags: 66MHz, fast devsel

00:01.1 RAM memory: nVidia Corporation Unknown device 0078 (rev a1)
	Flags: 66MHz, fast devsel

00:01.2 RAM memory: nVidia Corporation Unknown device 0079 (rev a1)
	Flags: 66MHz, fast devsel

00:01.3 RAM memory: nVidia Corporation Unknown device 007a (rev a1)
	Flags: 66MHz, fast devsel

00:01.4 RAM memory: nVidia Corporation Unknown device 007b (rev a1)
	Flags: 66MHz, fast devsel

00:01.5 RAM memory: nVidia Corporation Unknown device 007c (rev a1)
	Flags: 66MHz, fast devsel

00:01.6 RAM memory: nVidia Corporation Unknown device 007d (rev a1)
	Flags: 66MHz, fast devsel

00:02.0 PCI bridge: nVidia Corporation Unknown device 007e (rev a2) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: c6000000-c7ffffff
	Prefetchable memory behind bridge: 00000000b0000000-00000000bfffffff
	Capabilities: [40] Power Management version 2
	Capabilities: [48] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
	Capabilities: [80] Express Root Port (Slot+) IRQ 0

00:04.0 PCI bridge: nVidia Corporation Unknown device 007e (rev a2) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Capabilities: [40] Power Management version 2
	Capabilities: [48] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
	Capabilities: [80] Express Root Port (Slot+) IRQ 0

00:05.0 PCI bridge: nVidia Corporation Unknown device 007e (rev a2) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Capabilities: [40] Power Management version 2
	Capabilities: [48] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
	Capabilities: [80] Express Root Port (Slot+) IRQ 0

00:06.0 PCI bridge: nVidia Corporation Unknown device 007e (rev a2) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	Capabilities: [40] Power Management version 2
	Capabilities: [48] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
	Capabilities: [80] Express Root Port (Slot+) IRQ 0

00:07.0 PCI bridge: nVidia Corporation Unknown device 007e (rev a2) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
	Capabilities: [40] Power Management version 2
	Capabilities: [48] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
	Capabilities: [80] Express Root Port (Slot+) IRQ 0

00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
	Subsystem: ASUSTeK Computer Inc. A8N-VM CSM Mainboard
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: [44] HyperTransport: Slave or Primary Interface
	Capabilities: [e0] HyperTransport: MSI Mapping

00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a2)
	Subsystem: ASUSTeK Computer Inc. A8N-VM CSM Mainboard
	Flags: bus master, 66MHz, fast devsel, latency 0

00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a2)
	Subsystem: ASUSTeK Computer Inc. A8N-VM CSM Mainboard
	Flags: 66MHz, fast devsel, IRQ 5
	I/O ports at 5000 [size=64]
	I/O ports at 5100 [size=64]
	Capabilities: [44] Power Management version 2

00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a2)
	Subsystem: ASUSTeK Computer Inc. Unknown device 81bc
	Flags: 66MHz, fast devsel

00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2) (prog-if 10 [OHCI])
	Subsystem: ASUSTeK Computer Inc. A8N-VM CSM Mainboard
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
	Memory at c8005000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2

00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2) (prog-if 20 [EHCI])
	Subsystem: ASUSTeK Computer Inc. A8N-VM CSM Mainboard
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 18
	Memory at c8006000 (32-bit, non-prefetchable) [size=256]
	Capabilities: [44] Debug port
	Capabilities: [80] Power Management version 2

00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1) (prog-if 8a [Master SecP PriP])
	Subsystem: Unknown device f043:81bc
	Flags: bus master, 66MHz, fast devsel, latency 0
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at f000 [size=16]
	Capabilities: [44] Power Management version 2

00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1) (prog-if 85 [Master SecO PriO])
	Subsystem: ASUSTeK Computer Inc. A8N-VM CSM Mainboard
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 19
	I/O ports at 09f0 [size=8]
	I/O ports at 0bf0 [size=4]
	I/O ports at 0970 [size=8]
	I/O ports at 0b70 [size=4]
	I/O ports at d400 [size=16]
	Memory at c8007000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2
	Capabilities: [b0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/2 Enable-
	Capabilities: [cc] HyperTransport: MSI Mapping

00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1) (prog-if 85 [Master SecO PriO])
	Subsystem: ASUSTeK Computer Inc. A8N-VM CSM Mainboard
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
	I/O ports at 09e0 [size=8]
	I/O ports at 0be0 [size=4]
	I/O ports at 0960 [size=8]
	I/O ports at 0b60 [size=4]
	I/O ports at e800 [size=16]
	Memory at c8004000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2
	Capabilities: [b0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/2 Enable-
	Capabilities: [cc] HyperTransport: MSI Mapping

00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2) (prog-if 01 [Subtractive decode])
	Flags: bus master, 66MHz, fast devsel, latency 0
	Bus: primary=00, secondary=06, subordinate=06, sec-latency=128
	I/O behind bridge: 0000b000-0000bfff
	Memory behind bridge: c4000000-c5ffffff
	Prefetchable memory behind bridge: c0000000-c3ffffff
	Capabilities: [b8] Subsystem: Gammagraphx, Inc. Unknown device 0000
	Capabilities: [8c] HyperTransport: MSI Mapping

00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
	Subsystem: ASUSTeK Computer Inc. Unknown device 818f
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 5
	Memory at c8000000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [44] Power Management version 2
	Capabilities: [50] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/0 Enable-
	Capabilities: [6c] HyperTransport: MSI Mapping

01:00.0 VGA compatible controller: ATI Technologies Inc RV530 [Radeon X1600] (prog-if 00 [VGA controller])
	Subsystem: Diamond Multimedia Systems Unknown device 0456
	Flags: bus master, fast devsel, latency 0, IRQ 21
	Memory at b0000000 (64-bit, prefetchable) [size=256M]
	Memory at c7000000 (64-bit, non-prefetchable) [size=64K]
	I/O ports at a000 [size=256]
	Expansion ROM at c6000000 [disabled] [size=128K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Express Endpoint IRQ 0
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-

01:00.1 Display controller: ATI Technologies Inc RV530 [Radeon X1600] (Secondary)
	Subsystem: Diamond Multimedia Systems Unknown device 0457
	Flags: fast devsel
	Memory at c7010000 (64-bit, non-prefetchable) [disabled] [size=64K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Express Endpoint IRQ 0

06:06.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
	Subsystem: Hauppauge computer works Inc. WinTV PVR 150
	Flags: bus master, medium devsel, latency 64, IRQ 21
	Memory at c0000000 (32-bit, prefetchable) [size=64M]
	Capabilities: [44] Power Management version 2

06:0c.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
	Subsystem: ASUSTeK Computer Inc. Marvell 88E8001 Gigabit Ethernet Controller (Asus)
	Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
	Memory at c5000000 (32-bit, non-prefetchable) [size=16K]
	I/O ports at b000 [size=256]
	Expansion ROM at c4000000 [disabled] [size=128K]
	Capabilities: [48] Power Management version 2
	Capabilities: [50] Vital Product Data


```

---

### Post by warp99 on 2008-04-12
That's a hardware based encoding card with chipset CX23416 and is well supported. Do you have the ALSA aoss wrapper package installed?

---

### Post by warp99 on 2008-04-12
Also are you using the TV Out port on the ATI card, i.e. analog TV attached? If you can post a copy of your /etc/X11/xorg.conf that would be helpful.

---

### Post by DarK SouL on 2008-04-12
I think I do, is that the package alsa-oss?  If thats the one it is installed.

---

### Post by DarK SouL on 2008-04-12
> **warp99 said:**
> Also are you using the TV Out port on the ATI card, i.e. analog TV attached? If you can post a copy of your /etc/X11/xorg.conf that would be helpful.

Here it is

```

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
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbVariant"	"intl"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"vmmouse"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"fglrx"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection
Section "Module"
	Load		"glx"
EndSection

```

---

### Post by warp99 on 2008-04-12
If you post your xorg.conf I think I know what the problem may be. Also are you using an analog TV?

---

### Post by DarK SouL on 2008-04-12
The xorg.conf is above. 

I am using an lcd display (monitor) to view the frontend (this computer is also the backend)

---

### Post by warp99 on 2008-04-12
Well your xorg.conf is not set up properly for the card and xv support, so the card is dropping back to the default X11 video display. You need to set up your xorg.conf simliar to mine in order to get xv support:

```
# xorg.conf (xorg X Window System server configuration file)
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

Section "ServerLayout"
        Identifier     "Default Layout"
        Screen         "Default Screen" 0 0
        InputDevice    "Generic Keyboard"
        InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
        Load  "glx"
EndSection

Section "InputDevice"
        Identifier  "Generic Keyboard"
        Driver      "kbd"
        Option      "CoreKeyboard"
        Option      "XkbRules"      "xorg"
        Option      "XkbModel"      "pc104"
        Option      "XkbOptions"    "altwin:super_win"
        Option      "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "CorePointer"
        Option      "Device" "/dev/input/mice"
        Option      "Protocol" "ImPS/2"
        Option      "ZAxisMapping" "4 5"
        Option      "Emulate3Buttons" "true"
EndSection

Section "Monitor"
        Identifier   "Generic Monitor"
        HorizSync    30.0 - 70.0
        VertRefresh  50.0 - 160.0
        Option       "DPMS"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[1]"
        HorizSync    30.0 - 50.0
        VertRefresh  60.0 - 60.0
        Option       "DPMS" "true"
EndSection

Section "Device"
        Identifier  "ATI Technologies Inc RV350 AR [Radeon 9600]"
        Driver      "fglrx"
        Option      "PseudoColorVisuals" "off"
        Option      "OpenGLOverlay" "off"
        Option      "VideoOverlay" "on"
        Option      "TVStandard" "NTSC-M"
        Option      "TVFormat" "NTSC-M"
        Option      "DesktopSetup" "mirror"
        Option      "ForceMonitors" "crt1,tv"
        Option      "EnableMonitor" "crt1,tv"
        BusID       "PCI:1:0:0"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[1]"
        Driver      "fglrx"
        BusID       "PCI:1:0:0"
        Screen      1
EndSection

Section "Screen"
        Identifier "Default Screen"
        Device     "ATI Technologies Inc RV350 AR [Radeon 9600]"
        Monitor    "Generic Monitor"
        DefaultDepth     24
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[1]"
        Device     "aticonfig-Device[1]"
        Monitor    "aticonfig-Monitor[1]"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
                Modes    "1024x768"
        EndSubSection
EndSection

Section "Extensions"
        Option      "Composite" "true"
EndSection                                                    
```If you notice the line: 

```
Option      "VideoOverlay" "on"
```That's for xv support. Now this is the xorg.conf for my MythTV media sever with an ATI card running the restricted drivers, so I know it works perfect. You can replace you xorg.conf with this one if you like and it should work plus it will enable the TV_Out port and your windows super key will work again. You may have to make some change to the mouse section if your mouse doesn't work.

Now if you want to change the resolution of your monitor with this xorg.conf file then change "1024x768" in the modes section to whatever resolution you're running, ie "1280x1100" or "1680x1050" and so on. Just remember to include the quotation marks.

Oh ... backup your xorg.conf before you start and if you run into any problems you can always reset the video display with 'sudo dpkg-reconfigure xserver-xorg' to get back your desktop.

---

### Post by DarK SouL on 2008-04-13
I tried your xorg.config, specifically this

```

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"fglrx"
	Option      	"PseudoColorVisuals" "off"
        Option      	"OpenGLOverlay" "off"
        Option      	"VideoOverlay" "on"
EndSection

```

but its still not working, well, the interface is not flickering anymore but the video lasts around two seconds, then I get a black screen with skipping audio, if I press the left or right arrows I get like two seconds more of video.  If I go to audio output device and select null, and then go back to watch TV I get crystal clear video, it looks so good that its a shame is not working with audio :(

What could mythtv be doing with the audio that causes this?

BTW, thanks a lot for the help you have given me, I really appreciate it!

---

### Post by warp99 on 2008-04-13
Well at least we got the video flickering to stop, now we work on the audio, Let's increase  the audio buffer for encoder cards and check the sampling rate.

On your frontend go to Utilities/Setup > Setup > TV Settings > Playback and enable 'Extra audio buffering", then go into Utilities/Setup > Setup > TV Settings > Recording Profiles and  check to make sure you have the sampling rates for all of the profiles set to 48000. Also reduce the bit rate since 384kps is a little too high for the major of people. While you are there change you capture resolution from 480x480 to 720x480 for NTSC or 720x576 for PAL/SECAM. Seems to be an issue with the PVR-150 cards.

If this does not work check in your /var/log/mythtv/mythfrontend.log for any 'NVP: prebuffering pause' or 'audio buffer overflow' errors and enter following:

```
lsmod
```
and post the results. It may be a driver issue with your on-board sound card.

---

### Post by Trollslayer on 2008-04-13
> **DarK SouL said:**
> I have been fighting with this for over two weeks and looked all around the internet for answers but none seemed to help so I think its time to ask before, God forbid, I go back to Vista.

I have hardy running on a P4 dual core, 2 gigs ram, ati radeon x1600 and a WinTV-Pvr 150

I was able to setup mythbuntu over ubuntu using synaptic, the mythtv configuration went smoothly and I am able to change channels and all that, BUT, I have an horrible flickering problem and I am 100% sure its the sound thats causing  it, but I have no idea how to solve it.

Why do I know its the sound?

When I change the Audio Output Device to NULL the flickering stops, however, if I select ALSA:xxx or /dev/dspx it flickers like hell.

Has someone ran into something like this before?

BTW, forgot to mention

I have used this, cat /dev/video0 > test.mpg and I am able to watch the video with audio and without the flickering problem, so it should be a mythtv issue, I guess...

The internal player is poor, set it to use VLC
vlc --fullscreen %s vlc:quit

---

### Post by DarK SouL on 2008-04-13
> **warp99 said:**
> Well at least we got the video flickering to stop, now we work on the audio, Let's increase  the audio buffer for encoder cards and check the sampling rate.

On your frontend go to Utilities/Setup > Setup > TV Settings > Playback and enable 'Extra audio buffering", then go into Utilities/Setup > Setup > TV Settings > Recording Profiles and  check to make sure you have the sampling rates for all of the profiles set to 48000. Also reduce the bit rate since 384kps is a little too high for the major of people. While you are there change you capture resolution from 480x480 to 720x480 for NTSC or 720x576 for PAL/SECAM. Seems to be an issue with the PVR-150 cards.


The default value of the sampling rates is 48000, changed the bit rate from 384kbps to 112kbps.  I dont know where to select PAL/SECAM from, is it on the setup? There is no option like that in TV Settings.

> 
If this does not work check in your /var/log/mythtv/mythfrontend.log for any 'NVP: prebuffering pause' or 'audio buffer overflow' errors and enter following:


There were no errors like those, I have attached the file below. 

> 
```
lsmod
```
and post the results. It may be a driver issue with your on-board sound card.

lsmod

```

Module                  Size  Used by
nls_iso8859_1           4992  1 
nls_cp437               6656  1 
vfat                   14464  1 
fat                    54556  1 vfat
usb_storage            73664  1 
libusual               19108  1 usb_storage
binfmt_misc            12808  1 
af_packet              23812  2 
tun                    12672  0 
vboxdrv                61104  0 
nfsd                  228848  13 
lockd                  67720  2 nfsd
nfs_acl                 4608  1 nfsd
auth_rpcgss            43424  1 nfsd
sunrpc                185884  9 nfsd,lockd,nfs_acl,auth_rpcgss
exportfs                6016  1 nfsd
ppdev                  10372  0 
ipv6                  267780  28 
acpi_cpufreq           10796  0 
cpufreq_ondemand        9740  2 
cpufreq_powersave       2688  0 
cpufreq_userspace       5284  0 
cpufreq_stats           7104  0 
freq_table              5536  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
cpufreq_conservative     8712  0 
video                  19856  0 
output                  4736  1 video
container               5632  0 
dock                   11280  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
battery                14212  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
ac                      6916  0 
lp                     12324  0 
snd_hda_intel         344600  0 
snd_usb_audio          83936  3 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_usb_lib            18432  1 snd_usb_audio
snd_pcm                78596  3 snd_hda_intel,snd_usb_audio,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  2 snd_hda_intel,snd_usb_audio
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
wm8775                  6924  0 
cx25840                28176  0 
snd_rawmidi            25760  2 snd_usb_lib,snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
evdev                  13056  3 
tuner                  42912  0 
tea5767                 6788  1 tuner
tda8290                12420  1 tuner
tuner_simple           10248  1 tuner
mt20xx                 13192  1 tuner
tea5761                 6020  1 tuner
parport_pc             36260  1 
parport                37832  3 ppdev,lp,parport_pc
serio_raw               7940  0 
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
psmouse                40336  0 
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
pcspkr                  4224  0 
ivtv                  140352  0 
snd                    56996  19 snd_hda_intel,snd_usb_audio,snd_pcm_oss,snd_mixer_oss,snd_usb_lib,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit            7300  1 ivtv
cx2341x                13444  1 ivtv
soundcore               8800  1 snd
lirc_mceusb2           14852  0 
tveeprom               16656  1 ivtv
lirc_dev               15860  1 lirc_mceusb2
videodev               29440  1 ivtv
v4l2_common            18304  6 wm8775,cx25840,tuner,ivtv,cx2341x,videodev
v4l1_compat            15492  2 ivtv,videodev
fglrx                1555468  23 
agpgart                34760  1 fglrx
i2c_nforce2             7680  0 
i2c_core               24832  12 wm8775,cx25840,tuner,tea5767,tda8290,tuner_simple,mt20xx,tea5761,ivtv,i2c_algo_bit,tveeprom,i2c_nforce2
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
button                  9232  0 
ext3                  136712  2 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
sd_mod                 30720  10 
sata_nv                27528  0 
ata_generic             8324  0 
floppy                 59588  0 
skge                   43536  0 
pata_amd               14212  6 
pata_acpi               8320  0 
libata                159344  4 sata_nv,ata_generic,pata_amd,pata_acpi
scsi_mod              151436  5 usb_storage,sg,sr_mod,sd_mod,libata
ohci_hcd               25348  0 
ehci_hcd               37900  0 
usbcore               146028  8 usb_storage,libusual,snd_usb_audio,snd_usb_lib,lirc_mceusb2,ohci_hcd,ehci_hcd
thermal                16796  0 
processor              36872  2 acpi_cpufreq,thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  10 


```

---

### Post by DarK SouL on 2008-04-13
> **Trollslayer said:**
> The internal player is poor, set it to use VLC
vlc --fullscreen %s vlc:quit

Did that and it still does the same :(

---

### Post by warp99 on 2008-04-13
> I dont know where to select PAL/SECAM from, is it on the setup? There is no option like that in TV Settings.

That's a TV standard. In the United States we use NTSC. Other parts of the world use PAL/SECAM. NTSC or PAL/SECAM, you can't have both. If you don't know what your standard is, where do you live?

[http://www.videouniversity.com/standard.htm](http://www.videouniversity.com/standard.htm)

Go to Utilities/Setup > Setup > TV Settings > Recording Profiles change your recording screen size for your profiles from 480x480 to 720x480 for NTSC **or** 720x576 for PAL/SECAM.

---

### Post by DarK SouL on 2008-04-13
> **warp99 said:**
> That's a TV standard. In the United States we use NTSC. Other parts of the world use PAL/SECAM. NTSC or PAL/SECAM, you can't have both. If you don't know what your standard is, where do you live?

[http://www.videouniversity.com/standard.htm](http://www.videouniversity.com/standard.htm)

Go to Utilities/Setup > Setup > TV Settings > Recording Profiles change your recording screen size for your profiles from 480x480 to 720x480 for NTSC **or** 720x576 for PAL/SECAM.

Ah ok, I understand now, I am in the US and the screen size is set to 720x480 for NTSC

---

### Post by warp99 on 2008-04-13
> **DarK SouL said:**
> Did that and it still does the same :(

Are you running 5.1 surround sound? If so change that in Utilites/Setup > Setup > General and change "Max Audio Channels" to stereo. Also the 'Audio Ouput Device' in the same screen should be set to 'Alsa Default' and if the setting "Agressive Sound card Buffering" box is ticked please un-tick that box.

---

### Post by DarK SouL on 2008-04-13
> **warp99 said:**
> Are you running 5.1 surround sound? If so change that in Utilites/Setup > Setup > General and change "Max Audio Channels" to stereo. Also the 'Audio Ouput Device' in the same screen should be set to 'Alsa Default' and if the setting "Agressive Sound card Buffering" box is ticked please un-tick that box.

I changed it to alsa:default, but max audio channels was in stereo and aggressive sound card buffering was unticked, but its still doing it.  This is so frustrating.

---

### Post by warp99 on 2008-04-13
You particular on-board sound card has numerous problems. It's actually a Realtek ALC883 card because it has this chipset. Try some of the settings at the MythTV wiki:

[http://www.mythtv.org/wiki/index.php/Intel_HD_Audio_-_Realtek_ALC88x](http://www.mythtv.org/wiki/index.php/Intel_HD_Audio_-_Realtek_ALC88x)

If your using Gutsy 7.10 the Alsa version is a little old. You may want to install the newer version. This help guide will show you how:

[https://help.ubuntu.com/community/SoundTroubleshooting?highlight=%28soundtrouble%29#head-083f68c150e8cc9de635a7ab89b8ccfc6100ecf8](https://help.ubuntu.com/community/SoundTroubleshooting?highlight=%28soundtrouble%29#head-083f68c150e8cc9de635a7ab89b8ccfc6100ecf8)

You have to compile it, but it's not that difficult.

Edit:
You can also install the linux-backports-modules if you haven't already.

---

### Post by DarK SouL on 2008-04-20
Sorry for the delay, but I was trying different things and even formatted the computer a few times, but was not able to solve this problem.  

I am running Hardy so I guess I have the latest ALSA version, and I do an apt-update frequently just in case.

I also tried this ([http://www.mythtv.org/wiki/index.php/Intel_HD_Audio_-_Realtek_ALC88x](http://www.mythtv.org/wiki/index.php/Intel_HD_Audio_-_Realtek_ALC88x)) but to no avail, it just wont work.  Now I am looking for another alternatives like freevo and linuxmce, if I cannot make them work I will just go back to vista, this is too much work and time wasted for a simple thing.

Thanks for all the help.

---

### Post by DarK SouL on 2008-04-20
I think my problem could be related to this bug.  

[https://bugs.launchpad.net/mythtv/+bug/180814/+index#](https://bugs.launchpad.net/mythtv/+bug/180814/+index#)

I will keep an eye on it to see what happens.

---

### Post by warp99 on 2008-05-06
Disregard this post, different driver is in use.

---

