---
title: "Screen freezes if monitor is plugged in"
date: 2013-07-03
forum: Multimedia Software
---

### Post by tiagoarruda on 2013-07-03
Hi guys, 

every time I connect a monitor to my notebook (dell latitude E6510) it freezes after a short time.
I've found out that the problem doesn't happens with kernel 3.10, but this kernel is unstable and I ended with other issues.

Here are some information about my system and logs about the error:
[COLOR=#000000]DELL LATITUDE | E6510[/COLOR]

[COLOR=#000000]Kernel: 3.9.8-030908-generic[/COLOR]

[COLOR=#000000]Distributor ID: Ubuntu[/COLOR]
[COLOR=#000000]Description: Ubuntu 12.10[/COLOR]
[COLOR=#000000]Release: 12.10[/COLOR]
[COLOR=#000000]Codename: quantal

dmesg
[/COLOR][   16.909660] Bluetooth: BNEP socket layer initialized
[   16.917880] type=1400 audit(1372782009.527:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1060 comm="apparmor_parser"
[   16.918468] type=1400 audit(1372782009.527:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=1060 comm="apparmor_parser"
[   16.965766] Bluetooth: RFCOMM TTY layer initialized
[   16.965779] Bluetooth: RFCOMM socket layer initialized
[   16.965780] Bluetooth: RFCOMM ver 1.11
[   17.040129] e1000e 0000:00:19.0: irq 46 for MSI/MSI-X
[   17.094833] input: DualPoint Stick as /devices/platform/i8042/serio1/input/input15
[   17.107822] input: AlpsPS/2 ALPS DualPoint TouchPad as /devices/platform/i8042/serio1/input/input16
[   17.143910] e1000e 0000:00:19.0: irq 46 for MSI/MSI-X
[   17.144014] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.340338] type=1400 audit(1372782009.951:7): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1107 comm="apparmor_parser"
[   17.340825] type=1400 audit(1372782009.951:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1107 comm="apparmor_parser"
[   17.341102] type=1400 audit(1372782009.951:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1107 comm="apparmor_parser"
[   17.342901] type=1400 audit(1372782009.951:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1111 comm="apparmor_parser"
[   17.343703] type=1400 audit(1372782009.955:11): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=1111 comm="apparmor_parser"
[   17.711642] input: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:03.0/0000:01:00.1/sound/card1/input17
[   17.711804] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:03.0/0000:01:00.1/sound/card1/input18
[   17.711942] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:03.0/0000:01:00.1/sound/card1/input19
[   17.712073] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:03.0/0000:01:00.1/sound/card1/input20
[   17.836745] /dev/vmmon[1256]: Module vmmon: registered with major=10 minor=165
[   17.836752] /dev/vmmon[1256]: Module vmmon: initialized
[   17.947960] [1288]: VMCI: shared components initialized.
[   17.947999] [1288]: VMCI: host components initialized.
[   17.948053] [1288]: VMCI: Module registered (name=vmci,major=10,minor=54).
[   17.948055] [1288]: VMCI: Using host personality
[   17.948057] [1288]: VMCI: Module (name=vmci) is initialized
[   20.304758] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx
[   20.304795] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   23.267626] /dev/vmnet: open called by PID 1897 (vmnet-bridge)
[   23.267635] /dev/vmnet: hub 0 does not exist, allocating memory.
[   23.267655] /dev/vmnet: port on hub 0 successfully opened
[   23.267670] bridge-eth0: up
[   23.267673] bridge-eth0: attached
[   23.811808] /dev/vmnet: open called by PID 1904 (vmnet-netifup)
[   23.811815] /dev/vmnet: hub 1 does not exist, allocating memory.
[   23.811828] /dev/vmnet: port on hub 1 successfully opened
[   23.926235] /dev/vmnet: open called by PID 1909 (vmnet-dhcpd)
[   23.926246] /dev/vmnet: port on hub 1 successfully opened
[   24.001177] /dev/vmnet: open called by PID 1913 (vmnet-natd)
[   24.001184] /dev/vmnet: hub 8 does not exist, allocating memory.
[   24.001197] /dev/vmnet: port on hub 8 successfully opened
[   24.002195] userif-3: sent link down event.
[   24.002198] userif-3: sent link up event.<7>[   24.003456] /dev/vmnet: open called by PID 1914 (vmnet-netifup)
[   24.003462] /dev/vmnet: port on hub 8 successfully opened
[   24.044200] /dev/vmnet: open called by PID 1916 (vmnet-dhcpd)
[   24.044210] /dev/vmnet: port on hub 8 successfully opened
[   24.407573] init: plymouth-stop pre-start process (2348) terminated with status 1
[   29.865614] userif-3: sent link down event.
[   29.865618] userif-3: sent link up event.userif-3: sent link down event.
[   30.987415] userif-3: sent link up event.userif-3: sent link down event.
[  861.523132] userif-3: sent link up event.<7>[  950.042877] /dev/vmmon[4708]: PTSC: initialized at 1728999000 Hz using TSC, TSCs are synchronized.
[  950.270415] /dev/vmmon[4708]: Monitor IPI vector: 0
[  953.202002] /dev/vmnet: open called by PID 4721 (vmx-vcpu-0)
[  953.202026] device eth0 entered promiscuous mode
[  953.202045] bridge-eth0: enabled promiscuous mode
[  953.202048] /dev/vmnet: port on hub 0 successfully opened
[ 1596.377874] audit_printk_skb: 54 callbacks suppressed
[ 1596.377878] type=1400 audit(1372783589.353:30): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=6691 comm="apparmor_parser"
[ 1596.378518] type=1400 audit(1372783589.357:31): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=6691 comm="apparmor_parser"
[ 1911.222671] userif-3: sent link down event.
[ 1911.222681] userif-3: sent link up event.userif-3: sent link down event.
[ 3512.765099] userif-3: sent link up event.userif-3: sent link down event.
[ 4244.994115] userif-3: sent link up event.userif-3: sent link down event.
[ 4407.744461] userif-3: sent link up event.<6>[ 6209.017872] dell_wmi: Received unknown WMI event (0x11)
[ 6874.650328] dell_wmi: Received unknown WMI event (0x11)
[ 7311.260301] userif-3: sent link down event.
[ 7311.260310] userif-3: sent link up event.userif-3: sent link down event.
[ 8105.164097] userif-3: sent link up event.userif-3: sent link down event.
[ 8514.496028] userif-3: sent link up event.<6>[10459.381339] dell_wmi: Received unknown WMI event (0x11)
[12631.045129] dell_wmi: Received unknown WMI event (0x11)
[18295.149052] nouveau E[     DRM] GPU lockup - switching to software fbcon
[18299.103756] nouveau E[Xorg[1243]] failed to idle channel 0xcccc0001 [Xorg[1243]]
[18302.102467] nouveau E[Xorg[1243]] failed to idle channel 0xcccc0001 [Xorg[1243]]
[18304.101922] nouveau E[   PFIFO][0000:01:00.0] channel 3 [Xorg[1243]] unload timeout
[18307.100441] nouveau E[Xorg[1243]] failed to idle channel 0xcccc0000 [Xorg[1243]]
[18310.099112] nouveau E[Xorg[1243]] failed to idle channel 0xcccc0000 [Xorg[1243]]
[18312.098502] nouveau E[   PFIFO][0000:01:00.0] channel 2 [Xorg[1243]] unload timeout
[18315.132955] nouveau E[compiz[2478]] failed to idle channel 0xcccc0000 [compiz[2478]]
[18318.131747] nouveau E[compiz[2478]] failed to idle channel 0xcccc0000 [compiz[2478]]
[18320.131063] nouveau E[   PFIFO][0000:01:00.0] channel 4 [compiz[2478]] unload timeout
[18332.157669] device eth0 left promiscuous mode
[18332.157703] bridge-eth0: disabled promiscuous mode
[18340.968463] unity-greeter[12140]: segfault at 18 ip 00007feba60fe616 sp 00007fff21d23450 error 4 in libxklavier.so.16.2.0[7feba60ee000+19000]

Xorg.0.log
[ 18328.043] (II) NOUVEAU(0): 720x400@70Hz
[ 18328.043] (II) NOUVEAU(0): 640x480@60Hz
[ 18328.043] (II) NOUVEAU(0): 640x480@67Hz
[ 18328.043] (II) NOUVEAU(0): 640x480@72Hz
[ 18328.043] (II) NOUVEAU(0): 640x480@75Hz
[ 18328.043] (II) NOUVEAU(0): 800x600@56Hz
[ 18328.043] (II) NOUVEAU(0): 800x600@60Hz
[ 18328.043] (II) NOUVEAU(0): 800x600@72Hz
[ 18328.043] (II) NOUVEAU(0): 800x600@75Hz
[ 18328.043] (II) NOUVEAU(0): 832x624@75Hz
[ 18328.043] (II) NOUVEAU(0): 1024x768@60Hz
[ 18328.043] (II) NOUVEAU(0): 1024x768@70Hz
[ 18328.043] (II) NOUVEAU(0): 1024x768@75Hz
[ 18328.043] (II) NOUVEAU(0): 1280x1024@75Hz
[ 18328.043] (II) NOUVEAU(0): 1152x864@75Hz
[ 18328.043] (II) NOUVEAU(0): Manufacturer's mask: 0
[ 18328.043] (II) NOUVEAU(0): Supported standard timings:
[ 18328.043] (II) NOUVEAU(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[ 18328.043] (II) NOUVEAU(0): #1: hsize: 1280  vsize 720  refresh: 60  vid: 49281
[ 18328.043] (II) NOUVEAU(0): #2: hsize: 1280  vsize 800  refresh: 60  vid: 129
[ 18328.043] (II) NOUVEAU(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[ 18328.043] (II) NOUVEAU(0): #4: hsize: 1440  vsize 900  refresh: 60  vid: 149
[ 18328.043] (II) NOUVEAU(0): #5: hsize: 1600  vsize 900  refresh: 60  vid: 49321
[ 18328.043] (II) NOUVEAU(0): #6: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[ 18328.043] (II) NOUVEAU(0): Supported detailed timing:
[ 18328.043] (II) NOUVEAU(0): clock: 148.5 MHz   Image Size:  477 x 268 mm
[ 18328.043] (II) NOUVEAU(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[ 18328.043] (II) NOUVEAU(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[ 18328.043] (II) NOUVEAU(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 81 kHz, PixClock max 175 MHz
[ 18328.043] (II) NOUVEAU(0): Monitor name: S22B300
[ 18328.043] (II) NOUVEAU(0): Serial No: HXFCB02562
[ 18328.043] (II) NOUVEAU(0): EDID (in hex):
[ 18328.043] (II) NOUVEAU(0): 	00ffffffffffff004c2dab0838423359
[ 18328.043] (II) NOUVEAU(0): 	301601030e301b782a90c1a259559c27
[ 18328.043] (II) NOUVEAU(0): 	0e5054bfef80714f81c0810081809500
[ 18328.043] (II) NOUVEAU(0): 	a9c0b3000101023a801871382d40582c
[ 18328.043] (II) NOUVEAU(0): 	4500dd0c1100001e000000fd00384b1e
[ 18328.043] (II) NOUVEAU(0): 	5111000a202020202020000000fc0053
[ 18328.043] (II) NOUVEAU(0): 	3232423330300a2020202020000000ff
[ 18328.043] (II) NOUVEAU(0): 	00485846434230323536320a2020009b
[ 18328.043] (II) NOUVEAU(0): Printing probed modes for output VGA-1
[ 18328.043] (II) NOUVEAU(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[ 18328.043] (II) NOUVEAU(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[ 18328.043] (II) NOUVEAU(0): Modeline "1600x900"x60.0  118.96  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz)
[ 18328.043] (II) NOUVEAU(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[ 18328.043] (II) NOUVEAU(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[ 18328.043] (II) NOUVEAU(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz e)
[ 18328.043] (II) NOUVEAU(0): Modeline "1280x800"x59.8   83.50  1280 1352 1480 1680  800 803 809 831 +hsync -vsync (49.7 kHz e)
[ 18328.043] (II) NOUVEAU(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[ 18328.043] (II) NOUVEAU(0): Modeline "1280x720"x60.0   74.44  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.7 kHz)
[ 18328.043] (II) NOUVEAU(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz e)
[ 18328.043] (II) NOUVEAU(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[ 18328.043] (II) NOUVEAU(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[ 18328.043] (II) NOUVEAU(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[ 18328.043] (II) NOUVEAU(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[ 18328.043] (II) NOUVEAU(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[ 18328.043] (II) NOUVEAU(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[ 18328.043] (II) NOUVEAU(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[ 18328.043] (II) NOUVEAU(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz e)
[ 18328.043] (II) NOUVEAU(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[ 18328.043] (II) NOUVEAU(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[ 18328.043] (II) NOUVEAU(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[ 18328.043] (II) NOUVEAU(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[ 18328.168] (II) NOUVEAU(0): EDID for output DP-1
[ 18328.296] (II) NOUVEAU(0): EDID for output DP-2
[ 18328.296] (II) NOUVEAU(0): Output eDP-1 connected
[ 18328.296] (II) NOUVEAU(0): Output VGA-1 connected
[ 18328.296] (II) NOUVEAU(0): Output DP-1 disconnected
[ 18328.296] (II) NOUVEAU(0): Output DP-2 disconnected
[ 18328.296] (II) NOUVEAU(0): Using fuzzy aspect match for initial modes
[ 18328.296] (II) NOUVEAU(0): Output eDP-1 using initial mode 1024x768
[ 18328.296] (II) NOUVEAU(0): Output VGA-1 using initial mode 1024x768
[ 18328.296] (II) NOUVEAU(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[ 18328.296] (--) NOUVEAU(0): Virtual size is 1024x768 (pitch 0)
[ 18328.296] (**) NOUVEAU(0):  Driver mode "1024x768": 63.5 MHz (scaled from 0.0 MHz), 47.8 kHz, 59.9 Hz
[ 18328.296] (II) NOUVEAU(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz e)
[ 18328.296] (**) NOUVEAU(0):  Driver mode "800x600": 38.2 MHz (scaled from 0.0 MHz), 37.4 kHz, 59.9 Hz
[ 18328.296] (II) NOUVEAU(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz e)
[ 18328.296] (**) NOUVEAU(0):  Driver mode "640x480": 23.8 MHz (scaled from 0.0 MHz), 29.7 kHz, 59.4 Hz
[ 18328.296] (II) NOUVEAU(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz e)
[ 18328.296] (**) NOUVEAU(0):  Driver mode "720x400": 22.2 MHz (scaled from 0.0 MHz), 24.8 kHz, 59.6 Hz
[ 18328.296] (II) NOUVEAU(0): Modeline "720x400"x59.6   22.25  720 744 808 896  400 403 413 417 -hsync +vsync (24.8 kHz e)
[ 18328.296] (**) NOUVEAU(0):  Driver mode "640x400": 20.0 MHz (scaled from 0.0 MHz), 25.0 kHz, 60.0 Hz
[ 18328.296] (II) NOUVEAU(0): Modeline "640x400"x60.0   20.00  640 664 720 800  400 403 409 417 -hsync +vsync (25.0 kHz e)
[ 18328.296] (**) NOUVEAU(0):  Driver mode "640x350": 17.5 MHz (scaled from 0.0 MHz), 21.9 kHz, 59.8 Hz
[ 18328.296] (II) NOUVEAU(0): Modeline "640x350"x59.8   17.50  640 664 720 800  350 353 363 366 -hsync +vsync (21.9 kHz e)
[ 18328.296] (**) NOUVEAU(0):  Driver mode "1366x768": 72.0 MHz (scaled from 0.0 MHz), 47.4 kHz, 60.0 Hz
[ 18328.296] (II) NOUVEAU(0): Modeline "1366x768"x60.0   72.00  1366 1414 1446 1520  768 771 776 790 +hsync -vsync (47.4 kHz eP)
[ 18328.296] (**) NOUVEAU(0):  Driver mode "1366x768": 48.0 MHz (scaled from 0.0 MHz), 31.6 kHz, 40.0 Hz
[ 18328.296] (II) NOUVEAU(0): Modeline "1366x768"x40.0   48.00  1366 1414 1446 1520  768 771 776 790 +hsync -vsync (31.6 kHz e)
[ 18328.296] (==) NOUVEAU(0): DPI set to (96, 96)
[ 18328.296] (II) Loading sub module "fb"
[ 18328.296] (II) LoadModule: "fb"
[ 18328.296] (II) Loading /usr/lib/xorg/modules/libfb.so
[ 18328.335] (II) Module fb: vendor="X.Org Foundation"
[ 18328.335] 	compiled for 1.13.0, module version = 1.0.0
[ 18328.335] 	ABI class: X.Org ANSI C Emulation, version 0.4
[ 18328.335] (II) Loading sub module "exa"
[ 18328.335] (II) LoadModule: "exa"
[ 18328.335] (II) Loading /usr/lib/xorg/modules/libexa.so
[ 18328.335] (II) Module exa: vendor="X.Org Foundation"
[ 18328.335] 	compiled for 1.13.0, module version = 2.6.0
[ 18328.335] 	ABI class: X.Org Video Driver, version 13.0
[ 18328.335] (II) Loading sub module "shadowfb"
[ 18328.335] (II) LoadModule: "shadowfb"
[ 18328.336] (II) Loading /usr/lib/xorg/modules/libshadowfb.so
[ 18328.336] (II) Module shadowfb: vendor="X.Org Foundation"
[ 18328.336] 	compiled for 1.13.0, module version = 1.0.0
[ 18328.336] 	ABI class: X.Org ANSI C Emulation, version 0.4
[ 18328.336] (II) UnloadModule: "vesa"
[ 18328.336] (II) Unloading vesa
[ 18328.336] (II) UnloadModule: "modesetting"
[ 18328.336] (II) Unloading modesetting
[ 18328.336] (II) UnloadModule: "fbdev"
[ 18328.336] (II) Unloading fbdev
[ 18328.336] (II) UnloadSubModule: "fbdevhw"
[ 18328.336] (II) Unloading fbdevhw
[ 18328.336] (--) Depth 24 pixmap format is 32 bpp
[ 18328.338] (II) NOUVEAU(0): Opened GPU channel 0
[ 18328.351] (II) NOUVEAU(0): [DRI2] Setup complete
[ 18328.351] (II) NOUVEAU(0): [DRI2]   DRI driver: nouveau
[ 18328.351] (II) NOUVEAU(0): [DRI2]   VDPAU driver: nouveau
[ 18328.353] (II) EXA(0): Driver allocated offscreen pixmaps
[ 18328.353] (II) EXA(0): Driver registered support for the following operations:
[ 18328.353] (II)         Solid
[ 18328.353] (II)         Copy
[ 18328.353] (II)         Composite (RENDER acceleration)
[ 18328.353] (II)         UploadToScreen
[ 18328.353] (II)         DownloadFromScreen
[ 18328.353] (==) NOUVEAU(0): Backing store disabled
[ 18328.353] (==) NOUVEAU(0): Silken mouse enabled
[ 18328.363] (II) NOUVEAU(0): [XvMC] Associated with Nouveau GeForce 8/9 Textured Video.
[ 18328.363] (II) NOUVEAU(0): [XvMC] Extension initialized.
[ 18328.363] (==) NOUVEAU(0): DPMS enabled
[ 18328.363] (II) NOUVEAU(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[ 18328.364] (--) RandR disabled
[ 18328.392] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[ 18328.392] (II) AIGLX: enabled GLX_INTEL_swap_event
[ 18328.392] (II) AIGLX: enabled GLX_ARB_create_context
[ 18328.392] (II) AIGLX: enabled GLX_ARB_create_context_profile
[ 18328.392] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[ 18328.392] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[ 18328.392] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[ 18328.392] (II) AIGLX: Loaded and initialized nouveau
[ 18328.392] (II) GLX: Initialized DRI2 GL provider for screen 0
[ 18328.394] (II) NOUVEAU(0): NVEnterVT is called.
[ 18340.410] (II) NOUVEAU(0): Setting screen physical size to 270 x 203
[ 18340.410] resize called 1024 768
[ 18340.502] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[ 18340.511] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[ 18340.511] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[ 18340.511] (II) LoadModule: "evdev"
[ 18340.512] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 18340.523] (II) Module evdev: vendor="X.Org Foundation"
[ 18340.523] 	compiled for 1.13.0, module version = 2.7.3
[ 18340.523] 	Module class: X.Org XInput Driver
[ 18340.523] 	ABI class: X.Org XInput driver, version 18.0
[ 18340.523] (II) Using input driver 'evdev' for 'Power Button'
[ 18340.523] (**) Power Button: always reports core events
[ 18340.523] (**) evdev: Power Button: Device: "/dev/input/event3"
[ 18340.523] (--) evdev: Power Button: Vendor 0 Product 0x1
[ 18340.523] (--) evdev: Power Button: Found keys
[ 18340.523] (II) evdev: Power Button: Configuring as keyboard
[ 18340.523] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[ 18340.523] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[ 18340.523] (**) Option "xkb_rules" "evdev"
[ 18340.523] (**) Option "xkb_model" "pc105"
[ 18340.523] (**) Option "xkb_layout" "br"
[ 18340.525] (II) XKB: reuse xkmfile /var/lib/xkb/server-A37B2EFB8B2398771EA3BE2A51A1034B516E3F38.xkm
[ 18340.525] (II) config/udev: Adding input device Video Bus (/dev/input/event8)
[ 18340.525] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[ 18340.525] (II) Using input driver 'evdev' for 'Video Bus'
[ 18340.525] (**) Video Bus: always reports core events
[ 18340.525] (**) evdev: Video Bus: Device: "/dev/input/event8"
[ 18340.525] (--) evdev: Video Bus: Vendor 0 Product 0x6
[ 18340.525] (--) evdev: Video Bus: Found keys
[ 18340.525] (II) evdev: Video Bus: Configuring as keyboard
[ 18340.525] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:1d/LNXVIDEO:01/input/input9/event8"
[ 18340.525] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[ 18340.525] (**) Option "xkb_rules" "evdev"
[ 18340.525] (**) Option "xkb_model" "pc105"
[ 18340.525] (**) Option "xkb_layout" "br"
[ 18340.526] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[ 18340.526] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[ 18340.526] (II) Using input driver 'evdev' for 'Power Button'
[ 18340.526] (**) Power Button: always reports core events
[ 18340.526] (**) evdev: Power Button: Device: "/dev/input/event1"
[ 18340.526] (--) evdev: Power Button: Vendor 0 Product 0x1
[ 18340.526] (--) evdev: Power Button: Found keys
[ 18340.526] (II) evdev: Power Button: Configuring as keyboard
[ 18340.526] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1/event1"
[ 18340.526] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[ 18340.526] (**) Option "xkb_rules" "evdev"
[ 18340.526] (**) Option "xkb_model" "pc105"
[ 18340.526] (**) Option "xkb_layout" "br"
[ 18340.526] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[ 18340.526] (II) No input driver specified, ignoring this device.
[ 18340.526] (II) This device may have been added with another device file.
[ 18340.526] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[ 18340.526] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[ 18340.527] (II) Using input driver 'evdev' for 'Sleep Button'
[ 18340.527] (**) Sleep Button: always reports core events
[ 18340.527] (**) evdev: Sleep Button: Device: "/dev/input/event2"
[ 18340.527] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[ 18340.527] (--) evdev: Sleep Button: Found keys
[ 18340.527] (II) evdev: Sleep Button: Configuring as keyboard
[ 18340.527] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2/event2"
[ 18340.527] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 9)
[ 18340.527] (**) Option "xkb_rules" "evdev"
[ 18340.527] (**) Option "xkb_model" "pc105"
[ 18340.527] (**) Option "xkb_layout" "br"
[ 18340.527] (II) config/udev: Adding drm device (/dev/dri/card0)
[ 18340.527] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=9 (/dev/input/event16)
[ 18340.527] (II) No input driver specified, ignoring this device.
[ 18340.527] (II) This device may have been added with another device file.
[ 18340.527] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=8 (/dev/input/event17)
[ 18340.527] (II) No input driver specified, ignoring this device.
[ 18340.527] (II) This device may have been added with another device file.
[ 18340.528] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=7 (/dev/input/event18)
[ 18340.528] (II) No input driver specified, ignoring this device.
[ 18340.528] (II) This device may have been added with another device file.
[ 18340.528] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=3 (/dev/input/event19)
[ 18340.528] (II) No input driver specified, ignoring this device.
[ 18340.528] (II) This device may have been added with another device file.
[ 18340.528] (II) config/udev: Adding input device Laptop_Integrated_Webcam_3M (/dev/input/event9)
[ 18340.528] (**) Laptop_Integrated_Webcam_3M: Applying InputClass "evdev keyboard catchall"
[ 18340.528] (II) Using input driver 'evdev' for 'Laptop_Integrated_Webcam_3M'
[ 18340.528] (**) Laptop_Integrated_Webcam_3M: always reports core events
[ 18340.528] (**) evdev: Laptop_Integrated_Webcam_3M: Device: "/dev/input/event9"
[ 18340.528] (--) evdev: Laptop_Integrated_Webcam_3M: Vendor 0x5ca Product 0x1814
[ 18340.528] (--) evdev: Laptop_Integrated_Webcam_3M: Found keys
[ 18340.528] (II) evdev: Laptop_Integrated_Webcam_3M: Configuring as keyboard
[ 18340.528] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.0/input/input10/event9"
[ 18340.528] (II) XINPUT: Adding extended input device "Laptop_Integrated_Webcam_3M" (type: KEYBOARD, id 10)
[ 18340.528] (**) Option "xkb_rules" "evdev"
[ 18340.528] (**) Option "xkb_model" "pc105"
[ 18340.528] (**) Option "xkb_layout" "br"
[ 18340.529] (II) config/udev: Adding input device HDA Intel MID Mic (/dev/input/event10)
[ 18340.529] (II) No input driver specified, ignoring this device.
[ 18340.529] (II) This device may have been added with another device file.
[ 18340.529] (II) config/udev: Adding input device HDA Intel MID Dock Mic (/dev/input/event11)
[ 18340.529] (II) No input driver specified, ignoring this device.
[ 18340.529] (II) This device may have been added with another device file.
[ 18340.529] (II) config/udev: Adding input device HDA Intel MID Headphone (/dev/input/event12)
[ 18340.529] (II) No input driver specified, ignoring this device.
[ 18340.529] (II) This device may have been added with another device file.
[ 18340.529] (II) config/udev: Adding input device HDA Intel MID Dock Line Out (/dev/input/event13)
[ 18340.529] (II) No input driver specified, ignoring this device.
[ 18340.529] (II) This device may have been added with another device file.
[ 18340.530] (II) config/udev: Adding input device LITEON Technology USB Keyboard (/dev/input/event5)
[ 18340.530] (**) LITEON Technology USB Keyboard: Applying InputClass "evdev keyboard catchall"
[ 18340.530] (II) Using input driver 'evdev' for 'LITEON Technology USB Keyboard'
[ 18340.530] (**) LITEON Technology USB Keyboard: always reports core events
[ 18340.530] (**) evdev: LITEON Technology USB Keyboard: Device: "/dev/input/event5"
[ 18340.530] (--) evdev: LITEON Technology USB Keyboard: Vendor 0x45e Product 0x78c
[ 18340.530] (--) evdev: LITEON Technology USB Keyboard: Found keys
[ 18340.530] (II) evdev: LITEON Technology USB Keyboard: Configuring as keyboard
[ 18340.530] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1.3/2-1.1.3:1.0/input/input5/event5"
[ 18340.530] (II) XINPUT: Adding extended input device "LITEON Technology USB Keyboard" (type: KEYBOARD, id 11)
[ 18340.530] (**) Option "xkb_rules" "evdev"
[ 18340.530] (**) Option "xkb_model" "pc105"
[ 18340.530] (  **) Option "xkb_layout" "br"
[ 18340.530] (II) config/udev: Adding input device SIGMACHIP Usb Mouse (/dev/input/event6)
[ 18340.530] (**) SIGMACHIP Usb Mouse: Applying InputClass "evdev pointer catchall"
[ 18340.530] (II) Using input driver 'evdev' for 'SIGMACHIP Usb Mouse'
[ 18340.530] (**) SIGMACHIP Usb Mouse: always reports core events
[ 18340.530] (**) evdev: SIGMACHIP Usb Mouse: Device: "/dev/input/event6"
[ 18340.530] (--) evdev: SIGMACHIP Usb Mouse: Vendor 0x1c4f Product 0x3
[ 18340.530] (--) evdev: SIGMACHIP Usb Mouse: Found 9 mouse buttons
[ 18340.530] (--) evdev: SIGMACHIP Usb Mouse: Found scroll wheel(s)
[ 18340.530] (--) evdev: SIGMACHIP Usb Mouse: Found relative axes
[ 18340.530] (--) evdev: SIGMACHIP Usb Mouse: Found x and y relative axes
[ 18340.530] (II) evdev: SIGMACHIP Usb Mouse: Configuring as mouse
[ 18340.530] (II) evdev: SIGMACHIP Usb Mouse: Adding scrollwheel support
[ 18340.530] (**) evdev: SIGMACHIP Usb Mouse: YAxisMapping: buttons 4 and 5
[ 18340.530] (**) evdev: SIGMACHIP Usb Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[ 18340.530] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1.4/2-1.1.4:1.0/input/input7/event6"
[ 18340.530] (II) XINPUT: Adding extended input device "SIGMACHIP Usb Mouse" (type: MOUSE, id 12)
[ 18340.530] (II) evdev: SIGMACHIP Usb Mouse: initialized for relative axes.
[ 18340.531] (**) SIGMACHIP Usb Mouse: (accel) keeping acceleration scheme 1
[ 18340.531] (**) SIGMACHIP Usb Mouse: (accel) acceleration profile 0
[ 18340.531] (**) SIGMACHIP Usb Mouse: (accel) acceleration factor: 2.000
[ 18340.531] (**) SIGMACHIP Usb Mouse: (accel) acceleration threshold: 4
[ 18340.531] (II) config/udev: Adding input device SIGMACHIP Usb Mouse (/dev/input/mouse0)
[ 18340.531] (II) No input driver specified, ignoring this device.
[ 18340.531] (II) This device may have been added with another device file.
[ 18340.531] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[ 18340.531] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[ 18340.531] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[ 18340.531] (**) AT Translated Set 2 keyboard: always reports core events
[ 18340.531] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[ 18340.531] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[ 18340.531] (--) evdev: AT Translated Set 2 keyboard: Found keys
[ 18340.531] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[ 18340.531] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[ 18340.531] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 13)
[ 18340.531] (**) Option "xkb_rules" "evdev"
[ 18340.531] (**) Option "xkb_model" "pc105"
[ 18340.531] (**) Option "xkb_layout" "br"
[ 18340.532] (II) config/udev: Adding input device DualPoint Stick (/dev/input/event14)
[ 18340.532] (**) DualPoint Stick: Applying InputClass "evdev pointer catchall"
[ 18340.532] (**) DualPoint Stick: Applying InputClass "trackpoint catchall"
[ 18340.532] (II) Using input driver 'evdev' for 'DualPoint Stick'
[ 18340.532] (**) DualPoint Stick: always reports core events
[ 18340.532] (**) evdev: DualPoint Stick: Device: "/dev/input/event14"
[ 18340.532] (--) evdev: DualPoint Stick: Vendor 0x2 Product 0x8
[ 18340.532] (--) evdev: DualPoint Stick: Found 3 mouse buttons
[ 18340.532] (--) evdev: DualPoint Stick: Found relative axes
[ 18340.532] (--) evdev: DualPoint Stick: Found x and y relative axes
[ 18340.532] (II) evdev: DualPoint Stick: Configuring as mouse
[ 18340.532] (**) Option "Emulate3Buttons" "true"
[ 18340.532] (**) Option "EmulateWheel" "true"
[ 18340.532] (**) Option "EmulateWheelButton" "2"
[ 18340.532] (**) Option "YAxisMapping" "4 5"
[ 18340.532] (**) evdev: DualPoint Stick: YAxisMapping: buttons 4 and 5
[ 18340.532] (**) Option "XAxisMapping" "6 7"
[ 18340.532] (**) evdev: DualPoint Stick: XAxisMapping: buttons 6 and 7
[ 18340.532] (**) evdev: DualPoint Stick: EmulateWheelButton: 2, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[ 18340.532] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input15/event14"
[ 18340.532] (II) XINPUT: Adding extended input device "DualPoint Stick" (type: MOUSE, id 14)
[ 18340.532] (II) evdev: DualPoint Stick: initialized for relative axes.
[ 18340.532] (**) DualPoint Stick: (accel) keeping acceleration scheme 1
[ 18340.532] (**) DualPoint Stick: (accel) acceleration profile 0
[ 18340.532] (**) DualPoint Stick: (accel) acceleration factor: 2.000
[ 18340.532] (**) DualPoint Stick: (accel) acceleration threshold: 4
[ 18340.532] (II) config/udev: Adding input device DualPoint Stick (/dev/input/mouse1)
[ 18340.532] (II) No input driver specified, ignoring this device.
[ 18340.532] (II) This device may have been added with another device file.
[ 18340.533] (II) config/udev: Adding input device AlpsPS/2 ALPS DualPoint TouchPad (/dev/input/event15)
[ 18340.533] (**) AlpsPS/2 ALPS DualPoint TouchPad: Applying InputClass "evdev touchpad catchall"
[ 18340.533] (**) AlpsPS/2 ALPS DualPoint TouchPad: Applying InputClass "touchpad catchall"
[ 18340.533] (**) AlpsPS/2 ALPS DualPoint TouchPad: Applying InputClass "Default clickpad buttons"
[ 18340.533] (II) LoadModule: "synaptics"
[ 18340.533] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[ 18340.533] (II) Module synaptics: vendor="X.Org Foundation"
[ 18340.533] 	compiled for 1.12.99.905, module version = 1.6.2
[ 18340.533] 	Module class: X.Org XInput Driver
[ 18340.533] 	ABI class: X.Org XInput driver, version 18.0
[ 18340.533] (II) Using input driver 'synaptics' for 'AlpsPS/2 ALPS DualPoint TouchPad'
[ 18340.533] (**) AlpsPS/2 ALPS DualPoint TouchPad: always reports core events
[ 18340.533] (**) Option "Device" "/dev/input/event15"
[ 18340.540] (II) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: ignoring touch events for semi-multitouch device
[ 18340.540] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: x-axis range 0 - 2000
[ 18340.540] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: y-axis range 0 - 1400
[ 18340.540] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: pressure range 0 - 127
[ 18340.540] (II) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: device does not report finger width.
[ 18340.540] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: buttons: left right middle double triple
[ 18340.540] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: Vendor 0x2 Product 0x8
[ 18340.540] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: invalid finger width range.  defaulting to 0 - 15
[ 18340.540] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: touchpad found
[ 18340.540] (**) AlpsPS/2 ALPS DualPoint TouchPad: always reports core events
[ 18340.572] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input16/event15"
[ 18340.572] (II) XINPUT: Adding extended input device "AlpsPS/2 ALPS DualPoint TouchPad" (type: TOUCHPAD, id 15)
[ 18340.572] (**) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[ 18340.572] (**) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: MaxSpeed is now 1.75
[ 18340.572] (**) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: AccelFactor is now 0.082
[ 18340.573] (**) AlpsPS/2 ALPS DualPoint TouchPad: (accel) keeping acceleration scheme 1
[ 18340.573] (**) AlpsPS/2 ALPS DualPoint TouchPad: (accel) acceleration profile 1
[ 18340.573] (**) AlpsPS/2 ALPS DualPoint TouchPad: (accel) acceleration factor: 2.000
[ 18340.573] (**) AlpsPS/2 ALPS DualPoint TouchPad: (accel) acceleration threshold: 4
[ 18340.573] (    --) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: touchpad found
[ 18340.573] (II) config/udev: Adding input device AlpsPS/2 ALPS DualPoint TouchPad (/dev/input/mouse2)
[ 18340.573] (**) AlpsPS/2 ALPS DualPoint TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[ 18340.578] (II) config/udev: Adding input device Dell WMI hotkeys (/dev/input/event7)
[ 18340.578] (**) Dell WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[ 18340.578] (II) Using input driver 'evdev' for 'Dell WMI hotkeys'
[ 18340.578] (**) Dell WMI hotkeys: always reports core events
[ 18340.578] (**) evdev: Dell WMI hotkeys: Device: "/dev/input/event7"
[ 18340.578] (--) evdev: Dell WMI hotkeys: Vendor 0 Product 0
[ 18340.578] (--) evdev: Dell WMI hotkeys: Found keys
[ 18340.578] (II) evdev: Dell WMI hotkeys: Configuring as keyboard
[ 18340.578] (**) Option "config_info" "udev:/sys/devices/virtual/input/input8/event7"
[ 18340.579] (II) XINPUT: Adding extended input device "Dell WMI hotkeys" (type: KEYBOARD, id 16)
[ 18340.579] (**) Option "xkb_rules" "evdev"
[ 18340.579] (**) Option "xkb_model" "pc105"
[ 18340.579] (**) Option "xkb_layout" "br"
[ 18348.284] (EE) 
[ 18348.284] (EE) Backtrace:
[ 18348.304] (EE) 0: /usr/bin/X (xorg_backtrace+0x36) [0x7f00a2194b76]
[ 18348.304] (EE) 1: /usr/bin/X (0x7f00a1fec000+0x1ac9a9) [0x7f00a21989a9]
[ 18348.304] (EE) 2: /lib/x86_64-linux-gnu/libpthread.so.0 (0x7f00a1312000+0xfcb0) [0x7f00a1321cb0]
[ 18348.304] (EE) 3: /lib/x86_64-linux-gnu/libc.so.6 (0x7f009ff76000+0x14a3b4) [0x7f00a00c03b4]
[ 18348.304] (EE) 4: /usr/lib/xorg/modules/libexa.so (0x7f009df96000+0x584e) [0x7f009df9b84e]
[ 18348.304] (EE) 5: /usr/lib/xorg/modules/libexa.so (0x7f009df96000+0x5d03) [0x7f009df9bd03]
[ 18348.304] (EE) 6: /usr/lib/xorg/modules/libexa.so (0x7f009df96000+0x851a) [0x7f009df9e51a]
[ 18348.304] (EE) 7: /usr/lib/xorg/modules/libexa.so (0x7f009df96000+0x106bf) [0x7f009dfa66bf]
[ 18348.304] (EE) 8: /usr/lib/xorg/modules/libexa.so (0x7f009df96000+0x12098) [0x7f009dfa8098]
[ 18348.304] (EE) 9: /usr/lib/xorg/modules/libexa.so (0x7f009df96000+0xb56c) [0x7f009dfa156c]
[ 18348.305] (EE) 10: /usr/bin/X (0x7f00a1fec000+0x198ea3) [0x7f00a2184ea3]
[ 18348.305] (EE) 11: /usr/bin/X (0x7f00a1fec000+0xe2830) [0x7f00a20ce830]
[ 18348.305] (EE) 12: /usr/bin/X (0x7f00a1fec000+0x12adb8) [0x7f00a2116db8]
[ 18348.305] (EE) 13: /usr/bin/X (0x7f00a1fec000+0x55a91) [0x7f00a2041a91]
[ 18348.305] (EE) 14: /usr/bin/X (0x7f00a1fec000+0x4456a) [0x7f00a203056a]
[ 18348.305] (EE) 15: /lib/x86_64-linux-gnu/libc.so.6 (__libc_start_main+0xed) [0x7f009ff9776d]
[ 18348.305] (EE) 16: /usr/bin/X (0x7f00a1fec000+0x448ad) [0x7f00a20308ad]
[ 18348.305] (EE) 
[ 18348.305] (EE) Segmentation fault at address 0x50
[ 18348.306] 
Fatal server error:
[ 18348.306] Caught signal 11 (Segmentation fault). Server aborting
[ 18348.306] 
[ 18348.306] (EE) 
Please consult the The X.Org Foundation support 
	 at [http://wiki.x.org](http://wiki.x.org)
 for help. 
[ 18348.306] (EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[ 18348.306] (EE) 
[ 18348.328] (II) evdev: Power Button: Close
[ 18348.328] (II) UnloadModule: "evdev"
[ 18348.332] (II) evdev: Video Bus: Close
[ 18348.332] (II) UnloadModule: "evdev"
[ 18348.351] (II) evdev: Power Button: Close
[ 18348.351] (II) UnloadModule: "evdev"
[ 18348.364] (II) evdev: Sleep Button: Close
[ 18348.364] (II) UnloadModule: "evdev"
[ 18348.368] (II) evdev: Laptop_Integrated_Webcam_3M: Close
[ 18348.368] (II) UnloadModule: "evdev"
[ 18348.376] (II) evdev: LITEON Technology USB Keyboard: Close
[ 18348.376] (II) UnloadModule: "evdev"
[ 18348.396] (II) evdev: SIGMACHIP Usb Mouse: Close
[ 18348.396] (II) UnloadModule: "evdev"
[ 18348.412] (II) evdev: AT Translated Set 2 keyboard: Close
[ 18348.412] (II) UnloadModule: "evdev"
[ 18348.412] (II) evdev: DualPoint Stick: Close
[ 18348.412] (II) UnloadModule: "evdev"
[ 18348.416] (II) UnloadModule: "synaptics"
[ 18348.420] (II) evdev: Dell WMI hotkeys: Close
[ 18348.420] (II) UnloadModule: "evdev"
[ 18348.420] (II) AIGLX: Suspending AIGLX clients for VT switch
[ 18348.420] (II) NOUVEAU(0): NVLeaveVT is called.

[COLOR=#000000]
thanks in advance[/COLOR]

---

