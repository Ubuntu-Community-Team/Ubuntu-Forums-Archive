---
title: "Mythtv and bt878 livetv crash"
date: 2010-11-20
forum: Mythbuntu
---

### Post by gilson585 on 2010-11-20
I run Ubuntu 10.04 and have mythtv 0.24 autobuilds
2.6.32-25-generic
AMD X2 3.1Ghz, 4GB of mem, GTX 260, 2x 250GB in storage group

When I try to use my WinTV Go card in livetv mode it works till I try to change the channel. Screen goes black for a few secs and either crashes to desktop or displays interlaced video (at incorrect aspect ratio) w/o sound. It will work however if I tune to one of my DVB-C channels and then back to this card (Really annoying BTW).

Now it's worked fine b4 and I haven't made any major changes to the sys, just typical updates. Last I knew it worked for sure was on 0.23.1

Using audio out from tuner card to motherboard linein.
WinTV-Go has a sticker that says NTSC 44981 Rev E199
```
gilson585@Daves-MediaPC:~$ sudo lspci -v
[sudo] password for gilson585: 
00:00.0 Host bridge: ATI Technologies Inc RX780/RX790 Chipset Host Bridge
	Subsystem: ASUSTeK Computer Inc. Device 8353
	Flags: bus master, 66MHz, medium devsel, latency 0
	Capabilities: [c4] HyperTransport: Slave or Primary Interface
	Capabilities: [40] HyperTransport: Retry Mode
	Capabilities: [54] HyperTransport: UnitID Clumping
	Capabilities: [9c] HyperTransport: #1a

00:02.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (external gfx0 port A)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: f8000000-fb9fffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Root Port (Slot-), MSI 00
	Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [b0] Subsystem: ASUSTeK Computer Inc. Device 8353
	Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
	Capabilities: [100] Vendor Specific Information <?>
	Capabilities: [110] Virtual Channel <?>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:04.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port A)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Memory behind bridge: fba00000-fbbfffff
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Root Port (Slot-), MSI 00
	Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [b0] Subsystem: ASUSTeK Computer Inc. Device 8353
	Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
	Capabilities: [100] Vendor Specific Information <?>
	Capabilities: [110] Virtual Channel <?>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:09.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port E)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Memory behind bridge: fbc00000-fbdfffff
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Root Port (Slot-), MSI 00
	Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [b0] Subsystem: ASUSTeK Computer Inc. Device 8353
	Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
	Capabilities: [100] Vendor Specific Information <?>
	Capabilities: [110] Virtual Channel <?>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:0a.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port F)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: fbf00000-fbffffff
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Root Port (Slot-), MSI 00
	Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [b0] Subsystem: ASUSTeK Computer Inc. Device 8353
	Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
	Capabilities: [100] Vendor Specific Information <?>
	Capabilities: [110] Virtual Channel <?>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode] (prog-if 01)
	Subsystem: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 22
	I/O ports at c000 [size=8]
	I/O ports at b000 [size=4]
	I/O ports at a000 [size=8]
	I/O ports at 9000 [size=4]
	I/O ports at 8000 [size=16]
	Memory at f7fffc00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [60] Power Management version 2
	Capabilities: [70] SATA HBA <?>
	Kernel driver in use: ahci
	Kernel modules: ahci

00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10)
	Subsystem: ASUSTeK Computer Inc. Device 82ef
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	Memory at f7ffe000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller (prog-if 10)
	Subsystem: ASUSTeK Computer Inc. Device 82ef
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	Memory at f7ffd000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20)
	Subsystem: ASUSTeK Computer Inc. Device 82ef
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	Memory at f7fff800 (32-bit, non-prefetchable) [size=256]
	Capabilities: [c0] Power Management version 2
	Capabilities: [e4] Debug port: BAR=1 offset=00e0
	Kernel driver in use: ehci_hcd

00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10)
	Subsystem: ASUSTeK Computer Inc. Device 82ef
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at f7ffc000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller (prog-if 10)
	Subsystem: ASUSTeK Computer Inc. Device 82ef
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at f7ffb000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20)
	Subsystem: ASUSTeK Computer Inc. Device 82ef
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
	Memory at f7fff400 (32-bit, non-prefetchable) [size=256]
	Capabilities: [c0] Power Management version 2
	Capabilities: [e4] Debug port: BAR=1 offset=00e0
	Kernel driver in use: ehci_hcd

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
	Subsystem: ASUSTeK Computer Inc. Device 82ef
	Flags: 66MHz, medium devsel
	Capabilities: [b0] HyperTransport: MSI Mapping Enable- Fixed+
	Kernel modules: i2c-piix4

00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller (prog-if 8a [Master SecP PriP])
	Subsystem: ASUSTeK Computer Inc. Device 82ef
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at ff00 [size=16]
	Capabilities: [70] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Kernel driver in use: pata_atiixp
	Kernel modules: pata_atiixp

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
	Subsystem: ASUSTeK Computer Inc. Device 837b
	Flags: bus master, slow devsel, latency 64, IRQ 16
	Memory at f7ff4000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
	Subsystem: ASUSTeK Computer Inc. Device 82ef
	Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (prog-if 01)
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=64
	Prefetchable memory behind bridge: f6f00000-f6ffffff

00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller (prog-if 10)
	Subsystem: ASUSTeK Computer Inc. Device 82ef
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at f7ffa000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
	Flags: fast devsel
	Capabilities: [80] HyperTransport: Host or Secondary Interface

00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
	Flags: fast devsel
	Kernel modules: amd64_edac_mod

00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
	Flags: fast devsel
	Capabilities: [f0] Secure device <?>

00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
	Flags: fast devsel

01:00.0 VGA compatible controller: nVidia Corporation GT200 [GeForce GTX 260] (rev a1)
	Subsystem: Device 19f1:0aba
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at f8000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at dc00 [size=128]
	[virtual] Expansion ROM at fb980000 [disabled] [size=512K]
	Capabilities: [60] Power Management version 3
	Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [78] Express Endpoint, MSI 00
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [128] Power Budgeting <?>
	Capabilities: [600] Vendor Specific Information <?>
	Kernel driver in use: nvidia
	Kernel modules: nvidia-current, nvidiafb, nouveau

02:00.0 Multimedia video controller: Conexant Systems, Inc. Hauppauge Inc. HDPVR-1250 model 1196 (rev 04)
	Subsystem: Hauppauge computer works Inc. Device 2259
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at fba00000 (64-bit, non-prefetchable) [size=2M]
	Capabilities: [40] Express Endpoint, MSI 00
	Capabilities: [80] Power Management version 3
	Capabilities: [90] Vital Product Data <?>
	Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [200] Virtual Channel <?>
	Kernel driver in use: cx23885
	Kernel modules: cx23885

03:00.0 Multimedia video controller: Conexant Systems, Inc. CX23885 PCI Video and Audio Decoder (rev 02)
	Subsystem: Hauppauge computer works Inc. Device 7911
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at fbc00000 (64-bit, non-prefetchable) [size=2M]
	Capabilities: [40] Express Endpoint, MSI 00
	Capabilities: [80] Power Management version 2
	Capabilities: [90] Vital Product Data <?>
	Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [200] Virtual Channel <?>
	Kernel driver in use: cx23885
	Kernel modules: cx23885

04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
	Subsystem: ASUSTeK Computer Inc. Device 8385
	Flags: bus master, fast devsel, latency 0, IRQ 29
	I/O ports at e800 [size=256]
	Memory at fbfff000 (64-bit, non-prefetchable) [size=4K]
	Expansion ROM at fbfc0000 [disabled] [size=128K]
	Capabilities: [40] Power Management version 2
	Capabilities: [48] Vital Product Data <?>
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
	Capabilities: [60] Express Endpoint, MSI 00
	Capabilities: [84] Vendor Specific Information <?>
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [12c] Virtual Channel <?>
	Capabilities: [148] Device Serial Number 00-e0-4c-68-00-00-00-40
	Capabilities: [154] Power Budgeting <?>
	Kernel driver in use: r8169
	Kernel modules: r8169

05:07.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
	Subsystem: Hauppauge computer works Inc. Device 13eb
	Flags: bus master, medium devsel, latency 64, IRQ 21
	Memory at f6fff000 (32-bit, prefetchable) [size=4K]
	Capabilities: [44] Vital Product Data <?>
	Capabilities: [4c] Power Management version 2
	Kernel driver in use: bttv
	Kernel modules: bttv

05:07.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
	Subsystem: Hauppauge computer works Inc. Device 13eb
	Flags: bus master, medium devsel, latency 64, IRQ 21
	Memory at f6ffe000 (32-bit, prefetchable) [size=4K]
	Capabilities: [44] Vital Product Data <?>
	Capabilities: [4c] Power Management version 2
	Kernel driver in use: Bt87x
	Kernel modules: snd-bt87x
```
```
gilson585@Daves-MediaPC:~$ dmesg | grep bttv
[   20.444112] bttv: driver version 0.9.18 loaded
[   20.444114] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   20.564868] bttv: Bt8xx card found (0).
[   20.564884] bttv 0000:05:07.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   20.564893] bttv0: Bt878 (rev 17) at 0000:05:07.0, irq: 21, latency: 64, mmio: 0xf6fff000
[   20.565725] bttv0: detected: Hauppauge WinTV [card=10], PCI subsystem ID is 0070:13eb
[   20.565727] bttv0: using: Hauppauge (bt878) [card=10,autodetected]
[   20.565728] IRQ 21/bttv0: IRQF_DISABLED is not guaranteed on shared IRQs
[   20.565761] bttv0: gpio: en=00000000, out=00000000 in=00ffffdb [init]
[   20.568264] bttv0: Hauppauge/Voodoo msp34xx: reset line init [5]
[   20.618035] bttv0: Hauppauge eeprom indicates model#44981
[   20.618037] bttv0: tuner type=50
[   20.668604] bttv0: audio absent, no audio device found!
[   20.688454] bttv0: registered device video0
[   20.688472] bttv0: registered device vbi0
[   20.688500] bttv0: PLL: 28636363 => 35468950 ..
[   28.385400] bttv0: PLL can sleep, using XTAL (28636363).
```
mythbackend.log has no interesting info
```
2010-11-20 15:21:26.488 mythbackend version: branches/release-0-24-fixes [27299] www.mythtv.org
2010-11-20 15:21:26.626 Using runtime prefix = /usr
2010-11-20 15:21:26.701 Using configuration directory = /home/mythtv/.mythtv
2010-11-20 15:21:26.856 Empty LocalHostName.
2010-11-20 15:21:26.891 Using localhost value of Daves-MediaPC
2010-11-20 15:21:26.951 New DB connection, total: 1
2010-11-20 15:21:27.021 Connected to database 'mythconverg' at host: localhost
2010-11-20 15:21:27.104 Closing DB connection named 'DBManager0'
2010-11-20 15:21:27.133 Connected to database 'mythconverg' at host: localhost
2010-11-20 15:21:27.178 Current locale EN_US
2010-11-20 15:21:27.182 Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
2010-11-20 15:21:27.196 Current MythTV Schema Version (DBSchemaVer): 1264
2010-11-20 15:21:27.218 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
2010-11-20 15:21:27.237 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2010-11-20 15:21:27.241 Enabling Upnpmedia rebuild thread.
2010-11-20 15:21:27.249 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2010-11-20 15:21:28.459 MythBackend: Starting up as the master server.
2010-11-20 15:21:28.548 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2010-11-20 15:21:28.563 New DB connection, total: 2
2010-11-20 15:21:28.607 Connected to database 'mythconverg' at host: localhost
2010-11-20 15:21:30.881 New DB connection, total: 3
2010-11-20 15:21:30.897 Connected to database 'mythconverg' at host: localhost
2010-11-20 15:21:31.026 New DB scheduler connection
2010-11-20 15:21:31.036 Connected to database 'mythconverg' at host: localhost
2010-11-20 15:21:31.055 Main::Registering HttpStatus Extension
2010-11-20 15:21:31.072 Enabled verbose msgs:  important general
2010-11-20 15:21:31.114 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-11-20 15:21:31.661 MainServer::ANN Monitor
2010-11-20 15:21:31.664 adding: Daves-MediaPC as a client (events: 0)
2010-11-20 15:21:31.672 MainServer::ANN Monitor
2010-11-20 15:21:31.680 adding: Daves-MediaPC as a client (events: 1)
2010-11-20 15:21:34.041 Reschedule requested for id -1.
2010-11-20 15:21:35.301 Scheduled 1163 items in 1.3 = 0.19 match + 1.06 place
2010-11-20 15:21:35.315 Seem to be woken up by USER
2010-11-20 15:21:37.249 UPnpMedia: BuildMediaMap - no VideoStartupDir set,  skipping scan.
2010-11-20 15:21:38.121 MainServer::ANN Playback
2010-11-20 15:21:38.130 adding: Daves-MediaPC as a client (events: 0)
2010-11-20 15:21:38.155 TVRec(5): Changing from None to WatchingLiveTV
2010-11-20 15:21:38.173 TVRec(5): HW Tuner: 5->5
2010-11-20 15:21:38.186 LoadFromScheduler(): Error, called from backend.
2010-11-20 15:21:38.216 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2010-11-20 15:21:38.392 Finished recording Midday News: channel 7009
2010-11-20 15:21:38.418 LoadFromScheduler(): Error, called from backend.
2010-11-20 15:21:38.423 recording already exists...
2010-11-20 15:21:38.423 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2010-11-20 15:21:38.434 Finished recording Midday News: channel 7009
2010-11-20 15:21:39.839 RecBase(5:/dev/video0): GetKeyframePositions(1,9223372036854775807,#0) out of 1
2010-11-20 15:21:39.905 RecBase(5:/dev/video0): GetKeyframePositions(1,9223372036854775807,#1) out of 2
2010-11-20 15:21:51.518 TVRec(5): HW Tuner: 5->5
2010-11-20 15:21:51.547 LoadFromScheduler(): Error, called from backend.
2010-11-20 15:21:51.553 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2010-11-20 15:21:51.656 Finished recording Midday News: channel 7009
2010-11-20 15:21:51.909 Finished recording College Football Countdown: channel 7013
2010-11-20 15:21:51.930 LoadFromScheduler(): Error, called from backend.
2010-11-20 15:21:51.937 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2010-11-20 15:21:51.939 recording already exists...
2010-11-20 15:21:51.961 Finished recording College Football Countdown: channel 7013
2010-11-20 15:21:51.970 MainServer::ANN Monitor
2010-11-20 15:21:51.971 adding: Daves-MediaPC as a client (events: 0)
2010-11-20 15:21:52.023 MainServer::ANN Monitor
2010-11-20 15:21:52.047 adding: Daves-MediaPC as a client (events: 1)
2010-11-20 15:22:08.907 TVRec(5): Changing from WatchingLiveTV to None
2010-11-20 15:22:09.133 Finished recording College Football Countdown: channel 7013
```
mythtvfrontend.log has some info but is cryptic to me
```
Starting mythfrontend.real..
2010-11-20 15:21:28.593 mythfrontend version: branches/release-0-24-fixes [27299] www.mythtv.org
2010-11-20 15:21:28.593 Using runtime prefix = /usr
2010-11-20 15:21:28.593 Using configuration directory = /home/gilson585/.mythtv
2010-11-20 15:21:28.594 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
2010-11-20 15:21:28.594 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2010-11-20 15:21:28.594 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2010-11-20 15:21:29.181 Empty LocalHostName.
2010-11-20 15:21:29.182 Using localhost value of Daves-MediaPC
2010-11-20 15:21:29.191 New DB connection, total: 1
2010-11-20 15:21:29.193 Connected to database 'mythconverg' at host: localhost
2010-11-20 15:21:29.197 Closing DB connection named 'DBManager0'
2010-11-20 15:21:29.198 Connected to database 'mythconverg' at host: localhost
2010-11-20 15:21:29.199 Current locale EN_US
2010-11-20 15:21:29.199 Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
2010-11-20 15:21:29.403 ScreenSaverX11Private: Gnome screen saver support enabled
2010-11-20 15:21:29.404 DPMS is active.
2010-11-20 15:21:29.433 Desktop video mode: 1024x768 60.004 Hz
2010-11-20 15:21:29.459 Enabled verbose msgs:  important general
2010-11-20 15:21:29.461 Loading en_us translation for module mythfrontend
2010-11-20 15:21:29.467 LIRC: Successfully initialized '/dev/lircd' using '/home/gilson585/.lircrc' config
2010-11-20 15:21:29.467 JoystickMenuThread: Joystick disabled - Failed to read /home/gilson585/.mythtv/joystickmenurc
2010-11-20 15:21:29.525 Using Frameless Window
2010-11-20 15:21:29.525 Using Full Screen Window
2010-11-20 15:21:29.653 Using the OpenGL painter
2010-11-20 15:21:29.725 OpenGL: OpenGL vendor  : NVIDIA Corporation
2010-11-20 15:21:29.725 OpenGL: OpenGL renderer: GeForce GTX 260/PCI/SSE2
2010-11-20 15:21:29.725 OpenGL: OpenGL version : 3.3.0 NVIDIA 260.19.21
2010-11-20 15:21:29.726 OpenGL: Max texture size: 8192 x 8192
2010-11-20 15:21:29.726 OpenGL: Max texture units: 4
2010-11-20 15:21:29.726 OpenGL: Direct rendering: Yes
2010-11-20 15:21:29.726 OpenGL: Initialised MythRenderOpenGL
2010-11-20 15:21:30.094 New DB connection, total: 2
2010-11-20 15:21:30.094 Connected to database 'mythconverg' at host: localhost
2010-11-20 15:21:30.094 Current MythTV Schema Version (DBSchemaVer): 1264
2010-11-20 15:21:30.924 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
2010-11-20 15:21:30.924 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
2010-11-20 15:21:30.927 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
2010-11-20 15:21:30.927 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
2010-11-20 15:21:31.170 Pulse: PulseAudio suspend OK
2010-11-20 15:21:31.371 Pulse: PulseAudio resume OK
2010-11-20 15:21:31.446 Registering Internal as a media playback plugin.
2010-11-20 15:21:31.456 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2010-11-20 15:21:31.474 MediaMonitorUnix::AddDevice() - empty device path.
2010-11-20 15:21:31.474 MediaMonitorUnix::AddDevice() - empty device path.
2010-11-20 15:21:31.474 MediaMonitorUnix::AddDevice() - empty device path.
2010-11-20 15:21:31.475 MediaMonitorUnix::AddDevice() - empty device path.
2010-11-20 15:21:31.475 MediaMonitorUnix::AddDevice() - empty device path.
2010-11-20 15:21:31.475 MediaMonitorUnix::AddDevice() - empty device path.
2010-11-20 15:21:31.475 MediaMonitorUnix::AddDevice() - empty device path.
2010-11-20 15:21:31.476 MediaMonitorUnix::AddDevice() - empty device path.
2010-11-20 15:21:31.476 MediaMonitorUnix::AddDevice() - empty device path.
2010-11-20 15:21:31.476 MediaMonitorUnix::AddDevice() - empty device path.
2010-11-20 15:21:31.476 MediaMonitorUnix::AddDevice() - empty device path.
2010-11-20 15:21:31.476 MediaMonitorUnix::AddDevice() - empty device path.
2010-11-20 15:21:31.477 MediaMonitorUnix::AddDevice() - empty device path.
2010-11-20 15:21:31.477 MediaMonitorUnix::AddDevice() - empty device path.
2010-11-20 15:21:31.477 MediaMonitorUnix::AddDevice() - empty device path.
2010-11-20 15:21:31.477 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2010-11-20 15:21:31.480 Loading en_us translation for module mythmusic
2010-11-20 15:21:31.484 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1038
2010-11-20 15:21:31.491 Loading en_us translation for module mythvideo
2010-11-20 15:21:31.491 NetworkControl: Listening for remote connections on port 6546
2010-11-20 15:21:31.568 Found mainmenu.xml for theme 'Mythbuntu'
2010-11-20 15:21:31.660 MythCoreContext: Connecting to backend server: 192.168.1.4:6543 (try 1 of 1)
2010-11-20 15:21:31.660 Using protocol version 63
2010-11-20 15:21:38.120 TV: Attempting to change from None to WatchingLiveTV
2010-11-20 15:21:38.120 MythCoreContext: Connecting to backend server: 192.168.1.4:6543 (try 1 of 1)
2010-11-20 15:21:38.121 Using protocol version 63
2010-11-20 15:21:38.141 Spawning LiveTV Recorder -- begin
2010-11-20 15:21:38.605 Spawning LiveTV Recorder -- end
2010-11-20 15:21:38.608 We have a playbackURL(/var/lib/mythtv/livetv/7009_20101120152139.nuv) & cardtype(V4L)
2010-11-20 15:21:38.790 We have a RingBuffer
2010-11-20 15:21:38.972 Pulse: PulseAudio suspend OK
2010-11-20 15:21:38.994 Clearing OpenGL painter cache.
2010-11-20 15:21:39.123 VDPAU: Created 2 output surfaces.
2010-11-20 15:21:39.123 VDPAU: Version 1
2010-11-20 15:21:39.123 VDPAU: Information NVIDIA VDPAU Driver Shared Library  260.19.21  Thu Nov  4 21:46:12 PDT 2010
2010-11-20 15:21:39.123 VDPAU: Created VDPAU render device 1024x768
2010-11-20 15:21:39.235 Player(0): Video timing method: USleep with busy wait
2010-11-20 15:21:39.235 TV: Changing from None to WatchingLiveTV
2010-11-20 15:21:39.235 TV: State is LiveTV & mctx == ctx
2010-11-20 15:21:39.236 TV: UpdateOSDInput done
2010-11-20 15:21:39.236 TV: UpdateLCD done
2010-11-20 15:21:39.236 TV: ITVRestart done
2010-11-20 15:21:39.296 VDPAU Painter: Clearing VDPAU painter cache.
2010-11-20 15:21:39.296 MythPainter: 2 images not yet de-allocated.
2010-11-20 15:21:39.318 Clearing OpenGL painter cache.
2010-11-20 15:21:39.357 VDPAU: Created 2 output surfaces.
2010-11-20 15:21:39.357 VDPAU: Created VDPAU render device 1024x768
2010-11-20 15:21:39.545 Pulse: PulseAudio resume OK
2010-11-20 15:21:39.674 Pulse: PulseAudio suspend OK
[ac3 @ 0x7fcad49156e0] No channel layout specified. The encoder will guess the layout, but it might be incorrect.
2010-11-20 15:21:39.685 AO: Opening audio device 'iec958:CARD=SB,DEV=0' ch 2(2) sr 48000 sf signed 16 bit reenc 0
2010-11-20 15:21:39.685 Opening ALSA audio device 'iec958:AES0=0x6,AES1=0x82,AES2=0x0,AES3=0x2,CARD=SB,DEV=0'.
2010-11-20 15:21:39.798 AudioPlayer: Enabling Audio
2010-11-20 15:21:39.909 ScreenSaverX11Private: DPMS Deactivated 1
2010-11-20 15:21:39.931 VDPAU: Added 2 output surfaces (total 4, max 4)
2010-11-20 15:21:52.435 RingBuf(/var/lib/mythtv/livetv/7013_20101120152152.nuv) Warning: Not starting read ahead thread, already running
2010-11-20 15:21:52.436 Player(0): DecoderGetFrame() called with NULL decoder.
2010-11-20 15:21:56.254 VDPAU Painter: Clearing VDPAU painter cache.
2010-11-20 15:21:56.255 MythPainter: 3 images not yet de-allocated.
2010-11-20 15:21:56.295 Clearing OpenGL painter cache.
2010-11-20 15:21:56.333 VDPAU: Created 2 output surfaces.
2010-11-20 15:21:56.333 VDPAU: Created VDPAU render device 1024x768
2010-11-20 15:21:56.337 AFD Warning: ScanATSCCaptionStreams() called with no PMT
2010-11-20 15:21:56.338 AFD: Opened codec 0x7fcad5401290, id(MPEG4) type(Video)
2010-11-20 15:21:56.338 AudioPlayer: Disabling Audio, params(0,-1,-1)
2010-11-20 15:21:56.498 Pulse: PulseAudio resume OK
2010-11-20 15:21:56.598 Pulse: PulseAudio suspend OK
2010-11-20 15:21:56.608 AudioPlayer: Disabling Audio, reason is: Aborting Audio Reconfigure. Invalid audio parameters ch -1 fmt 0 @ -1Hz
2010-11-20 15:21:56.740 VDPAU: Added 2 output surfaces (total 4, max 4)
2010-11-20 15:22:08.718 TV: Attempting to change from WatchingLiveTV to None
2010-11-20 15:22:08.725 VDPAU Painter: Clearing VDPAU painter cache.
2010-11-20 15:22:08.906 Pulse: PulseAudio resume OK
2010-11-20 15:22:09.188 TV: Changing from WatchingLiveTV to None
2010-11-20 15:22:09.189 ScreenSaverX11Private: DPMS Reactivated 1
```

---

### Post by oregonbob on 2010-11-20
Man oh man I struggled and struggled with MythTV (junk IMHO) and numerous other TV packages to use with my 10.04, 10.10 and my Hauppage 1600HVR TV card. I spent uncountable man-hours tinkering with TV programs and the millions of settings in configuration.

Then I tried Kaffeine. Simple and it works great. It works better than anything else I tried with no muss or fuss. It even works great on Gnome.

---

### Post by gilson585 on 2010-11-20
lol but i like my dvr, I blame 0.24

---

### Post by gilson585 on 2010-11-21
Found a bug report concerning this issue here [http://svn.mythtv.org/trac/ticket/9201](http://svn.mythtv.org/trac/ticket/9201)
[http://svn.mythtv.org/trac/ticket/9177](http://svn.mythtv.org/trac/ticket/9177)

---

