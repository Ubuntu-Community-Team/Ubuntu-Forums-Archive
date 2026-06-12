---
title: "Started as display properties...now it's about the right driver"
date: 2007-11-18
forum: Multimedia &amp; Video
---

### Post by Joedude on 2007-11-18
It all started as a question about adjusting the diplay properties. I have an HP Pavilion mx70 monitor (which isn't listed in the system>admin>screens and graphics) and an ATI Radeon 8500 LE. One of them is going bad as my display over the l;ast couple of years has been "dark" and I have to use the control panel to increase brightness, alpha and contrast to view my screen properly...However, I can't find that here. Along the way, I have found that it's not even loading the right driver. I Installed the ati drivers through synaptic and the fglrx-control and the kernel source...but nothjing...I still get this.

It's time for me to put my hands up and admit I need help:

Appreciate any help in advance:

$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R200 20060602 AGP 4x x86/MMX+/3DNow!+/SSE TCL
OpenGL version string: 1.3 Mesa 7.0.1

Wrong....ATI Radeon 8500LE...and no matter what I do, I can't seem to change that...nor get a control panel to adjust the diplay properties...

$ fglrx-control
bash: fglrx-control: command not found

dang it...the package is installed, I checked in synaptic.

$ atigetsysteminfo.sh produced a long note with everything in my puter...and listed the same vid driver

```
ATI System configuration report started Sun Nov 18 09:56:36 GMT 2007 on zeus.

==========uname -a==========
Linux zeus 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux


==========/proc/version (09:56)==========
Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007


==========gcc --version==========
gcc (GCC) 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)
Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.


==========/usr/bin/fglrxinfo==========
libGL: XF86DRIGetClientDriverName: 5.3.0 r200 (screen 0)
libGL: OpenDriver: trying /usr/lib/dri/r200_dri.so
libGL error: dlopen /usr/lib/dri/r200_dri.so failed (/usr/lib/dri/r200_dri.so: undefined symbol: _glapi_add_dispatch)
libGL error: unable to find driver: r200_dri.so
libGL: XF86DRIGetClientDriverName: 5.3.0 r200 (screen 0)
libGL: OpenDriver: trying /usr/lib/dri/r200_dri.so
libGL error: dlopen /usr/lib/dri/r200_dri.so failed (/usr/lib/dri/r200_dri.so: undefined symbol: _glapi_add_dispatch)
libGL error: unable to find driver: r200_dri.so
display: :0.0  screen: 0
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R200 20060602 AGP 4x x86/MMX+/3DNow!+/SSE TCL
OpenGL version string: 1.3 Mesa 7.0.1


==========ldd /usr/bin/fglrxinfo==========
	linux-gate.so.1 =>  (0xffffe000)
	libGL.so.1 => /usr/lib/libGL.so.1 (0xb7eed000)
	libX11.so.6 => /usr/lib/libX11.so.6 (0xb7dfc000)
	libXext.so.6 => /usr/lib/libXext.so.6 (0xb7dee000)
	libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7ca4000)
	libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb7c8c000)
	libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7c88000)
	libXau.so.6 => /usr/lib/libXau.so.6 (0xb7c84000)
	libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0xb7c7f000)
	/lib/ld-linux.so.2 (0xb7fa1000)



==========ENVIRONMENT VARIABLES==========

$PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

$LD_LIBRARY_PATH=

$LD_CONFIG_PATH=

$LIBGL_DRIVERS_PATH=



==========PROC DEVICES==========


==========/proc/cpuinfo (09:56)==========
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 6
model		: 10
model name	: AMD Athlon(tm) XP 2800+
stepping	: 0
cpu MHz		: 2079.534
cache size	: 512 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow up ts
bogomips	: 4162.39
clflush size	: 32


==========/proc/meminfo (09:56)==========
MemTotal:      1295728 kB
MemFree:        127180 kB
Buffers:         19176 kB
Cached:         901000 kB
SwapCached:         28 kB
Active:         678932 kB
Inactive:       449152 kB
HighTotal:      393152 kB
HighFree:        13996 kB
LowTotal:       902576 kB
LowFree:        113184 kB
SwapTotal:     1044216 kB
SwapFree:      1009396 kB
Dirty:             196 kB
Writeback:           0 kB
AnonPages:      207880 kB
Mapped:          46304 kB
Slab:            19440 kB
SReclaimable:    10756 kB
SUnreclaim:       8684 kB
PageTables:       2016 kB
NFS_Unstable:        0 kB
Bounce:              0 kB
CommitLimit:   1692080 kB
Committed_AS:   534776 kB
VmallocTotal:   114680 kB
VmallocUsed:      7548 kB
VmallocChunk:   106484 kB


==========/usr/bin/lspci==========
00:00.0 Host bridge: nVidia Corporation nForce2 AGP (different version?) (rev c1)
00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev c1)
00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev c1)
00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev c1)
00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev c1)
00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev c1)
00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a4)
00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1)
00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3)
00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2)
00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev c1)
02:00.0 VGA compatible controller: ATI Technologies Inc Radeon R200 QL [Radeon 8500 LE]


==========/proc/pci ()==========
cat: /proc/pci: No such file or directory


==========/proc/dri/0/bufs (09:56)==========
 o     size count  free	 segs pages    kB

16    65536    32     0     0     0     0

 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0


==========/proc/dri/0/clients (09:56)==========
a dev	pid    uid	magic	  ioctls

y   0  5001     0          0     213074
y   0  5001     0          1         15


==========/proc/dri/0/mem (09:56)==========



==========/proc/dri/0/name (09:56)==========
radeon 0000:02:00.0 pci:0000:02:00.0


==========/proc/dri/0/queues (09:56)==========
  ctx/flags   use   fin   blk/rw/rwf  wait    flushed	   queued      locks


==========/proc/dri/0/vm (09:56)==========
slot	 offset	      size type flags	 address mtrr

   0 0xe0302000 0x004e0000  AGP  0x00 0xe0302000    2
   1 0xe0102000 0x00200000  AGP  0x00 0xe0102000    2
   2 0xe0101000 0x00001000  AGP  0x02 0xe0101000    2
   3 0xe0000000 0x00101000  AGP  0x02 0xe0000000    2
   4 0xf8bad000 0x00002000  SHM  0x20 0xf8bad000 none
   5 0xd0000000 0x08000000   FB  0x10 0xd0000000    3
   6 0xe5000000 0x00010000  REG  0x02 0xe5000000 none


==========/proc/dri/0/vma (09:56)==========
vma use count: 12, high_memory = f8000000, 0x38000000

 5001 0xa6722000-0xa6c02000 rw-s-i 0x000e0302000 pwubca-kl

 5001 0xa6c02000-0xa6e02000 rw-s-i 0x000e0102000 pwubca-kl

 5001 0xaee4b000-0xaee4c000 rw-s-i 0x000e0101000 pwubca-kl

 5001 0xb7a51000-0xb7a61000 rw-s-i 0x000e5000000 pwubua-kl

 5001 0xb7c8f000-0xb7c91000 rw-s-- 0x000f8bad000 pwubca-kl

 5001 0xa6e02000-0xaee02000 rw-s-i 0x000d0000000 pwubua-kl

 5001 0xaf0aa000-0xaf2aa000 rw-s-i 0x000e0102000 pwubca-kl

 5001 0xaf2aa000-0xaf78a000 rw-s-i 0x000e0302000 pwubca-kl

 5001 0xaf78a000-0xaf98a000 rw-s-i 0x000e0102000 pwubca-kl

 5001 0xb7c91000-0xb7c92000 rw-s-i 0x000e0101000 pwubca-kl

 5001 0xb7a61000-0xb7b62000 rw-s-i 0x000e0000000 pwubca-kl

 5001 0xb7f77000-0xb7f79000 rw-s-- 0x000f8bad000 pwubca-kl



==========X SERVER INFORMATION==========


==========/etc/X11/xorg.conf ()==========
cat: /etc/X11/xorg.conf: No such file or directory


==========/var/log/Xorg.0.log (08:53)==========

X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8)
Current Operating System: Linux zeus 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686
Build Date: 29 September 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Nov 18 03:16:20 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "MX70"
(**) |   |-->Device "ATI Technologies Inc Radeon R200 QL [Radeon 8500 LE]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(WW) Including the default font path /usr/share/fonts/X11/misc,/usr/share/fonts/X11/cyrillic,/usr/share/fonts/X11/100dpi/:unscaled,/usr/share/fonts/X11/75dpi/:unscaled,/usr/share/fonts/X11/Type1,/usr/share/fonts/X11/100dpi,/usr/share/fonts/X11/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType.
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/cyrillic,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81ea440
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.2
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 10de,01e0 card 147b,1c02 rev c1 class 06,00,00 hdr 80
(II) PCI: 00:00:1: chip 10de,01eb card 10de,0c17 rev c1 class 05,00,00 hdr 80
(II) PCI: 00:00:2: chip 10de,01ee card 10de,0c17 rev c1 class 05,00,00 hdr 80
(II) PCI: 00:00:3: chip 10de,01ed card 10de,0c17 rev c1 class 05,00,00 hdr 80
(II) PCI: 00:00:4: chip 10de,01ec card 10de,0c17 rev c1 class 05,00,00 hdr 80
(II) PCI: 00:00:5: chip 10de,01ef card 10de,0c17 rev c1 class 05,00,00 hdr 80
(II) PCI: 00:01:0: chip 10de,0060 card 147b,1c02 rev a4 class 06,01,00 hdr 80
(II) PCI: 00:01:1: chip 10de,0064 card 147b,1c02 rev a2 class 0c,05,00 hdr 80
(II) PCI: 00:02:0: chip 10de,0067 card 147b,1c02 rev a4 class 0c,03,10 hdr 80
(II) PCI: 00:02:1: chip 10de,0067 card 147b,1c02 rev a4 class 0c,03,10 hdr 80
(II) PCI: 00:02:2: chip 10de,0068 card 147b,1c02 rev a4 class 0c,03,20 hdr 80
(II) PCI: 00:04:0: chip 10de,0066 card 147b,1c02 rev a1 class 02,00,00 hdr 00
(II) PCI: 00:06:0: chip 10de,006a card 147b,1c02 rev a1 class 04,01,00 hdr 00
(II) PCI: 00:08:0: chip 10de,006c card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:09:0: chip 10de,0065 card 147b,1c02 rev a2 class 01,01,8a hdr 00
(II) PCI: 00:1e:0: chip 10de,01e8 card 0000,0000 rev c1 class 06,04,00 hdr 01
(II) PCI: 02:00:0: chip 1002,514c card 1002,003a rev 00 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:1:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:8:0), (0,1,1), BCTRL: 0x0202 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,2), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000c000 - 0x0000cfff (0x1000) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xe4000000 - 0xe5ffffff (0x2000000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
(--) PCI:*(2:0:0) ATI Technologies Inc Radeon R200 QL [Radeon 8500 LE] rev 0, Mem @ 0xd0000000/28, 0xe5000000/16, I/O @ 0xc000/8
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xe0000000 from 0xe3ffffff to 0xdfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xe6002000 - 0xe6002fff (0x1000) MX[B]
	[1] -1	0	0xe6001000 - 0xe6001fff (0x1000) MX[B]
	[2] -1	0	0xe6000000 - 0xe60000ff (0x100) MX[B]
	[3] -1	0	0xe6005000 - 0xe6005fff (0x1000) MX[B]
	[4] -1	0	0xe6004000 - 0xe6004fff (0x1000) MX[B]
	[5] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[6] -1	0	0xe5000000 - 0xe500ffff (0x10000) MX[B](B)
	[7] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[8] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[9] -1	0	0x0000d800 - 0x0000d87f (0x80) IX[B]
	[10] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[11] -1	0	0x0000d000 - 0x0000d007 (0x8) IX[B]
	[12] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[13] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xe6002000 - 0xe6002fff (0x1000) MX[B]
	[1] -1	0	0xe6001000 - 0xe6001fff (0x1000) MX[B]
	[2] -1	0	0xe6000000 - 0xe60000ff (0x100) MX[B]
	[3] -1	0	0xe6005000 - 0xe6005fff (0x1000) MX[B]
	[4] -1	0	0xe6004000 - 0xe6004fff (0x1000) MX[B]
	[5] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[6] -1	0	0xe5000000 - 0xe500ffff (0x10000) MX[B](B)
	[7] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[8] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[9] -1	0	0x0000d800 - 0x0000d87f (0x80) IX[B]
	[10] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[11] -1	0	0x0000d000 - 0x0000d007 (0x8) IX[B]
	[12] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[13] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe6002000 - 0xe6002fff (0x1000) MX[B]
	[5] -1	0	0xe6001000 - 0xe6001fff (0x1000) MX[B]
	[6] -1	0	0xe6000000 - 0xe60000ff (0x100) MX[B]
	[7] -1	0	0xe6005000 - 0xe6005fff (0x1000) MX[B]
	[8] -1	0	0xe6004000 - 0xe6004fff (0x1000) MX[B]
	[9] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[10] -1	0	0xe5000000 - 0xe500ffff (0x10000) MX[B](B)
	[11] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[12] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[13] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[14] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[15] -1	0	0x0000d800 - 0x0000d87f (0x80) IX[B]
	[16] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[17] -1	0	0x0000d000 - 0x0000d007 (0x8) IX[B]
	[18] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[19] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
(II) LoadModule: "i2c"(II) Module already built-in
(II) LoadModule: "ddc"(II) Module already built-in
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.3.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.2
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "ati"
(II) Loading /usr/lib/xorg/modules/drivers//ati_drv.so
(II) Module ati: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 6.7.195
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.2
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) Wacom driver level: 47-0.7.7-7 $
(II) ATI: ATI driver wrapper (version 6.7.195) for chipsets: mach64, rage128, radeon
(II) Primary Device is: PCI 02:00:0
(II) Loading sub module "radeon"
(II) LoadModule: "radeon"
(II) Loading /usr/lib/xorg/modules/drivers//radeon_drv.so
(II) Module radeon: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 4.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.2
(II) RADEON: Driver for ATI Radeon chipsets: ATI Radeon QD (AGP),
	ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
	ATI Radeon VE/7000 QY (AGP/PCI), ATI Radeon VE/7000 QZ (AGP/PCI),
	ATI ES1000 515E (PCI), ATI ES1000 5969 (PCI),
	ATI Radeon Mobility M7 LW (AGP),
	ATI Mobility FireGL 7800 M7 LX (AGP),
	ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
	ATI Radeon IGP320 (A3) 4136, ATI Radeon IGP320M (U1) 4336,
	ATI Radeon IGP330/340/350 (A4) 4137,
	ATI Radeon IGP330M/340M/350M (U2) 4337,
	ATI Radeon 7000 IGP (A4+) 4237, ATI Radeon Mobility 7000 IGP 4437,
	ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
	ATI Radeon 9100 QM (AGP), ATI Radeon 8500 AIW BB (AGP),
	ATI Radeon 8500 AIW BC (AGP), ATI Radeon 7500 QW (AGP/PCI),
	ATI Radeon 7500 QX (AGP/PCI), ATI Radeon 9000/PRO If (AGP/PCI),
	ATI Radeon 9000 Ig (AGP/PCI), ATI FireGL Mobility 9000 (M9) Ld (AGP),
	ATI Radeon Mobility 9000 (M9) Lf (AGP),
	ATI Radeon Mobility 9000 (M9) Lg (AGP),
	ATI Radeon 9100 IGP (A5) 5834,
	ATI Radeon Mobility 9100 IGP (U3) 5835, ATI Radeon 9100 PRO IGP 7834,
	ATI Radeon Mobility 9200 IGP 7835, ATI Radeon 9250 5960 (AGP),
	ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
	ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
	ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
	ATI Radeon Mobility 9200 (M9+) 5C63 (AGP), ATI Radeon 9500 AD (AGP),
	ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
	ATI FireGL Z1 AG (AGP), ATI Radeon 9700 Pro ND (AGP),
	ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9600TX NF (AGP),
	ATI FireGL X1 NG (AGP), ATI Radeon 9600 AP (AGP),
	ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
	ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP),
	ATI FireGL RV360 AV (AGP),
	ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
	ATI Radeon Mobility 9600 (M10) NQ (AGP),
	ATI Radeon Mobility 9600 (M11) NR (AGP),
	ATI Radeon Mobility 9600 (M10) NS (AGP),
	ATI FireGL Mobility T2 (M10) NT (AGP),
	ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon 9650,
	ATI Radeon 9800SE AH (AGP), ATI Radeon 9800 AI (AGP),
	ATI Radeon 9800 AJ (AGP), ATI FireGL X2 AK (AGP),
	ATI Radeon 9800PRO NH (AGP), ATI Radeon 9800 NI (AGP),
	ATI FireGL X2 NK (AGP), ATI Radeon 9800XT NJ (AGP),
	ATI Radeon X600 (RV380) 3E50 (PCIE),
	ATI FireGL V3200 (RV380) 3E54 (PCIE),
	ATI Radeon Mobility X600 (M24) 3150 (PCIE),
	ATI Radeon Mobility X300 (M24) 3152 (PCIE),
	ATI FireGL M24 GL 3154 (PCIE), ATI Radeon X300 (RV370) 5B60 (PCIE),
	ATI Radeon X600 (RV370) 5B62 (PCIE),
	ATI Radeon X550 (RV370) 5B63 (PCIE),
	ATI FireGL V3100 (RV370) 5B64 (PCIE),
	ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
	ATI Radeon Mobility X300 (M22) 5460 (PCIE),
	ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
	ATI FireGL M22 GL 5464 (PCIE), ATI Radeon XPRESS 200 5A41 (PCIE),
	ATI Radeon XPRESS 200M 5A42 (PCIE),
	ATI Radeon XPRESS 200 5A61 (PCIE),
	ATI Radeon XPRESS 200M 5A62 (PCIE),
	ATI Radeon XPRESS 200 5954 (PCIE),
	ATI Radeon XPRESS 200M 5955 (PCIE),
	ATI Radeon XPRESS 200 5974 (PCIE),
	ATI Radeon XPRESS 200M 5975 (PCIE), ATI FireGL V5000 (RV410) (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility Radeon X700 XL (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Radeon X700 PRO (RV410) (PCIE),
	ATI Radeon X700 XT (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 SE (RV410) (PCIE),
	ATI Radeon X800 (R420) JH (AGP), ATI Radeon X800PRO (R420) JI (AGP),
	ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
	ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
	ATI Radeon Mobility 9800 (M18) JN (AGP),
	ATI Radeon X800XT (R420) JP (AGP), ATI Radeon X800 SE (R420) (AGP),
	ATI Radeon AIW X800 VE (R420) JT (AGP),
	ATI Radeon X800 (R423) UH (PCIE),
	ATI Radeon X800PRO (R423) UI (PCIE),
	ATI Radeon X800LE (R423) UJ (PCIE),
	ATI Radeon X800SE (R423) UK (PCIE),
	ATI FireGL V5100 (R423) UQ (PCIE),
	ATI FireGL unknown (R423) UR (PCIE),
	ATI FireGL unknown (R423) UT (PCIE),
	ATI Radeon X800XT (R423) 5D57 (PCIE), ATI FireGL V7100 (R423) (PCIE),
	ATI Mobility FireGL V5100 (M28) (PCIE),
	ATI Mobility Radeon X800 (M28) (PCIE),
	ATI Mobility Radeon X800 XT (M28) (PCIE),
	ATI Radeon X800 (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
	ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 XTP (R430) (PCIE),
	ATI Radeon X850 5D4C (PCIE),
	ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
	ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
	ATI Radeon X850 XT (R480) (PCIE),
	ATI Radeon X850 XT PE (R480) (PCIE),
	ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
	ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP)
(--) Chipset ATI Radeon 8500 QL (AGP) found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe6002000 - 0xe6002fff (0x1000) MX[B]
	[5] -1	0	0xe6001000 - 0xe6001fff (0x1000) MX[B]
	[6] -1	0	0xe6000000 - 0xe60000ff (0x100) MX[B]
	[7] -1	0	0xe6005000 - 0xe6005fff (0x1000) MX[B]
	[8] -1	0	0xe6004000 - 0xe6004fff (0x1000) MX[B]
	[9] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[10] -1	0	0xe5000000 - 0xe500ffff (0x10000) MX[B](B)
	[11] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[12] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[13] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[14] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[15] -1	0	0x0000d800 - 0x0000d87f (0x80) IX[B]
	[16] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[17] -1	0	0x0000d000 - 0x0000d007 (0x8) IX[B]
	[18] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[19] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe6002000 - 0xe6002fff (0x1000) MX[B]
	[5] -1	0	0xe6001000 - 0xe6001fff (0x1000) MX[B]
	[6] -1	0	0xe6000000 - 0xe60000ff (0x100) MX[B]
	[7] -1	0	0xe6005000 - 0xe6005fff (0x1000) MX[B]
	[8] -1	0	0xe6004000 - 0xe6004fff (0x1000) MX[B]
	[9] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[10] -1	0	0xe5000000 - 0xe500ffff (0x10000) MX[B](B)
	[11] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[12] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[13] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[14] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[18] -1	0	0x0000d800 - 0x0000d87f (0x80) IX[B]
	[19] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[20] -1	0	0x0000d000 - 0x0000d007 (0x8) IX[B]
	[21] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[22] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
	[23] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[24] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) RADEON(0): MMIO registers at 0xe5000000: size 64KB
(II) RADEON(0): PCI bus 2 card 0 func 0
(**) RADEON(0): Depth 24, (--) framebuffer bpp 32
(II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) RADEON(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.2
(II) RADEON(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) RADEON(0): RGB weight 888
(II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) RADEON(0): initializing int10
(II) RADEON(0): Primary V_BIOS segment is: 0xc000
(--) RADEON(0): Chipset: "ATI Radeon 8500 QL (AGP)" (ChipID = 0x514c)
(--) RADEON(0): Linear framebuffer at 0xd0000000
(II) RADEON(0): AGP card detected
(II) RADEON(0): Legacy BIOS detected
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: Searching for BusID pci:0000:02:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports pci:0000:02:00.0
(II) RADEON(0): [dri] Found DRI library version 1.3.0 and kernel module version 1.27.0
(==) RADEON(0): Page Flipping disabled
(II) RADEON(0): Will try to use DMA for Xv image transfers
(II) RADEON(0): Detected total video RAM=131072K, accessible=131072K (PCI BAR=262144K)
(--) RADEON(0): Mapped VideoRAM: 131072 kByte (128 bit DDR SDRAM)
(II) RADEON(0): Color tiling enabled by default
(II) RADEON(0): Max desktop size set to 2048x1200
(II) RADEON(0): For a larger or smaller max desktop size, add a Virtual line to your xorg.conf
(II) RADEON(0): If you are having trouble with 3D, reduce the desktop size by adjusting the Virtual line to your xorg.conf
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"(II) Module already built-in
(II) RADEON(0): PLL parameters: rf=2700 rd=12 min=20000 max=35000; xclk=25000
(II) RADEON(0): Bios Connector table: 
(II) RADEON(0): Port0: DDCType-3, DACType-0, TMDSType-0, ConnectorType-2
(II) RADEON(0): Output VGA-0 using monitor section MX70
(II) RADEON(0): I2C bus "VGA_DDC" initialized.
(II) RADEON(0): Port0:
 Monitor   -- AUTO
 Connector -- VGA
 DAC Type  -- Primary
 TMDS Type -- None
 DDC Type  -- VGA_DDC
(II) RADEON(0): I2C device "VGA_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" removed.
(II) RADEON(0): DDC Type: 3, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on connector: VGA ----------------------
(II) RADEON(0): Manufacturer: HWP  Model: 503  Serial#: 5389
(II) RADEON(0): Year: 2001  Week: 37
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 32  vert.: 24
(II) RADEON(0): Gamma: 2.83
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.632 redY: 0.330   greenX: 0.273 greenY: 0.605
(II) RADEON(0): blueX: 0.142 blueY: 0.061   whiteX: 0.281 whiteY: 0.311
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEON(0): #1: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEON(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEON(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 94.5 MHz   Image Size:  320 x 240 mm
(II) RADEON(0): h_active: 1024  h_sync: 1072  h_sync_end 1168 h_blank_end 1376 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 808 v_border: 0
(II) RADEON(0): Serial No: THLDK05389
(II) RADEON(0): Monitor name: MX70
(II) RADEON(0): Ranges: V min: 50  V max: 120 Hz, H min: 30  H max: 70 kHz, PixClock max 110 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0022f003050d150000
(II) RADEON(0): 	250b0103682018b7eae062a154469b24
(II) RADEON(0): 	0f484fa44a0031594559615981800101
(II) RADEON(0): 	010101010101ea240060410028303060
(II) RADEON(0): 	130040f01000001e000000ff0054484c
(II) RADEON(0): 	444b30353338390a2020000000fc004d
(II) RADEON(0): 	5837300a2020202020202020000000fd
(II) RADEON(0): 	0032781e460b000a20202020202000d7
finished output detect: 0
finished all detect
before xf86InitialConfiguration
(II) RADEON(0): I2C device "VGA_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" removed.
(II) RADEON(0): DDC Type: 3, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on connector: VGA ----------------------
(II) RADEON(0): Manufacturer: HWP  Model: 503  Serial#: 5389
(II) RADEON(0): Year: 2001  Week: 37
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 32  vert.: 24
(II) RADEON(0): Gamma: 2.83
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.632 redY: 0.330   greenX: 0.273 greenY: 0.605
(II) RADEON(0): blueX: 0.142 blueY: 0.061   whiteX: 0.281 whiteY: 0.311
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEON(0): #1: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEON(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEON(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 94.5 MHz   Image Size:  320 x 240 mm
(II) RADEON(0): h_active: 1024  h_sync: 1072  h_sync_end 1168 h_blank_end 1376 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 808 v_border: 0
(II) RADEON(0): Serial No: THLDK05389
(II) RADEON(0): Monitor name: MX70
(II) RADEON(0): Ranges: V min: 50  V max: 120 Hz, H min: 30  H max: 70 kHz, PixClock max 110 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0022f003050d150000
(II) RADEON(0): 	250b0103682018b7eae062a154469b24
(II) RADEON(0): 	0f484fa44a0031594559615981800101
(II) RADEON(0): 	010101010101ea240060410028303060
(II) RADEON(0): 	130040f01000001e000000ff0054484c
(II) RADEON(0): 	444b30353338390a2020000000fc004d
(II) RADEON(0): 	5837300a2020202020202020000000fd
(II) RADEON(0): 	0032781e460b000a20202020202000d7
(II) RADEON(0): Output VGA-0 connected
in RADEONProbeOutputModes
(II) RADEON(0): I2C device "VGA_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" removed.
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): Manufacturer: HWP  Model: 503  Serial#: 5389
(II) RADEON(0): Year: 2001  Week: 37
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 32  vert.: 24
(II) RADEON(0): Gamma: 2.83
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.632 redY: 0.330   greenX: 0.273 greenY: 0.605
(II) RADEON(0): blueX: 0.142 blueY: 0.061   whiteX: 0.281 whiteY: 0.311
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEON(0): #1: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEON(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEON(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 94.5 MHz   Image Size:  320 x 240 mm
(II) RADEON(0): h_active: 1024  h_sync: 1072  h_sync_end 1168 h_blank_end 1376 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 808 v_border: 0
(II) RADEON(0): Serial No: THLDK05389
(II) RADEON(0): Monitor name: MX70
(II) RADEON(0): Ranges: V min: 50  V max: 120 Hz, H min: 30  H max: 70 kHz, PixClock max 110 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0022f003050d150000
(II) RADEON(0): 	250b0103682018b7eae062a154469b24
(II) RADEON(0): 	0f484fa44a0031594559615981800101
(II) RADEON(0): 	010101010101ea240060410028303060
(II) RADEON(0): 	130040f01000001e000000ff0054484c
(II) RADEON(0): 	444b30353338390a2020000000fc004d
(II) RADEON(0): 	5837300a2020202020202020000000fd
(II) RADEON(0): 	0032781e460b000a20202020202000d7
(II) RADEON(0): Using EDID range info for horizontal sync
(II) RADEON(0): Using EDID range info for vertical refresh
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(II) RADEON(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(II) RADEON(0): Modeline "720x400"   28.32  720 738 846 900  400 412 414 449 -hsync +vsync
(II) RADEON(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(II) RADEON(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) RADEON(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(II) RADEON(0): Modeline "640x480"   35.00  640 664 728 816  480 483 487 507 -hsync +vsync
(II) RADEON(0): Modeline "800x600"   56.75  800 848 928 1056  600 603 607 633 -hsync +vsync
(II) RADEON(0): Modeline "1024x768"   94.50  1024 1096 1200 1376  768 771 775 809 -hsync +vsync
(II) RADEON(0): Modeline "1280x1024"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
(II) RADEON(0): Modeline "1024x768"   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync
(II) RADEON(0): EDID vendor "HWP", prod id 1283
(II) RADEON(0): Not using default mode "640x350" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x400" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "720x400" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x960" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x960" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "832x624" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x800" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1152x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1440x900" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1024" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1920x1200" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1920x1200" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Printing probed modes for output VGA-0
(II) RADEON(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) RADEON(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) RADEON(0): Modeline "1024x768"x84.9   94.50  1024 1096 1200 1376  768 771 775 809 -hsync +vsync (68.7 kHz)
(II) RADEON(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x84.9   56.75  800 848 928 1056  600 603 607 633 -hsync +vsync (53.7 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "640x480"x84.6   35.00  640 664 728 816  480 483 487 507 -hsync +vsync (42.9 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Output VGA-0 connected
(II) RADEON(0): Output VGA-0 using initial mode 1024x768
after xf86InitialConfiguration
(**) RADEON(0): Display dimensions: (320, 240) mm
(**) RADEON(0): DPI set to (101, 126)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(==) RADEON(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module already built-in
(==) RADEON(0): Using XAA acceleration architecture
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.2
(==) RADEON(0): Assuming overlay scaler buffer width is 1920
(II) RADEON(0): No MM_TABLE found - assuming CARD is not TV-in capable.
(!!) RADEON(0): For information on using the multimedia capabilities
	of this adapter, please see http://gatos.sf.net.
(!!) RADEON(0): MergedFB support has been removed and replaced with xrandr 1.2 support
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xe5000000 - 0xe500ffff (0x10000) MX[B]
	[1] 0	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xe6002000 - 0xe6002fff (0x1000) MX[B]
	[7] -1	0	0xe6001000 - 0xe6001fff (0x1000) MX[B]
	[8] -1	0	0xe6000000 - 0xe60000ff (0x100) MX[B]
	[9] -1	0	0xe6005000 - 0xe6005fff (0x1000) MX[B]
	[10] -1	0	0xe6004000 - 0xe6004fff (0x1000) MX[B]
	[11] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[12] -1	0	0xe5000000 - 0xe500ffff (0x10000) MX[B](B)
	[13] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[14] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[15] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[16] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[17] 0	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[21] -1	0	0x0000d800 - 0x0000d87f (0x80) IX[B]
	[22] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[23] -1	0	0x0000d000 - 0x0000d007 (0x8) IX[B]
	[24] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[25] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
	[26] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[27] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(==) RADEON(0): Write-combining range (0xd0000000,0x8000000)
(==) RADEON(0): Using 24 bit depth buffer
(II) RADEON(0): RADEONInitMemoryMap() : 
(II) RADEON(0):   mem_size         : 0x08000000
(II) RADEON(0):   MC_FB_LOCATION   : 0xd7ffd000
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(II) RADEON(0): Depth moves disabled by default
(II) RADEON(0): CP in BM mode
(II) RADEON(0): Using 8 MB GART aperture
(II) RADEON(0): Using 1 MB for the ring buffer
(II) RADEON(0): Using 2 MB for vertex/indirect buffers
(II) RADEON(0): Using 5 MB for GART textures
(II) RADEON(0): Memory manager initialized to (0,0) (1280,8191)
(II) RADEON(0): Reserved area from (0,1200) to (1280,1202)
(II) RADEON(0): Largest offscreen area available: 1280 x 6989
(II) RADEON(0): Will use front buffer at offset 0x0
(II) RADEON(0): Will use back buffer at offset 0x1838000
(II) RADEON(0): Will use depth buffer at offset 0x1e14000
(II) RADEON(0): Will use 94208 kb for textures at offset 0x23f0000
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID pci:0000:02:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports pci:0000:02:00.0
(II) RADEON(0): [drm] DRM interface version 1.3
(II) RADEON(0): [drm] created "radeon" driver at busid "pci:0000:02:00.0"
(II) RADEON(0): [drm] added 8192 byte SAREA at 0xf8bad000
(II) RADEON(0): [drm] mapped SAREA 0xf8bad000 to 0xb7f77000
(II) RADEON(0): [drm] framebuffer handle = 0xd0000000
(II) RADEON(0): [drm] added 1 reserved context for kernel
(==) RADEON(0): Using AGP 4x
(II) RADEON(0): [agp] Mode 0x1f000207 [AGP 0x10de/0x01e0; Card 0x1002/0x514c]
(II) RADEON(0): [agp] 8192 kB allocated with handle 0x00000001
(II) RADEON(0): [agp] ring handle = 0xe0000000
(II) RADEON(0): [agp] Ring mapped at 0xb7a61000
(II) RADEON(0): [agp] ring read ptr handle = 0xe0101000
(II) RADEON(0): [agp] Ring read ptr mapped at 0xb7c91000
(II) RADEON(0): [agp] vertex/indirect buffers handle = 0xe0102000
(II) RADEON(0): [agp] Vertex/indirect buffers mapped at 0xaf78a000
(II) RADEON(0): [agp] GART texture map handle = 0xe0302000
(II) RADEON(0): [agp] GART Texture map mapped at 0xaf2aa000
(II) RADEON(0): [drm] register handle = 0xe5000000
(II) RADEON(0): [dri] Visual configs initialized
init memmap
init common
init crtc1
init pll1
restore memmap
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0xd7ffd000
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
restore common
restore crtc1
restore pll1
finished PLL1
restore dac
enable montype: 1
(WW) RADEON(0): No crtc mode list for crtc 1,continuing with desired mode
disable montype: 1
(==) RADEON(0): Backing store disabled
(II) RADEON(0): X context handle = 0x1
(II) RADEON(0): [drm] installed DRM signal handler
(II) RADEON(0): [DRI] installation complete
(II) RADEON(0): [drm] Added 32 65536 byte vertex/indirect buffers
(II) RADEON(0): [drm] Mapped 32 vertex/indirect buffers
(II) RADEON(0): [drm] dma control initialized, using IRQ 19
(II) RADEON(0): [drm] Initialized kernel GART heap manager, 5111808
(WW) RADEON(0): DRI init changed memory map, adjusting ...
(WW) RADEON(0):   MC_FB_LOCATION  was: 0xd7ffd000 is: 0xd7ffd000
(WW) RADEON(0):   MC_AGP_LOCATION was: 0xffffffc0 is: 0xe07fe000
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0xd7ffd000
(II) RADEON(0):   MC_AGP_LOCATION  : 0xe07fe000
(II) RADEON(0): Direct rendering enabled
(II) RADEON(0): Render acceleration enabled
(II) RADEON(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Lines
	Scanline Image Writes
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(II) RADEON(0): Acceleration enabled
(**) Option "dpms"
(**) RADEON(0): DPMS enabled
(==) RADEON(0): Silken mouse enabled
(II) RADEON(0): Using hardware cursor (scanline 1202)
(II) RADEON(0): Largest offscreen area available: 1280 x 6985
(II) RADEON(0): No video input capabilities detected and no information is provided - disabling multimedia i2c
(II) Loading sub module "theatre_detect"
(II) LoadModule: "theatre_detect"
(II) Loading /usr/lib/xorg/modules/multimedia//theatre_detect_drv.so
(II) Module theatre_detect: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(II) RADEON(0): no multimedia table present, disabling Rage Theatre.
(II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(--) RandR disabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID pci:0000:02:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:02:00.0
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32
(II) AIGLX: Loaded and initialized /usr/lib/dri/r200_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) RADEON(0): Setting screen physical size to 320 x 240
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/input/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/input/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/input/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
enable montype: 1
(II) RADEON(0): I2C device "VGA_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" removed.
(II) RADEON(0): DDC Type: 3, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on connector: VGA ----------------------
(II) RADEON(0): Manufacturer: HWP  Model: 503  Serial#: 5389
(II) RADEON(0): Year: 2001  Week: 37
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 32  vert.: 24
(II) RADEON(0): Gamma: 2.83
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.632 redY: 0.330   greenX: 0.273 greenY: 0.605
(II) RADEON(0): blueX: 0.142 blueY: 0.061   whiteX: 0.281 whiteY: 0.311
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEON(0): #1: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEON(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEON(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 94.5 MHz   Image Size:  320 x 240 mm
(II) RADEON(0): h_active: 1024  h_sync: 1072  h_sync_end 1168 h_blank_end 1376 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 808 v_border: 0
(II) RADEON(0): Serial No: THLDK05389
(II) RADEON(0): Monitor name: MX70
(II) RADEON(0): Ranges: V min: 50  V max: 120 Hz, H min: 30  H max: 70 kHz, PixClock max 110 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0022f003050d150000
(II) RADEON(0): 	250b0103682018b7eae062a154469b24
(II) RADEON(0): 	0f484fa44a0031594559615981800101
(II) RADEON(0): 	010101010101ea240060410028303060
(II) RADEON(0): 	130040f01000001e000000ff0054484c
(II) RADEON(0): 	444b30353338390a2020000000fc004d
(II) RADEON(0): 	5837300a2020202020202020000000fd
(II) RADEON(0): 	0032781e460b000a20202020202000d7
(II) RADEON(0): Output VGA-0 connected
in RADEONProbeOutputModes
(II) RADEON(0): I2C device "VGA_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" removed.
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): Manufacturer: HWP  Model: 503  Serial#: 5389
(II) RADEON(0): Year: 2001  Week: 37
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 32  vert.: 24
(II) RADEON(0): Gamma: 2.83
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.632 redY: 0.330   greenX: 0.273 greenY: 0.605
(II) RADEON(0): blueX: 0.142 blueY: 0.061   whiteX: 0.281 whiteY: 0.311
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEON(0): #1: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEON(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEON(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 94.5 MHz   Image Size:  320 x 240 mm
(II) RADEON(0): h_active: 1024  h_sync: 1072  h_sync_end 1168 h_blank_end 1376 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 808 v_border: 0
(II) RADEON(0): Serial No: THLDK05389
(II) RADEON(0): Monitor name: MX70
(II) RADEON(0): Ranges: V min: 50  V max: 120 Hz, H min: 30  H max: 70 kHz, PixClock max 110 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0022f003050d150000
(II) RADEON(0): 	250b0103682018b7eae062a154469b24
(II) RADEON(0): 	0f484fa44a0031594559615981800101
(II) RADEON(0): 	010101010101ea240060410028303060
(II) RADEON(0): 	130040f01000001e000000ff0054484c
(II) RADEON(0): 	444b30353338390a2020000000fc004d
(II) RADEON(0): 	5837300a2020202020202020000000fd
(II) RADEON(0): 	0032781e460b000a20202020202000d7
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(II) RADEON(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(II) RADEON(0): Modeline "720x400"   28.32  720 738 846 900  400 412 414 449 -hsync +vsync
(II) RADEON(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(II) RADEON(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) RADEON(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(II) RADEON(0): Modeline "640x480"   35.00  640 664 728 816  480 483 487 507 -hsync +vsync
(II) RADEON(0): Modeline "800x600"   56.75  800 848 928 1056  600 603 607 633 -hsync +vsync
(II) RADEON(0): Modeline "1024x768"   94.50  1024 1096 1200 1376  768 771 775 809 -hsync +vsync
(II) RADEON(0): Modeline "1280x1024"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
(II) RADEON(0): Modeline "1024x768"   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync
(II) RADEON(0): EDID vendor "HWP", prod id 1283
(II) RADEON(0): Not using default mode "640x350" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x400" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "720x400" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x960" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x960" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "832x624" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x800" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1152x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1440x900" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1024" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Printing probed modes for output VGA-0
(II) RADEON(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) RADEON(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) RADEON(0): Modeline "1024x768"x84.9   94.50  1024 1096 1200 1376  768 771 775 809 -hsync +vsync (68.7 kHz)
(II) RADEON(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x84.9   56.75  800 848 928 1056  600 603 607 633 -hsync +vsync (53.7 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "640x480"x84.6   35.00  640 664 728 816  480 483 487 507 -hsync +vsync (42.9 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
disable montype: 1
enable montype: 1
disable montype: 1
enable montype: 1
disable montype: 1
enable montype: 1
disable montype: 1
enable montype: 1
enable montype: 1
disable montype: 1
enable montype: 1
disable montype: 1
enable montype: 1
enable montype: 1
(II) RADEON(0): I2C device "VGA_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" removed.
(II) RADEON(0): DDC Type: 3, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on connector: VGA ----------------------
(II) RADEON(0): Manufacturer: HWP  Model: 503  Serial#: 5389
(II) RADEON(0): Year: 2001  Week: 37
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 32  vert.: 24
(II) RADEON(0): Gamma: 2.83
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.632 redY: 0.330   greenX: 0.273 greenY: 0.605
(II) RADEON(0): blueX: 0.142 blueY: 0.061   whiteX: 0.281 whiteY: 0.311
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEON(0): #1: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEON(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEON(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 94.5 MHz   Image Size:  320 x 240 mm
(II) RADEON(0): h_active: 1024  h_sync: 1072  h_sync_end 1168 h_blank_end 1376 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 808 v_border: 0
(II) RADEON(0): Serial No: THLDK05389
(II) RADEON(0): Monitor name: MX70
(II) RADEON(0): Ranges: V min: 50  V max: 120 Hz, H min: 30  H max: 70 kHz, PixClock max 110 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0022f003050d150000
(II) RADEON(0): 	250b0103682018b7eae062a154469b24
(II) RADEON(0): 	0f484fa44a0031594559615981800101
(II) RADEON(0): 	010101010101ea240060410028303060
(II) RADEON(0): 	130040f01000001e000000ff0054484c
(II) RADEON(0): 	444b30353338390a2020000000fc004d
(II) RADEON(0): 	5837300a2020202020202020000000fd
(II) RADEON(0): 	0032781e460b000a20202020202000d7
(II) RADEON(0): Output VGA-0 connected
in RADEONProbeOutputModes
(II) RADEON(0): I2C device "VGA_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" removed.
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): Manufacturer: HWP  Model: 503  Serial#: 5389
(II) RADEON(0): Year: 2001  Week: 37
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 32  vert.: 24
(II) RADEON(0): Gamma: 2.83
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.632 redY: 0.330   greenX: 0.273 greenY: 0.605
(II) RADEON(0): blueX: 0.142 blueY: 0.061   whiteX: 0.281 whiteY: 0.311
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEON(0): #1: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEON(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEON(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 94.5 MHz   Image Size:  320 x 240 mm
(II) RADEON(0): h_active: 1024  h_sync: 1072  h_sync_end 1168 h_blank_end 1376 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 808 v_border: 0
(II) RADEON(0): Serial No: THLDK05389
(II) RADEON(0): Monitor name: MX70
(II) RADEON(0): Ranges: V min: 50  V max: 120 Hz, H min: 30  H max: 70 kHz, PixClock max 110 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0022f003050d150000
(II) RADEON(0): 	250b0103682018b7eae062a154469b24
(II) RADEON(0): 	0f484fa44a0031594559615981800101
(II) RADEON(0): 	010101010101ea240060410028303060
(II) RADEON(0): 	130040f01000001e000000ff0054484c
(II) RADEON(0): 	444b30353338390a2020000000fc004d
(II) RADEON(0): 	5837300a2020202020202020000000fd
(II) RADEON(0): 	0032781e460b000a20202020202000d7
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(II) RADEON(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(II) RADEON(0): Modeline "720x400"   28.32  720 738 846 900  400 412 414 449 -hsync +vsync
(II) RADEON(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(II) RADEON(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) RADEON(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(II) RADEON(0): Modeline "640x480"   35.00  640 664 728 816  480 483 487 507 -hsync +vsync
(II) RADEON(0): Modeline "800x600"   56.75  800 848 928 1056  600 603 607 633 -hsync +vsync
(II) RADEON(0): Modeline "1024x768"   94.50  1024 1096 1200 1376  768 771 775 809 -hsync +vsync
(II) RADEON(0): Modeline "1280x1024"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
(II) RADEON(0): Modeline "1024x768"   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync
(II) RADEON(0): EDID vendor "HWP", prod id 1283
(II) RADEON(0): Not using default mode "640x350" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x400" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "720x400" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x960" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x960" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "832x624" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x800" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1152x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1440x900" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1024" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Printing probed modes for output VGA-0
(II) RADEON(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) RADEON(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) RADEON(0): Modeline "1024x768"x84.9   94.50  1024 1096 1200 1376  768 771 775 809 -hsync +vsync (68.7 kHz)
(II) RADEON(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x84.9   56.75  800 848 928 1056  600 603 607 633 -hsync +vsync (53.7 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "640x480"x84.6   35.00  640 664 728 816  480 483 487 507 -hsync +vsync (42.9 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
SetClientVersion: 0 9


==========/var/log/Xorg.9.log (21:47)==========

X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8)
Current Operating System: Linux zeus 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686
Build Date: 29 September 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.9.log", Time: Sat Nov 17 21:47:46 2007
(++) Using config file: "/tmp/dcg-40qs1b5953/testserver.config"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "MX70"
(**) |   |-->Device "ATI Technologies Inc Radeon R200 QL [Radeon 8500 LE]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(WW) Including the default font path /usr/share/fonts/X11/misc,/usr/share/fonts/X11/cyrillic,/usr/share/fonts/X11/100dpi/:unscaled,/usr/share/fonts/X11/75dpi/:unscaled,/usr/share/fonts/X11/Type1,/usr/share/fonts/X11/100dpi,/usr/share/fonts/X11/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType.
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/cyrillic,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81ea440
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.2
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(--) using VT number 10

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 10de,01e0 card 147b,1c02 rev c1 class 06,00,00 hdr 80
(II) PCI: 00:00:1: chip 10de,01eb card 10de,0c17 rev c1 class 05,00,00 hdr 80
(II) PCI: 00:00:2: chip 10de,01ee card 10de,0c17 rev c1 class 05,00,00 hdr 80
(II) PCI: 00:00:3: chip 10de,01ed card 10de,0c17 rev c1 class 05,00,00 hdr 80
(II) PCI: 00:00:4: chip 10de,01ec card 10de,0c17 rev c1 class 05,00,00 hdr 80
(II) PCI: 00:00:5: chip 10de,01ef card 10de,0c17 rev c1 class 05,00,00 hdr 80
(II) PCI: 00:01:0: chip 10de,0060 card 147b,1c02 rev a4 class 06,01,00 hdr 80
(II) PCI: 00:01:1: chip 10de,0064 card 147b,1c02 rev a2 class 0c,05,00 hdr 80
(II) PCI: 00:02:0: chip 10de,0067 card 147b,1c02 rev a4 class 0c,03,10 hdr 80
(II) PCI: 00:02:1: chip 10de,0067 card 147b,1c02 rev a4 class 0c,03,10 hdr 80
(II) PCI: 00:02:2: chip 10de,0068 card 147b,1c02 rev a4 class 0c,03,20 hdr 80
(II) PCI: 00:04:0: chip 10de,0066 card 147b,1c02 rev a1 class 02,00,00 hdr 00
(II) PCI: 00:06:0: chip 10de,006a card 147b,1c02 rev a1 class 04,01,00 hdr 00
(II) PCI: 00:08:0: chip 10de,006c card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:09:0: chip 10de,0065 card 147b,1c02 rev a2 class 01,01,8a hdr 00
(II) PCI: 00:1e:0: chip 10de,01e8 card 0000,0000 rev c1 class 06,04,00 hdr 01
(II) PCI: 02:00:0: chip 1002,514c card 1002,003a rev 00 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:1:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:8:0), (0,1,1), BCTRL: 0x0202 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,2), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000c000 - 0x0000cfff (0x1000) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xe4000000 - 0xe5ffffff (0x2000000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
(--) PCI:*(2:0:0) ATI Technologies Inc Radeon R200 QL [Radeon 8500 LE] rev 0, Mem @ 0xd0000000/28, 0xe5000000/16, I/O @ 0xc000/8
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xe0000000 from 0xe3ffffff to 0xdfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xe6002000 - 0xe6002fff (0x1000) MX[B]
	[1] -1	0	0xe6001000 - 0xe6001fff (0x1000) MX[B]
	[2] -1	0	0xe6000000 - 0xe60000ff (0x100) MX[B]
	[3] -1	0	0xe6005000 - 0xe6005fff (0x1000) MX[B]
	[4] -1	0	0xe6004000 - 0xe6004fff (0x1000) MX[B]
	[5] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[6] -1	0	0xe5000000 - 0xe500ffff (0x10000) MX[B](B)
	[7] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[8] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[9] -1	0	0x0000d800 - 0x0000d87f (0x80) IX[B]
	[10] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[11] -1	0	0x0000d000 - 0x0000d007 (0x8) IX[B]
	[12] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[13] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xe6002000 - 0xe6002fff (0x1000) MX[B]
	[1] -1	0	0xe6001000 - 0xe6001fff (0x1000) MX[B]
	[2] -1	0	0xe6000000 - 0xe60000ff (0x100) MX[B]
	[3] -1	0	0xe6005000 - 0xe6005fff (0x1000) MX[B]
	[4] -1	0	0xe6004000 - 0xe6004fff (0x1000) MX[B]
	[5] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[6] -1	0	0xe5000000 - 0xe500ffff (0x10000) MX[B](B)
	[7] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[8] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[9] -1	0	0x0000d800 - 0x0000d87f (0x80) IX[B]
	[10] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[11] -1	0	0x0000d000 - 0x0000d007 (0x8) IX[B]
	[12] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[13] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe6002000 - 0xe6002fff (0x1000) MX[B]
	[5] -1	0	0xe6001000 - 0xe6001fff (0x1000) MX[B]
	[6] -1	0	0xe6000000 - 0xe60000ff (0x100) MX[B]
	[7] -1	0	0xe6005000 - 0xe6005fff (0x1000) MX[B]
	[8] -1	0	0xe6004000 - 0xe6004fff (0x1000) MX[B]
	[9] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[10] -1	0	0xe5000000 - 0xe500ffff (0x10000) MX[B](B)
	[11] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[12] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[13] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[14] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[15] -1	0	0x0000d800 - 0x0000d87f (0x80) IX[B]
	[16] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[17] -1	0	0x0000d000 - 0x0000d007 (0x8) IX[B]
	[18] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[19] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
(II) LoadModule: "i2c"(II) Module already built-in
(II) LoadModule: "ddc"(II) Module already built-in
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules/fonts//libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.3.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.2
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "v4l"
(II) Loading /usr/lib/xorg/modules/drivers//v4l_drv.so
(II) Module v4l: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.1
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "radeon"
(II) Loading /usr/lib/xorg/modules/drivers//radeon_drv.so
(II) Module radeon: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 4.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.2
(II) LoadModule: "ati"
(II) Loading /usr/lib/xorg/modules/drivers//ati_drv.so
(II) Module ati: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 6.7.195
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.2
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) Wacom driver level: 47-0.7.7-7 $
(II) v4l driver for Video4Linux
(II) ATI: ATI driver wrapper (version 6.7.195) for chipsets: mach64, rage128, radeon
(II) Primary Device is: PCI 02:00:0
(II) Loading sub module "radeon"
(II) LoadModule: "radeon"
(II) Reloading /usr/lib/xorg/modules/drivers//radeon_drv.so
(II) RADEON: Driver for ATI Radeon chipsets: ATI Radeon QD (AGP),
	ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
	ATI Radeon VE/7000 QY (AGP/PCI), ATI Radeon VE/7000 QZ (AGP/PCI),
	ATI ES1000 515E (PCI), ATI ES1000 5969 (PCI),
	ATI Radeon Mobility M7 LW (AGP),
	ATI Mobility FireGL 7800 M7 LX (AGP),
	ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
	ATI Radeon IGP320 (A3) 4136, ATI Radeon IGP320M (U1) 4336,
	ATI Radeon IGP330/340/350 (A4) 4137,
	ATI Radeon IGP330M/340M/350M (U2) 4337,
	ATI Radeon 7000 IGP (A4+) 4237, ATI Radeon Mobility 7000 IGP 4437,
	ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
	ATI Radeon 9100 QM (AGP), ATI Radeon 8500 AIW BB (AGP),
	ATI Radeon 8500 AIW BC (AGP), ATI Radeon 7500 QW (AGP/PCI),
	ATI Radeon 7500 QX (AGP/PCI), ATI Radeon 9000/PRO If (AGP/PCI),
	ATI Radeon 9000 Ig (AGP/PCI), ATI FireGL Mobility 9000 (M9) Ld (AGP),
	ATI Radeon Mobility 9000 (M9) Lf (AGP),
	ATI Radeon Mobility 9000 (M9) Lg (AGP),
	ATI Radeon 9100 IGP (A5) 5834,
	ATI Radeon Mobility 9100 IGP (U3) 5835, ATI Radeon 9100 PRO IGP 7834,
	ATI Radeon Mobility 9200 IGP 7835, ATI Radeon 9250 5960 (AGP),
	ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
	ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
	ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
	ATI Radeon Mobility 9200 (M9+) 5C63 (AGP), ATI Radeon 9500 AD (AGP),
	ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
	ATI FireGL Z1 AG (AGP), ATI Radeon 9700 Pro ND (AGP),
	ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9600TX NF (AGP),
	ATI FireGL X1 NG (AGP), ATI Radeon 9600 AP (AGP),
	ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
	ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP),
	ATI FireGL RV360 AV (AGP),
	ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
	ATI Radeon Mobility 9600 (M10) NQ (AGP),
	ATI Radeon Mobility 9600 (M11) NR (AGP),
	ATI Radeon Mobility 9600 (M10) NS (AGP),
	ATI FireGL Mobility T2 (M10) NT (AGP),
	ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon 9650,
	ATI Radeon 9800SE AH (AGP), ATI Radeon 9800 AI (AGP),
	ATI Radeon 9800 AJ (AGP), ATI FireGL X2 AK (AGP),
	ATI Radeon 9800PRO NH (AGP), ATI Radeon 9800 NI (AGP),
	ATI FireGL X2 NK (AGP), ATI Radeon 9800XT NJ (AGP),
	ATI Radeon X600 (RV380) 3E50 (PCIE),
	ATI FireGL V3200 (RV380) 3E54 (PCIE),
	ATI Radeon Mobility X600 (M24) 3150 (PCIE),
	ATI Radeon Mobility X300 (M24) 3152 (PCIE),
	ATI FireGL M24 GL 3154 (PCIE), ATI Radeon X300 (RV370) 5B60 (PCIE),
	ATI Radeon X600 (RV370) 5B62 (PCIE),
	ATI Radeon X550 (RV370) 5B63 (PCIE),
	ATI FireGL V3100 (RV370) 5B64 (PCIE),
	ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
	ATI Radeon Mobility X300 (M22) 5460 (PCIE),
	ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
	ATI FireGL M22 GL 5464 (PCIE), ATI Radeon XPRESS 200 5A41 (PCIE),
	ATI Radeon XPRESS 200M 5A42 (PCIE),
	ATI Radeon XPRESS 200 5A61 (PCIE),
	ATI Radeon XPRESS 200M 5A62 (PCIE),
	ATI Radeon XPRESS 200 5954 (PCIE),
	ATI Radeon XPRESS 200M 5955 (PCIE),
	ATI Radeon XPRESS 200 5974 (PCIE),
	ATI Radeon XPRESS 200M 5975 (PCIE), ATI FireGL V5000 (RV410) (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility Radeon X700 XL (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Radeon X700 PRO (RV410) (PCIE),
	ATI Radeon X700 XT (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 SE (RV410) (PCIE),
	ATI Radeon X800 (R420) JH (AGP), ATI Radeon X800PRO (R420) JI (AGP),
	ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
	ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
	ATI Radeon Mobility 9800 (M18) JN (AGP),
	ATI Radeon X800XT (R420) JP (AGP), ATI Radeon X800 SE (R420) (AGP),
	ATI Radeon AIW X800 VE (R420) JT (AGP),
	ATI Radeon X800 (R423) UH (PCIE),
	ATI Radeon X800PRO (R423) UI (PCIE),
	ATI Radeon X800LE (R423) UJ (PCIE),
	ATI Radeon X800SE (R423) UK (PCIE),
	ATI FireGL V5100 (R423) UQ (PCIE),
	ATI FireGL unknown (R423) UR (PCIE),
	ATI FireGL unknown (R423) UT (PCIE),
	ATI Radeon X800XT (R423) 5D57 (PCIE), ATI FireGL V7100 (R423) (PCIE),
	ATI Mobility FireGL V5100 (M28) (PCIE),
	ATI Mobility Radeon X800 (M28) (PCIE),
	ATI Mobility Radeon X800 XT (M28) (PCIE),
	ATI Radeon X800 (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
	ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 XTP (R430) (PCIE),
	ATI Radeon X850 5D4C (PCIE),
	ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
	ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
	ATI Radeon X850 XT (R480) (PCIE),
	ATI Radeon X850 XT PE (R480) (PCIE),
	ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
	ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP)
(--) Chipset ATI Radeon 8500 QL (AGP) found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe6002000 - 0xe6002fff (0x1000) MX[B]
	[5] -1	0	0xe6001000 - 0xe6001fff (0x1000) MX[B]
	[6] -1	0	0xe6000000 - 0xe60000ff (0x100) MX[B]
	[7] -1	0	0xe6005000 - 0xe6005fff (0x1000) MX[B]
	[8] -1	0	0xe6004000 - 0xe6004fff (0x1000) MX[B]
	[9] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[10] -1	0	0xe5000000 - 0xe500ffff (0x10000) MX[B](B)
	[11] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[12] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[13] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[14] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[15] -1	0	0x0000d800 - 0x0000d87f (0x80) IX[B]
	[16] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[17] -1	0	0x0000d000 - 0x0000d007 (0x8) IX[B]
	[18] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[19] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe6002000 - 0xe6002fff (0x1000) MX[B]
	[5] -1	0	0xe6001000 - 0xe6001fff (0x1000) MX[B]
	[6] -1	0	0xe6000000 - 0xe60000ff (0x100) MX[B]
	[7] -1	0	0xe6005000 - 0xe6005fff (0x1000) MX[B]
	[8] -1	0	0xe6004000 - 0xe6004fff (0x1000) MX[B]
	[9] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[10] -1	0	0xe5000000 - 0xe500ffff (0x10000) MX[B](B)
	[11] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[12] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[13] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[14] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[18] -1	0	0x0000d800 - 0x0000d87f (0x80) IX[B]
	[19] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[20] -1	0	0x0000d000 - 0x0000d007 (0x8) IX[B]
	[21] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[22] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
	[23] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[24] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) RADEON(0): MMIO registers at 0xe5000000: size 64KB
(II) RADEON(0): PCI bus 2 card 0 func 0
(**) RADEON(0): Depth 24, (--) framebuffer bpp 32
(II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) RADEON(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.2
(II) RADEON(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) RADEON(0): RGB weight 888
(II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) RADEON(0): initializing int10
(II) RADEON(0): Primary V_BIOS segment is: 0xc000
(--) RADEON(0): Chipset: "ATI Radeon 8500 QL (AGP)" (ChipID = 0x514c)
(--) RADEON(0): Linear framebuffer at 0xd0000000
(II) RADEON(0): AGP card detected
(II) RADEON(0): Legacy BIOS detected
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: Searching for BusID pci:0000:02:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: drmOpenMinor returns 9
drmOpenByBusid: drmGetBusid reports pci:0000:02:00.0
(II) RADEON(0): [dri] Found DRI library version 1.3.0 and kernel module version 1.27.0
(==) RADEON(0): Page Flipping disabled
(II) RADEON(0): Will try to use DMA for Xv image transfers
(II) RADEON(0): Detected total video RAM=131072K, accessible=131072K (PCI BAR=262144K)
(--) RADEON(0): Mapped VideoRAM: 131072 kByte (128 bit DDR SDRAM)
(II) RADEON(0): Color tiling enabled by default
(II) RADEON(0): Max desktop size set to 1400x1050
(II) RADEON(0): For a larger or smaller max desktop size, add a Virtual line to your xorg.conf
(II) RADEON(0): If you are having trouble with 3D, reduce the desktop size by adjusting the Virtual line to your xorg.conf
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"(II) Module already built-in
(II) RADEON(0): PLL parameters: rf=2700 rd=12 min=20000 max=35000; xclk=25000
(II) RADEON(0): Bios Connector table: 
(II) RADEON(0): Port0: DDCType-3, DACType-0, TMDSType-0, ConnectorType-2
(II) RADEON(0): Output VGA-0 using monitor section MX70
(II) RADEON(0): I2C bus "VGA_DDC" initialized.
(II) RADEON(0): Port0:
 Monitor   -- AUTO
 Connector -- VGA
 DAC Type  -- Primary
 TMDS Type -- None
 DDC Type  -- VGA_DDC
(II) RADEON(0): I2C device "VGA_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" removed.
(II) RADEON(0): DDC Type: 3, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on connector: VGA ----------------------
(II) RADEON(0): Manufacturer: HWP  Model: 503  Serial#: 5389
(II) RADEON(0): Year: 2001  Week: 37
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 32  vert.: 24
(II) RADEON(0): Gamma: 2.83
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.632 redY: 0.330   greenX: 0.273 greenY: 0.605
(II) RADEON(0): blueX: 0.142 blueY: 0.061   whiteX: 0.281 whiteY: 0.311
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEON(0): #1: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEON(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEON(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 94.5 MHz   Image Size:  320 x 240 mm
(II) RADEON(0): h_active: 1024  h_sync: 1072  h_sync_end 1168 h_blank_end 1376 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 808 v_border: 0
(II) RADEON(0): Serial No: THLDK05389
(II) RADEON(0): Monitor name: MX70
(II) RADEON(0): Ranges: V min: 50  V max: 120 Hz, H min: 30  H max: 70 kHz, PixClock max 110 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0022f003050d150000
(II) RADEON(0): 	250b0103682018b7eae062a154469b24
(II) RADEON(0): 	0f484fa44a0031594559615981800101
(II) RADEON(0): 	010101010101ea240060410028303060
(II) RADEON(0): 	130040f01000001e000000ff0054484c
(II) RADEON(0): 	444b30353338390a2020000000fc004d
(II) RADEON(0): 	5837300a2020202020202020000000fd
(II) RADEON(0): 	0032781e460b000a20202020202000d7
finished output detect: 0
finished all detect
before xf86InitialConfiguration
(II) RADEON(0): I2C device "VGA_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" removed.
(II) RADEON(0): DDC Type: 3, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on connector: VGA ----------------------
(II) RADEON(0): Manufacturer: HWP  Model: 503  Serial#: 5389
(II) RADEON(0): Year: 2001  Week: 37
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 32  vert.: 24
(II) RADEON(0): Gamma: 2.83
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.632 redY: 0.330   greenX: 0.273 greenY: 0.605
(II) RADEON(0): blueX: 0.142 blueY: 0.061   whiteX: 0.281 whiteY: 0.311
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEON(0): #1: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEON(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEON(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 94.5 MHz   Image Size:  320 x 240 mm
(II) RADEON(0): h_active: 1024  h_sync: 1072  h_sync_end 1168 h_blank_end 1376 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 808 v_border: 0
(II) RADEON(0): Serial No: THLDK05389
(II) RADEON(0): Monitor name: MX70
(II) RADEON(0): Ranges: V min: 50  V max: 120 Hz, H min: 30  H max: 70 kHz, PixClock max 110 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0022f003050d150000
(II) RADEON(0): 	250b0103682018b7eae062a154469b24
(II) RADEON(0): 	0f484fa44a0031594559615981800101
(II) RADEON(0): 	010101010101ea240060410028303060
(II) RADEON(0): 	130040f01000001e000000ff0054484c
(II) RADEON(0): 	444b30353338390a2020000000fc004d
(II) RADEON(0): 	5837300a2020202020202020000000fd
(II) RADEON(0): 	0032781e460b000a20202020202000d7
(II) RADEON(0): Output VGA-0 connected
in RADEONProbeOutputModes
(II) RADEON(0): I2C device "VGA_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" removed.
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): Manufacturer: HWP  Model: 503  Serial#: 5389
(II) RADEON(0): Year: 2001  Week: 37
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 32  vert.: 24
(II) RADEON(0): Gamma: 2.83
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.632 redY: 0.330   greenX: 0.273 greenY: 0.605
(II) RADEON(0): blueX: 0.142 blueY: 0.061   whiteX: 0.281 whiteY: 0.311
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEON(0): #1: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEON(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEON(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 94.5 MHz   Image Size:  320 x 240 mm
(II) RADEON(0): h_active: 1024  h_sync: 1072  h_sync_end 1168 h_blank_end 1376 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 808 v_border: 0
(II) RADEON(0): Serial No: THLDK05389
(II) RADEON(0): Monitor name: MX70
(II) RADEON(0): Ranges: V min: 50  V max: 120 Hz, H min: 30  H max: 70 kHz, PixClock max 110 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0022f003050d150000
(II) RADEON(0): 	250b0103682018b7eae062a154469b24
(II) RADEON(0): 	0f484fa44a0031594559615981800101
(II) RADEON(0): 	010101010101ea240060410028303060
(II) RADEON(0): 	130040f01000001e000000ff0054484c
(II) RADEON(0): 	444b30353338390a2020000000fc004d
(II) RADEON(0): 	5837300a2020202020202020000000fd
(II) RADEON(0): 	0032781e460b000a20202020202000d7
(II) RADEON(0): Using EDID range info for horizontal sync
(II) RADEON(0): Using EDID range info for vertical refresh
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(II) RADEON(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(II) RADEON(0): Modeline "720x400"   28.32  720 738 846 900  400 412 414 449 -hsync +vsync
(II) RADEON(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(II) RADEON(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) RADEON(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(II) RADEON(0): Modeline "640x480"   35.00  640 664 728 816  480 483 487 507 -hsync +vsync
(II) RADEON(0): Modeline "800x600"   56.75  800 848 928 1056  600 603 607 633 -hsync +vsync
(II) RADEON(0): Modeline "1024x768"   94.50  1024 1096 1200 1376  768 771 775 809 -hsync +vsync
(II) RADEON(0): Modeline "1280x1024"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
(II) RADEON(0): Modeline "1024x768"   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync
(II) RADEON(0): EDID vendor "HWP", prod id 1283
(II) RADEON(0): Not using default mode "640x350" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x400" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "720x400" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x960" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x960" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "832x624" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x800" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1152x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1440x900" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1024" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Printing probed modes for output VGA-0
(II) RADEON(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) RADEON(0): Modeline "1400x1050@60"x60.0  122.61  1400 1488 1640 1880  1050 1051 1054 1087 -hsync +vsync (65.2 kHz)
(II) RADEON(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) RADEON(0): Modeline "1280x1024@60"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "1280x960@60"x60.0  102.10  1280 1360 1496 1712  960 961 964 994 -hsync +vsync (59.6 kHz)
(II) RADEON(0): Modeline "1152x864@75"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1024x768@85"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) RADEON(0): Modeline "1024x768"x84.9   94.50  1024 1096 1200 1376  768 771 775 809 -hsync +vsync (68.7 kHz)
(II) RADEON(0): Modeline "1024x768@75"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "1024x768@70"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768@60"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "1024x768@43"x87.0   44.90  1024 1032 1208 1264  768 768 776 817 interlace +hsync +vsync (35.5 kHz)
(II) RADEON(0): Modeline "832x624@75"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x84.9   56.75  800 848 928 1056  600 603 607 633 -hsync +vsync (53.7 kHz)
(II) RADEON(0): Modeline "800x600@85"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) RADEON(0): Modeline "800x600@72"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "800x600@75"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600@60"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600@56"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480@85"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) RADEON(0): Modeline "640x480"x84.6   35.00  640 664 728 816  480 483 487 507 -hsync +vsync (42.9 kHz)
(II) RADEON(0): Modeline "640x480@72"x72.8   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480@75"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480@60"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Output VGA-0 connected
(II) RADEON(0): Output VGA-0 using initial mode 1024x768
after xf86InitialConfiguration
(**) RADEON(0): Display dimensions: (320, 240) mm
(**) RADEON(0): DPI set to (111, 111)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(**) RADEON(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module already built-in
(==) RADEON(0): Using XAA acceleration architecture
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.2
(==) RADEON(0): Assuming overlay scaler buffer width is 1920
(II) RADEON(0): No MM_TABLE found - assuming CARD is not TV-in capable.
(!!) RADEON(0): For information on using the multimedia capabilities
	of this adapter, please see http://gatos.sf.net.
(!!) RADEON(0): MergedFB support has been removed and replaced with xrandr 1.2 support
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xe5000000 - 0xe500ffff (0x10000) MX[B]
	[1] 0	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xe6002000 - 0xe6002fff (0x1000) MX[B]
	[7] -1	0	0xe6001000 - 0xe6001fff (0x1000) MX[B]
	[8] -1	0	0xe6000000 - 0xe60000ff (0x100) MX[B]
	[9] -1	0	0xe6005000 - 0xe6005fff (0x1000) MX[B]
	[10] -1	0	0xe6004000 - 0xe6004fff (0x1000) MX[B]
	[11] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[12] -1	0	0xe5000000 - 0xe500ffff (0x10000) MX[B](B)
	[13] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[14] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[15] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[16] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[17] 0	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[21] -1	0	0x0000d800 - 0x0000d87f (0x80) IX[B]
	[22] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[23] -1	0	0x0000d000 - 0x0000d007 (0x8) IX[B]
	[24] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[25] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
	[26] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[27] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(==) RADEON(0): Write-combining range (0xd0000000,0x8000000)
(==) RADEON(0): Using 24 bit depth buffer
(II) RADEON(0): RADEONInitMemoryMap() : 
(II) RADEON(0):   mem_size         : 0x08000000
(II) RADEON(0):   MC_FB_LOCATION   : 0xd7ffd000
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(II) RADEON(0): Depth moves disabled by default
(II) RADEON(0): CP in BM mode
(II) RADEON(0): Using 8 MB GART aperture
(II) RADEON(0): Using 1 MB for the ring buffer
(II) RADEON(0): Using 2 MB for vertex/indirect buffers
(II) RADEON(0): Using 5 MB for GART textures
(II) RADEON(0): Memory manager initialized to (0,0) (1408,8191)
(II) RADEON(0): Reserved area from (0,1050) to (1408,1058)
(II) RADEON(0): Largest offscreen area available: 1408 x 7133
(II) RADEON(0): Will use front buffer at offset 0x0
(II) RADEON(0): Will use back buffer at offset 0x1894000
(II) RADEON(0): Will use depth buffer at offset 0x1e40000
(II) RADEON(0): Will use 94208 kb for textures at offset 0x23ec000
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: Searching for BusID pci:0000:02:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: drmOpenMinor returns 9
drmOpenByBusid: drmGetBusid reports pci:0000:02:00.0
(II) RADEON(0): [drm] DRM interface version 1.0
(II) RADEON(0): [drm] drmSetBusid failed (9, pci:0000:02:00.0), Permission denied
(EE) RADEON(0): [dri] DRIScreenInit failed.  Disabling DRI.
init memmap
init common
init crtc1
init pll1
restore memmap
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0xd7ffd000
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
restore common
restore crtc1
restore pll1
finished PLL1
restore dac
enable montype: 1
(WW) RADEON(0): No crtc mode list for crtc 1,continuing with desired mode
disable montype: 1
(==) RADEON(0): Backing store disabled
(WW) RADEON(0): Direct rendering disabled
(II) RADEON(0): Render acceleration enabled
(II) RADEON(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Lines
	Scanline Image Writes
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(II) RADEON(0): Acceleration enabled
(==) RADEON(0): Silken mouse enabled
(II) RADEON(0): Using hardware cursor (scanline 1058)
(II) RADEON(0): Largest offscreen area available: 1408 x 7130
(II) RADEON(0): No video input capabilities detected and no information is provided - disabling multimedia i2c
(II) Loading sub module "theatre_detect"
(II) LoadModule: "theatre_detect"
(II) Loading /usr/lib/xorg/modules/multimedia//theatre_detect_drv.so
(II) Module theatre_detect: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(II) RADEON(0): no multimedia table present, disabling Rage Theatre.
(II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(WW) RADEON(0): Option "MergedFB" is not used
(--) RandR disabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(EE) AIGLX: Screen 0 is not DRI capable
(II) Loading local sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
(II) RADEON(0): Setting screen physical size to 320 x 240
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/input/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/input/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/input/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
enable montype: 1
(II) RADEON(0): I2C device "VGA_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" removed.
(II) RADEON(0): DDC Type: 3, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on connector: VGA ----------------------
(II) RADEON(0): Manufacturer: HWP  Model: 503  Serial#: 5389
(II) RADEON(0): Year: 2001  Week: 37
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 32  vert.: 24
(II) RADEON(0): Gamma: 2.83
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.632 redY: 0.330   greenX: 0.273 greenY: 0.605
(II) RADEON(0): blueX: 0.142 blueY: 0.061   whiteX: 0.281 whiteY: 0.311
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEON(0): #1: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEON(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEON(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 94.5 MHz   Image Size:  320 x 240 mm
(II) RADEON(0): h_active: 1024  h_sync: 1072  h_sync_end 1168 h_blank_end 1376 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 808 v_border: 0
(II) RADEON(0): Serial No: THLDK05389
(II) RADEON(0): Monitor name: MX70
(II) RADEON(0): Ranges: V min: 50  V max: 120 Hz, H min: 30  H max: 70 kHz, PixClock max 110 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0022f003050d150000
(II) RADEON(0): 	250b0103682018b7eae062a154469b24
(II) RADEON(0): 	0f484fa44a0031594559615981800101
(II) RADEON(0): 	010101010101ea240060410028303060
(II) RADEON(0): 	130040f01000001e000000ff0054484c
(II) RADEON(0): 	444b30353338390a2020000000fc004d
(II) RADEON(0): 	5837300a2020202020202020000000fd
(II) RADEON(0): 	0032781e460b000a20202020202000d7
(II) RADEON(0): Output VGA-0 connected
in RADEONProbeOutputModes
(II) RADEON(0): I2C device "VGA_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" removed.
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): Manufacturer: HWP  Model: 503  Serial#: 5389
(II) RADEON(0): Year: 2001  Week: 37
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 32  vert.: 24
(II) RADEON(0): Gamma: 2.83
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.632 redY: 0.330   greenX: 0.273 greenY: 0.605
(II) RADEON(0): blueX: 0.142 blueY: 0.061   whiteX: 0.281 whiteY: 0.311
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEON(0): #1: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEON(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEON(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 94.5 MHz   Image Size:  320 x 240 mm
(II) RADEON(0): h_active: 1024  h_sync: 1072  h_sync_end 1168 h_blank_end 1376 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 808 v_border: 0
(II) RADEON(0): Serial No: THLDK05389
(II) RADEON(0): Monitor name: MX70
(II) RADEON(0): Ranges: V min: 50  V max: 120 Hz, H min: 30  H max: 70 kHz, PixClock max 110 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0022f003050d150000
(II) RADEON(0): 	250b0103682018b7eae062a154469b24
(II) RADEON(0): 	0f484fa44a0031594559615981800101
(II) RADEON(0): 	010101010101ea240060410028303060
(II) RADEON(0): 	130040f01000001e000000ff0054484c
(II) RADEON(0): 	444b30353338390a2020000000fc004d
(II) RADEON(0): 	5837300a2020202020202020000000fd
(II) RADEON(0): 	0032781e460b000a20202020202000d7
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(II) RADEON(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(II) RADEON(0): Modeline "720x400"   28.32  720 738 846 900  400 412 414 449 -hsync +vsync
(II) RADEON(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(II) RADEON(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) RADEON(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(II) RADEON(0): Modeline "640x480"   35.00  640 664 728 816  480 483 487 507 -hsync +vsync
(II) RADEON(0): Modeline "800x600"   56.75  800 848 928 1056  600 603 607 633 -hsync +vsync
(II) RADEON(0): Modeline "1024x768"   94.50  1024 1096 1200 1376  768 771 775 809 -hsync +vsync
(II) RADEON(0): Modeline "1280x1024"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
(II) RADEON(0): Modeline "1024x768"   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync
(II) RADEON(0): EDID vendor "HWP", prod id 1283
(II) RADEON(0): Not using default mode "640x350" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x400" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "720x400" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x960" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x960" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "832x624" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x800" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1152x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1440x900" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1024" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Printing probed modes for output VGA-0
(II) RADEON(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) RADEON(0): Modeline "1400x1050@60"x60.0  122.61  1400 1488 1640 1880  1050 1051 1054 1087 -hsync +vsync (65.2 kHz)
(II) RADEON(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) RADEON(0): Modeline "1280x1024@60"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "1280x960@60"x60.0  102.10  1280 1360 1496 1712  960 961 964 994 -hsync +vsync (59.6 kHz)
(II) RADEON(0): Modeline "1152x864@75"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1024x768@85"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) RADEON(0): Modeline "1024x768"x84.9   94.50  1024 1096 1200 1376  768 771 775 809 -hsync +vsync (68.7 kHz)
(II) RADEON(0): Modeline "1024x768@75"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "1024x768@70"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768@60"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "1024x768@43"x87.0   44.90  1024 1032 1208 1264  768 768 776 817 interlace +hsync +vsync (35.5 kHz)
(II) RADEON(0): Modeline "832x624@75"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x84.9   56.75  800 848 928 1056  600 603 607 633 -hsync +vsync (53.7 kHz)
(II) RADEON(0): Modeline "800x600@85"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) RADEON(0): Modeline "800x600@72"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "800x600@75"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600@60"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600@56"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480@85"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) RADEON(0): Modeline "640x480"x84.6   35.00  640 664 728 816  480 483 487 507 -hsync +vsync (42.9 kHz)
(II) RADEON(0): Modeline "640x480@72"x72.8   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480@75"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480@60"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): I2C device "VGA_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" removed.
(II) RADEON(0): DDC Type: 3, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on connector: VGA ----------------------
(II) RADEON(0): Manufacturer: HWP  Model: 503  Serial#: 5389
(II) RADEON(0): Year: 2001  Week: 37
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 32  vert.: 24
(II) RADEON(0): Gamma: 2.83
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.632 redY: 0.330   greenX: 0.273 greenY: 0.605
(II) RADEON(0): blueX: 0.142 blueY: 0.061   whiteX: 0.281 whiteY: 0.311
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEON(0): #1: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEON(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEON(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 94.5 MHz   Image Size:  320 x 240 mm
(II) RADEON(0): h_active: 1024  h_sync: 1072  h_sync_end 1168 h_blank_end 1376 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 808 v_border: 0
(II) RADEON(0): Serial No: THLDK05389
(II) RADEON(0): Monitor name: MX70
(II) RADEON(0): Ranges: V min: 50  V max: 120 Hz, H min: 30  H max: 70 kHz, PixClock max 110 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0022f003050d150000
(II) RADEON(0): 	250b0103682018b7eae062a154469b24
(II) RADEON(0): 	0f484fa44a0031594559615981800101
(II) RADEON(0): 	010101010101ea240060410028303060
(II) RADEON(0): 	130040f01000001e000000ff0054484c
(II) RADEON(0): 	444b30353338390a2020000000fc004d
(II) RADEON(0): 	5837300a2020202020202020000000fd
(II) RADEON(0): 	0032781e460b000a20202020202000d7
(II) RADEON(0): Output VGA-0 connected
in RADEONProbeOutputModes
(II) RADEON(0): I2C device "VGA_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" removed.
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): Manufacturer: HWP  Model: 503  Serial#: 5389
(II) RADEON(0): Year: 2001  Week: 37
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 32  vert.: 24
(II) RADEON(0): Gamma: 2.83
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.632 redY: 0.330   greenX: 0.273 greenY: 0.605
(II) RADEON(0): blueX: 0.142 blueY: 0.061   whiteX: 0.281 whiteY: 0.311
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEON(0): #1: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEON(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEON(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 94.5 MHz   Image Size:  320 x 240 mm
(II) RADEON(0): h_active: 1024  h_sync: 1072  h_sync_end 1168 h_blank_end 1376 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 808 v_border: 0
(II) RADEON(0): Serial No: THLDK05389
(II) RADEON(0): Monitor name: MX70
(II) RADEON(0): Ranges: V min: 50  V max: 120 Hz, H min: 30  H max: 70 kHz, PixClock max 110 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0022f003050d150000
(II) RADEON(0): 	250b0103682018b7eae062a154469b24
(II) RADEON(0): 	0f484fa44a0031594559615981800101
(II) RADEON(0): 	010101010101ea240060410028303060
(II) RADEON(0): 	130040f01000001e000000ff0054484c
(II) RADEON(0): 	444b30353338390a2020000000fc004d
(II) RADEON(0): 	5837300a2020202020202020000000fd
(II) RADEON(0): 	0032781e460b000a20202020202000d7
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(II) RADEON(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(II) RADEON(0): Modeline "720x400"   28.32  720 738 846 900  400 412 414 449 -hsync +vsync
(II) RADEON(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(II) RADEON(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) RADEON(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(II) RADEON(0): Modeline "640x480"   35.00  640 664 728 816  480 483 487 507 -hsync +vsync
(II) RADEON(0): Modeline "800x600"   56.75  800 848 928 1056  600 603 607 633 -hsync +vsync
(II) RADEON(0): Modeline "1024x768"   94.50  1024 1096 1200 1376  768 771 775 809 -hsync +vsync
(II) RADEON(0): Modeline "1280x1024"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
(II) RADEON(0): Modeline "1024x768"   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync
(II) RADEON(0): EDID vendor "HWP", prod id 1283
(II) RADEON(0): Not using default mode "640x350" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x400" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "720x400" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x960" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x960" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "832x624" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x800" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1152x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1440x900" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1024" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Printing probed modes for output VGA-0
(II) RADEON(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) RADEON(0): Modeline "1400x1050@60"x60.0  122.61  1400 1488 1640 1880  1050 1051 1054 1087 -hsync +vsync (65.2 kHz)
(II) RADEON(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) RADEON(0): Modeline "1280x1024@60"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "1280x960@60"x60.0  102.10  1280 1360 1496 1712  960 961 964 994 -hsync +vsync (59.6 kHz)
(II) RADEON(0): Modeline "1152x864@75"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1024x768@85"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) RADEON(0): Modeline "1024x768"x84.9   94.50  1024 1096 1200 1376  768 771 775 809 -hsync +vsync (68.7 kHz)
(II) RADEON(0): Modeline "1024x768@75"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "1024x768@70"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768@60"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "1024x768@43"x87.0   44.90  1024 1032 1208 1264  768 768 776 817 interlace +hsync +vsync (35.5 kHz)
(II) RADEON(0): Modeline "832x624@75"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x84.9   56.75  800 848 928 1056  600 603 607 633 -hsync +vsync (53.7 kHz)
(II) RADEON(0): Modeline "800x600@85"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) RADEON(0): Modeline "800x600@72"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "800x600@75"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600@60"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600@56"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480@85"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) RADEON(0): Modeline "640x480"x84.6   35.00  640 664 728 816  480 483 487 507 -hsync +vsync (42.9 kHz)
(II) RADEON(0): Modeline "640x480@72"x72.8   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480@75"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480@60"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
disable montype: 1
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x1fff0000
(II) RADEON(0):   MC_AGP_LOCATION  : 0x27ff2000
finished PLL2
finished PLL1
FreeFontPath: FPE "/usr/share/fonts/X11/misc" refcount is 2, should be 1; fixing.


==========/usr/bin/xdpyinfo==========
name of display:    :0.0
version number:    11.0
vendor string:    The X.Org Foundation
vendor release number:    10300000
X.Org version: 1.3.0
maximum request size:  16777212 bytes
motion buffer size:  256
bitmap unit, bit order, padding:    32, LSBFirst, 32
image byte order:    LSBFirst
number of supported pixmap formats:    7
supported pixmap formats:
    depth 1, bits_per_pixel 1, scanline_pad 32
    depth 4, bits_per_pixel 8, scanline_pad 32
    depth 8, bits_per_pixel 8, scanline_pad 32
    depth 15, bits_per_pixel 16, scanline_pad 32
    depth 16, bits_per_pixel 16, scanline_pad 32
    depth 24, bits_per_pixel 32, scanline_pad 32
    depth 32, bits_per_pixel 32, scanline_pad 32
keycode range:    minimum 8, maximum 255
focus:  window 0x3200021, revert to Parent
number of extensions:    33
    BIG-REQUESTS
    Composite
    DAMAGE
    DOUBLE-BUFFER
    DPMS
    Extended-Visual-Information
    GLX
    MIT-SCREEN-SAVER
    MIT-SHM
    MIT-SUNDRY-NONSTANDARD
    RANDR
    RECORD
    RENDER
    SECURITY
    SGI-GLX
    SHAPE
    SYNC
    TOG-CUP
    X-Resource
    XAccessControlExtension
    XC-APPGROUP
    XC-MISC
    XFIXES
    XFree86-Bigfont
    XFree86-DGA
    XFree86-DRI
    XFree86-Misc
    XFree86-VidModeExtension
    XINERAMA
    XInputExtension
    XKEYBOARD
    XTEST
    XVideo
default screen number:    0
number of screens:    1

screen #0:
  dimensions:    1024x768 pixels (320x240 millimeters)
  resolution:    81x81 dots per inch
  depths (7):    24, 1, 4, 8, 15, 16, 32
  root window id:    0x5b
  depth of root window:    24 planes
  number of colormaps:    minimum 1, maximum 1
  default colormap:    0x20
  default number of colormap cells:    256
  preallocated pixels:    black 0, white 16777215
  options:    backing-store NO, save-unders NO
  largest cursor:    64x64
  current input event mask:    0xfa0033
    KeyPressMask             KeyReleaseMask           EnterWindowMask          
    LeaveWindowMask          StructureNotifyMask      SubstructureNotifyMask   
    SubstructureRedirectMask FocusChangeMask          PropertyChangeMask       
    ColormapChangeMask       
  number of visuals:    17
  default visual id:  0x23
  visual:
    visual id:    0x23
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x24
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x25
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x26
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x27
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x28
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x29
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x2a
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x2b
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x2c
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x2d
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x2e
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x2f
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x30
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x31
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x32
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x59
    class:    TrueColor
    depth:    32 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits



==========KERNEL RELATED==========


==========/var/log/dmesg (03:16)==========
[    0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000004fff0000 (usable)
[    0.000000]  BIOS-e820: 000000004fff0000 - 000000004fff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000004fff3000 - 0000000050000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] 383MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 327664) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   327664
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   327664
[    0.000000] On node 0 totalpages: 327664
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 767 pages used for memmap
[    0.000000]   HighMem zone: 97521 pages, LIFO batch:31
[    0.000000] DMI 2.2 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F6B00 checksum 0
[    0.000000] ACPI: RSDP 000F6B00, 0014 (r0 Nvidia)
[    0.000000] ACPI: RSDT 4FFF3000, 002C (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP 4FFF3040, 0074 (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT 4FFF30C0, 48E8 (r1 NVIDIA AWRDACPI     1000 MSFT  100000D)
[    0.000000] ACPI: FACS 4FFF0000, 0040
[    0.000000] ACPI: APIC 4FFF79C0, 005A (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:10 APIC version 16
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: BIOS IRQ0 pin2 override ignored.
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 60000000 (gap: 50000000:aec00000)
[    0.000000] Built 1 zonelists.  Total pages: 325105
[    0.000000] Kernel command line: root=UUID=2f65bc2d-eefb-4f67-92ed-6208a5001bad ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 2079.534 MHz processor.
[   24.434609] Console: colour VGA+ 80x25
[   24.435255] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   24.435761] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   24.478512] Memory: 1287320k/1310656k available (2015k kernel code, 22024k reserved, 916k data, 364k init, 393152k highmem)
[   24.478523] virtual kernel memory layout:
[   24.478524]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   24.478526]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   24.478527]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   24.478528]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   24.478529]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   24.478531]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
[   24.478532]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
[   24.478535] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   24.478585] SLUB: Genslabs=22, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   24.558544] Calibrating delay using timer specific routine.. 4162.39 BogoMIPS (lpj=8324798)
[   24.558582] Security Framework v1.0.0 initialized
[   24.558591] SELinux:  Disabled at boot.
[   24.558609] Mount-cache hash table entries: 512
[   24.558780] CPU: After generic identify, caps: 0383fbff c1c3fbff 00000000 00000000 00000000 00000000 00000000
[   24.558791] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   24.558793] CPU: L2 Cache: 512K (64 bytes/line)
[   24.558796] CPU: After all inits, caps: 0383fbff c1c3fbff 00000000 00000420 00000000 00000000 00000000
[   24.558809] Compat vDSO mapped to ffffe000.
[   24.558824] Checking 'hlt' instruction... OK.
[   24.574702] SMP alternatives: switching to UP code
[   24.575029] Freeing SMP alternatives: 11k freed
[   24.575397] Early unpacking initramfs... done
[   24.875318] ACPI: Core revision 20070126
[   24.875418] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   24.895710] CPU0: AMD Athlon(tm) XP 2800+ stepping 00
[   24.895736] Total of 1 processors activated (4162.39 BogoMIPS).
[   24.895935] ENABLING IO-APIC IRQs
[   24.896123] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[   25.042234] Brought up 1 CPUs
[   25.042381] Booting paravirtualized kernel on bare hardware
[   25.042458] Time:  3:15:58  Date: 10/18/107
[   25.042494] NET: Registered protocol family 16
[   25.042609] EISA bus registered
[   25.042622] ACPI: bus type pci registered
[   25.043254] PCI: PCI BIOS revision 2.10 entry at 0xfb420, last bus=2
[   25.043257] PCI: Using configuration type 1
[   25.043259] Setting up standard PCI resources
[   25.045685] ACPI: EC: Look up EC in DSDT
[   25.051386] ACPI: Interpreter enabled
[   25.051390] ACPI: (supports S0 S1 S4 S5)
[   25.051406] ACPI: Using IOAPIC for interrupt routing
[   25.059737] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   25.059745] PCI: Probing PCI hardware (bus 00)
[   25.059818] PCI: nForce2 C1 Halt Disconnect fixup
[   25.060476] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   25.060639] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[   25.060874] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGPB._PRT]
[   25.101467] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   25.101624] ACPI: PCI Interrupt Link [LNK2] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   25.101778] ACPI: PCI Interrupt Link [LNK3] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   25.101933] ACPI: PCI Interrupt Link [LNK4] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   25.102085] ACPI: PCI Interrupt Link [LNK5] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   25.102244] ACPI: PCI Interrupt Link [LUBA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   25.102403] ACPI: PCI Interrupt Link [LUBB] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   25.102556] ACPI: PCI Interrupt Link [LMAC] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   25.102711] ACPI: PCI Interrupt Link [LAPU] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   25.102864] ACPI: PCI Interrupt Link [LACI] (IRQs 3 4 5 6 7 10 11 *12 14 15)
[   25.103015] ACPI: PCI Interrupt Link [LMCI] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   25.103175] ACPI: PCI Interrupt Link [LSMB] (IRQs 3 4 5 6 7 10 11 *12 14 15)
[   25.103332] ACPI: PCI Interrupt Link [LUB2] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   25.103487] ACPI: PCI Interrupt Link [LFIR] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   25.103640] ACPI: PCI Interrupt Link [L3CM] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   25.103793] ACPI: PCI Interrupt Link [LIDE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   25.103928] ACPI: PCI Interrupt Link [APC1] (IRQs *16), disabled.
[   25.104046] ACPI: PCI Interrupt Link [APC2] (IRQs *17), disabled.
[   25.104165] ACPI: PCI Interrupt Link [APC3] (IRQs *18), disabled.
[   25.104282] ACPI: PCI Interrupt Link [APC4] (IRQs *19)
[   25.104408] ACPI: PCI Interrupt Link [APCE] (IRQs *16), disabled.
[   25.104579] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22) *0
[   25.104749] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22) *0
[   25.104917] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22) *0
[   25.105085] ACPI: PCI Interrupt Link [APCI] (IRQs 20 21 22) *0, disabled.
[   25.105253] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22) *0
[   25.105422] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22) *0, disabled.
[   25.105542] ACPI: PCI Interrupt Link [APCS] (IRQs *23)
[   25.105709] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22) *0
[   25.105878] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22) *0, disabled.
[   25.106046] ACPI: PCI Interrupt Link [AP3C] (IRQs 20 21 22) *0, disabled.
[   25.106223] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22) *0, disabled.
[   25.106325] Linux Plug and Play Support v0.97 (c) Adam Belay
[   25.106338] pnp: PnP ACPI init
[   25.106346] ACPI: bus type pnp registered
[   25.110523] pnp: PnP ACPI: found 14 devices
[   25.110525] ACPI: ACPI bus type pnp unregistered
[   25.110530] PnPBIOS: Disabled by ACPI PNP
[   25.110589] PCI: Using ACPI for IRQ routing
[   25.110594] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   25.144557] NET: Registered protocol family 8
[   25.144560] NET: Registered protocol family 20
[   25.144631] pnp: 00:00: ioport range 0x4000-0x407f has been reserved
[   25.144634] pnp: 00:00: ioport range 0x4080-0x40ff has been reserved
[   25.144637] pnp: 00:00: ioport range 0x4400-0x447f has been reserved
[   25.144640] pnp: 00:00: ioport range 0x4480-0x44ff has been reserved
[   25.144642] pnp: 00:00: ioport range 0x4200-0x427f has been reserved
[   25.144645] pnp: 00:00: ioport range 0x4280-0x42ff has been reserved
[   25.144649] pnp: 00:01: ioport range 0x5000-0x503f has been reserved
[   25.144652] pnp: 00:01: ioport range 0x5100-0x513f has been reserved
[   25.144657] pnp: 00:02: iomem range 0xce200-0xcffff has been reserved
[   25.144660] pnp: 00:02: iomem range 0xf0000-0xf7fff could not be reserved
[   25.144663] pnp: 00:02: iomem range 0xf8000-0xfbfff could not be reserved
[   25.144665] pnp: 00:02: iomem range 0xfc000-0xfffff could not be reserved
[   25.146106] Time: tsc clocksource has been installed.
[   25.174969] PCI: Bridge: 0000:00:08.0
[   25.174970]   IO window: disabled.
[   25.174975]   MEM window: disabled.
[   25.174978]   PREFETCH window: disabled.
[   25.174985] PCI: Bridge: 0000:00:1e.0
[   25.174988]   IO window: c000-cfff
[   25.174992]   MEM window: e4000000-e5ffffff
[   25.174996]   PREFETCH window: d0000000-dfffffff
[   25.175007] PCI: Setting latency timer of device 0000:00:08.0 to 64
[   25.175024] NET: Registered protocol family 2
[   25.214114] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   25.214313] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[   25.216552] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   25.217365] TCP: Hash tables configured (established 131072 bind 65536)
[   25.217368] TCP reno registered
[   25.226195] checking if image is initramfs... it is
[   25.677709] Switched to high resolution mode on CPU 0
[   25.793614] Freeing initrd memory: 7104k freed
[   25.794097] audit: initializing netlink socket (disabled)
[   25.794114] audit(1195355759.048:1): initialized
[   25.794184] highmem bounce pool size: 64 pages
[   25.795980] VFS: Disk quotas dquot_6.5.1
[   25.796031] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   25.796132] io scheduler noop registered
[   25.796135] io scheduler anticipatory registered
[   25.796137] io scheduler deadline registered
[   25.796150] io scheduler cfq registered (default)
[   25.796197] Boot video device is 0000:02:00.0
[   25.796371] isapnp: Scanning for PnP cards...
[   26.150583] isapnp: No Plug & Play device found
[   26.174539] Real Time Clock Driver v1.12ac
[   26.174664] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   26.174783] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   26.174961] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   26.175539] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   26.175798] 00:0b: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   26.176582] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   26.176805] input: Macintosh mouse button emulation as /class/input/input0
[   26.176881] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[   26.176884] PNP: PS/2 controller doesn't have AUX irq; using default 12
[   26.429249] serio: i8042 KBD port at 0x60,0x64 irq 1
[   26.429444] mice: PS/2 mouse device common for all mice
[   26.429571] EISA: Probing bus 0 at eisa.0
[   26.429596] Cannot allocate resource for EISA slot 4
[   26.429599] Cannot allocate resource for EISA slot 5
[   26.429614] EISA: Detected 0 cards.
[   26.429726] TCP cubic registered
[   26.429736] NET: Registered protocol family 1
[   26.429758] Using IPI No-Shortcut mode
[   26.429945]   Magic number: 15:417:260
[   26.430003]   hash matches device ttyx2
[   26.430658] Freeing unused kernel memory: 364k freed
[   26.468982] input: AT Translated Set 2 keyboard as /class/input/input1
[   27.628129] AppArmor: AppArmor initialized<5>audit(1195355760.548:2):  type=1505 info="AppArmor initialized" pid=1218
[   27.636735] fuse init (API version 7.8)
[   27.642665] Failure registering capabilities with primary security module.
[   27.656159] ACPI: Fan [FAN] (on)
[   27.664264] ACPI: Thermal Zone [THRM] (45 C)
[   28.289533] usbcore: registered new interface driver usbfs
[   28.289566] usbcore: registered new interface driver hub
[   28.289599] usbcore: registered new device driver usb
[   28.290324] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   28.290739] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 22
[   28.290750] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [APCF] -> GSI 22 (level, high) -> IRQ 16
[   28.290765] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   28.290769] ohci_hcd 0000:00:02.0: OHCI Host Controller
[   28.291021] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[   28.291044] ohci_hcd 0000:00:02.0: irq 16, io mem 0xe6004000
[   28.323030] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.60.
[   28.344558] SCSI subsystem initialized
[   28.349495] libata version 2.21 loaded.
[   28.377397] usb usb1: configuration #1 chosen from 1 choice
[   28.377434] hub 1-0:1.0: USB hub found
[   28.377448] hub 1-0:1.0: 3 ports detected
[   28.461647] Floppy drive(s): fd0 is 1.44M
[   28.479615] ACPI: PCI Interrupt Link [APCG] enabled at IRQ 21
[   28.479627] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [APCG] -> GSI 21 (level, high) -> IRQ 17
[   28.479646] PCI: Setting latency timer of device 0000:00:02.1 to 64
[   28.479650] ohci_hcd 0000:00:02.1: OHCI Host Controller
[   28.479680] ohci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
[   28.479701] ohci_hcd 0000:00:02.1: irq 17, io mem 0xe6005000
[   28.505036] FDC 0 is a post-1991 82077
[   28.537205] usb usb2: configuration #1 chosen from 1 choice
[   28.537245] hub 2-0:1.0: USB hub found
[   28.537260] hub 2-0:1.0: 3 ports detected
[   28.639834] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 20
[   28.639847] ACPI: PCI Interrupt 0000:00:02.2[C] -> Link [APCL] -> GSI 20 (level, high) -> IRQ 18
[   28.639861] PCI: Setting latency timer of device 0000:00:02.2 to 64
[   28.639865] ehci_hcd 0000:00:02.2: EHCI Host Controller
[   28.639899] ehci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 3
[   28.639942] ehci_hcd 0000:00:02.2: debug port 1
[   28.639947] PCI: cache line size of 64 is not supported by device 0000:00:02.2
[   28.639959] ehci_hcd 0000:00:02.2: irq 18, io mem 0xe6000000
[   28.782816] usb 1-1: new full speed USB device using ohci_hcd and address 2
[   28.782846] ehci_hcd 0000:00:02.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   28.782979] usb usb3: configuration #1 chosen from 1 choice
[   28.783012] hub 3-0:1.0: USB hub found
[   28.783024] hub 3-0:1.0: 6 ports detected
[   28.887320] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 22
[   28.887327] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [APCH] -> GSI 22 (level, high) -> IRQ 16
[   28.887334] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   29.406727] eth0: forcedeth.c: subsystem: 0147b:1c02 bound to 0000:00:04.0
[   29.412167] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   29.412175] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   29.413988] NFORCE2: IDE controller at PCI slot 0000:00:09.0
[   29.414019] NFORCE2: chipset revision 162
[   29.414022] NFORCE2: not 100% native mode: will probe irqs later
[   29.414027] NFORCE2: BIOS didn't set cable bits correctly. Enabling workaround.
[   29.414030] NFORCE2: BIOS didn't set cable bits correctly. Enabling workaround.
[   29.414036] NFORCE2: 0000:00:09.0 (rev a2) UDMA133 controller
[   29.414049]     ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:DMA
[   29.414063]     ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdc:DMA, hdd:DMA
[   29.414073] Probing IDE interface ide0...
[   29.702099] hda: MAXTOR STM3250820A, ATA DISK drive
[   29.981844] hdb: MAXTOR 6L080L4, ATA DISK drive
[   30.038392] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   30.042610] Probing IDE interface ide1...
[   30.193534] usb 1-1: new full speed USB device using ohci_hcd and address 3
[   30.396789] usb 1-1: configuration #1 chosen from 1 choice
[   30.399744] hub 1-1:1.0: USB hub found
[   30.402690] hub 1-1:1.0: 4 ports detected
[   30.777124] hdc: CREATIVE CD5233E-N, ATAPI CD/DVD-ROM drive
[   30.824963] usb 1-2: new low speed USB device using ohci_hcd and address 4
[   31.038273] usb 1-2: configuration #1 chosen from 1 choice
[   31.344499] usb 2-1: new full speed USB device using ohci_hcd and address 2
[   31.560414] hdd: DVD-RW IDE1008, ATAPI CD/DVD-ROM drive
[   31.565840] usb 2-1: configuration #1 chosen from 1 choice
[   31.616728] ide1 at 0x170-0x177,0x376 on irq 15
[   31.625213] hda: max request size: 512KiB
[   31.663045] hda: 488397168 sectors (250059 MB) w/8192KiB Cache, CHS=30401/255/63, UDMA(100)
[   31.687413] hda: cache flushes supported
[   31.687479]  hda: hda1 hda2 hda3 hda4
[   31.725080] hdb: max request size: 128KiB
[   31.725217] hdb: 156355584 sectors (80054 MB) w/1819KiB Cache, CHS=65535/16/63, UDMA(133)
[   31.725395] hdb: cache flushes supported
[   31.725415]  hdb: hdb1 < hdb5 >
[   31.752347] hdc: ATAPI 52X CD-ROM drive, 128kB Cache, UDMA(33)
[   31.752357] Uniform CD-ROM driver Revision: 3.20
[   31.772720] hdd: ATAPI 40X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache<4>hdd: drive side 80-wire cable detection failed, limiting max speed to UDMA33
[   31.772730] 
[   31.785642] usb 1-1.3: new full speed USB device using ohci_hcd and address 5
[   31.893640] usb 1-1.3: configuration #1 chosen from 1 choice
[   32.105354] usb 1-1.4: new full speed USB device using ohci_hcd and address 6
[   32.211594] Attempting manual resume
[   32.211599] swsusp: Resume From Partition 3:3
[   32.211601] PM: Checking swsusp image.
[   32.211782] PM: Resume from disk failed.
[   32.228381] usb 1-1.4: configuration #1 chosen from 1 choice
[   32.241273] usbcore: registered new interface driver hiddev
[   32.248536] input: Microsoft Microsoft 5-Button Mouse with IntelliEye(TM) as /class/input/input2
[   32.248561] input: USB HID v1.10 Mouse [Microsoft Microsoft 5-Button Mouse with IntelliEye(TM)] on usb-0000:00:02.0-2
[   32.258313] hiddev96: USB HID v1.00 Device [Lexmark  2300 Series] on usb-0000:00:02.0-1.4
[   32.258336] usbcore: registered new interface driver usbhid
[   32.258341] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   32.304727] kjournald starting.  Commit interval 5 seconds
[   32.304742] EXT3-fs: mounted filesystem with ordered data mode.
[   39.245827] Linux agpgart interface v0.102 (c) Dave Jones
[   39.321181] agpgart: Detected NVIDIA nForce2 chipset
[   39.326219] agpgart: AGP aperture is 64M @ 0xe0000000
[   39.375760] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x5000
[   39.375793] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x5100
[   39.919507] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   39.921279] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   39.950976] Linux video capture interface: v2.00
[   39.989976] quickcam: QuickCam USB camera found (driver version QuickCam USB 0.6.6 $Date: 2006/11/04 08:38:14 $)
[   39.989983] quickcam: Kernel:2.6.22-14-generic bus:1 class:FF subclass:FF vendor:046D product:0840
[   40.003209] quickcam: Sensor HDCS-1000/1100 detected
[   40.009324] quickcam: Registered device: /dev/video0
[   40.009361] usbcore: registered new interface driver quickcam
[   40.342994] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 6 if 1 alt 0 proto 2 vid 0x043D pid 0x00BB
[   40.343022] usbcore: registered new interface driver usblp
[   40.343026] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[   40.508534] usbcore: registered new interface driver xpad
[   40.508541] /build/buildd/linux-source-2.6.22-2.6.22/drivers/input/joystick/xpad.c: driver for Xbox controllers v0.1.6
[   40.831369] Bluetooth: Core ver 2.11
[   40.831447] NET: Registered protocol family 31
[   40.831449] Bluetooth: HCI device and connection manager initialized
[   40.831454] Bluetooth: HCI socket layer initialized
[   40.871528] parport_pc 00:0c: reported by Plug and Play ACPI
[   40.871653] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   40.883683] input: PC Speaker as /class/input/input3
[   40.962923] Bluetooth: HCI USB driver ver 2.9
[   40.964796] usbcore: registered new interface driver hci_usb
[   41.340238] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 21
[   41.340246] ACPI: PCI Interrupt 0000:00:06.0[A] -> Link [APCJ] -> GSI 21 (level, high) -> IRQ 17
[   41.340274] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   41.663133] intel8x0_measure_ac97_clock: measured 52750 usecs
[   41.663138] intel8x0: clocking to 47475
[   42.225360] lp0: using parport0 (interrupt-driven).
[   42.263236] Adding 1044216k swap on /dev/hda3.  Priority:-1 extents:1 across:1044216k
[   42.594938] EXT3 FS on hda2, internal journal
[   43.317771] kjournald starting.  Commit interval 5 seconds
[   43.317931] EXT3 FS on hda4, internal journal
[   43.317937] EXT3-fs: mounted filesystem with ordered data mode.
[   43.326178] kjournald starting.  Commit interval 5 seconds
[   43.333796] EXT3 FS on hdb5, internal journal
[   43.333799] EXT3-fs: mounted filesystem with ordered data mode.
[   43.360086] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!


==========/bin/dmesg==========
[    0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000004fff0000 (usable)
[    0.000000]  BIOS-e820: 000000004fff0000 - 000000004fff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000004fff3000 - 0000000050000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] 383MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 327664) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   327664
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   327664
[    0.000000] On node 0 totalpages: 327664
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 767 pages used for memmap
[    0.000000]   HighMem zone: 97521 pages, LIFO batch:31
[    0.000000] DMI 2.2 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F6B00 checksum 0
[    0.000000] ACPI: RSDP 000F6B00, 0014 (r0 Nvidia)
[    0.000000] ACPI: RSDT 4FFF3000, 002C (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP 4FFF3040, 0074 (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT 4FFF30C0, 48E8 (r1 NVIDIA AWRDACPI     1000 MSFT  100000D)
[    0.000000] ACPI: FACS 4FFF0000, 0040
[    0.000000] ACPI: APIC 4FFF79C0, 005A (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:10 APIC version 16
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: BIOS IRQ0 pin2 override ignored.
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 60000000 (gap: 50000000:aec00000)
[    0.000000] Built 1 zonelists.  Total pages: 325105
[    0.000000] Kernel command line: root=UUID=2f65bc2d-eefb-4f67-92ed-6208a5001bad ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 2079.534 MHz processor.
[   24.434609] Console: colour VGA+ 80x25
[   24.435255] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   24.435761] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   24.478512] Memory: 1287320k/1310656k available (2015k kernel code, 22024k reserved, 916k data, 364k init, 393152k highmem)
[   24.478523] virtual kernel memory layout:
[   24.478524]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   24.478526]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   24.478527]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   24.478528]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   24.478529]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   24.478531]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
[   24.478532]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
[   24.478535] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   24.478585] SLUB: Genslabs=22, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   24.558544] Calibrating delay using timer specific routine.. 4162.39 BogoMIPS (lpj=8324798)
[   24.558582] Security Framework v1.0.0 initialized
[   24.558591] SELinux:  Disabled at boot.
[   24.558609] Mount-cache hash table entries: 512
[   24.558780] CPU: After generic identify, caps: 0383fbff c1c3fbff 00000000 00000000 00000000 00000000 00000000
[   24.558791] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   24.558793] CPU: L2 Cache: 512K (64 bytes/line)
[   24.558796] CPU: After all inits, caps: 0383fbff c1c3fbff 00000000 00000420 00000000 00000000 00000000
[   24.558809] Compat vDSO mapped to ffffe000.
[   24.558824] Checking 'hlt' instruction... OK.
[   24.574702] SMP alternatives: switching to UP code
[   24.575029] Freeing SMP alternatives: 11k freed
[   24.575397] Early unpacking initramfs... done
[   24.875318] ACPI: Core revision 20070126
[   24.875418] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   24.895710] CPU0: AMD Athlon(tm) XP 2800+ stepping 00
[   24.895736] Total of 1 processors activated (4162.39 BogoMIPS).
[   24.895935] ENABLING IO-APIC IRQs
[   24.896123] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[   25.042234] Brought up 1 CPUs
[   25.042381] Booting paravirtualized kernel on bare hardware
[   25.042458] Time:  3:15:58  Date: 10/18/107
[   25.042494] NET: Registered protocol family 16
[   25.042609] EISA bus registered
[   25.042622] ACPI: bus type pci registered
[   25.043254] PCI: PCI BIOS revision 2.10 entry at 0xfb420, last bus=2
[   25.043257] PCI: Using configuration type 1
[   25.043259] Setting up standard PCI resources
[   25.045685] ACPI: EC: Look up EC in DSDT
[   25.051386] ACPI: Interpreter enabled
[   25.051390] ACPI: (supports S0 S1 S4 S5)
[   25.051406] ACPI: Using IOAPIC for interrupt routing
[   25.059737] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   25.059745] PCI: Probing PCI hardware (bus 00)
[   25.059818] PCI: nForce2 C1 Halt Disconnect fixup
[   25.060476] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   25.060639] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[   25.060874] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGPB._PRT]
[   25.101467] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   25.101624] ACPI: PCI Interrupt Link [LNK2] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   25.101778] ACPI: PCI Interrupt Link [LNK3] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   25.101933] ACPI: PCI Interrupt Link [LNK4] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   25.102085] ACPI: PCI Interrupt Link [LNK5] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   25.102244] ACPI: PCI Interrupt Link [LUBA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   25.102403] ACPI: PCI Interrupt Link [LUBB] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   25.102556] ACPI: PCI Interrupt Link [LMAC] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   25.102711] ACPI: PCI Interrupt Link [LAPU] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   25.102864] ACPI: PCI Interrupt Link [LACI] (IRQs 3 4 5 6 7 10 11 *12 14 15)
[   25.103015] ACPI: PCI Interrupt Link [LMCI] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   25.103175] ACPI: PCI Interrupt Link [LSMB] (IRQs 3 4 5 6 7 10 11 *12 14 15)
[   25.103332] ACPI: PCI Interrupt Link [LUB2] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   25.103487] ACPI: PCI Interrupt Link [LFIR] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   25.103640] ACPI: PCI Interrupt Link [L3CM] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   25.103793] ACPI: PCI Interrupt Link [LIDE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   25.103928] ACPI: PCI Interrupt Link [APC1] (IRQs *16), disabled.
[   25.104046] ACPI: PCI Interrupt Link [APC2] (IRQs *17), disabled.
[   25.104165] ACPI: PCI Interrupt Link [APC3] (IRQs *18), disabled.
[   25.104282] ACPI: PCI Interrupt Link [APC4] (IRQs *19)
[   25.104408] ACPI: PCI Interrupt Link [APCE] (IRQs *16), disabled.
[   25.104579] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22) *0
[   25.104749] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22) *0
[   25.104917] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22) *0
[   25.105085] ACPI: PCI Interrupt Link [APCI] (IRQs 20 21 22) *0, disabled.
[   25.105253] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22) *0
[   25.105422] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22) *0, disabled.
[   25.105542] ACPI: PCI Interrupt Link [APCS] (IRQs *23)
[   25.105709] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22) *0
[   25.105878] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22) *0, disabled.
[   25.106046] ACPI: PCI Interrupt Link [AP3C] (IRQs 20 21 22) *0, disabled.
[   25.106223] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22) *0, disabled.
[   25.106325] Linux Plug and Play Support v0.97 (c) Adam Belay
[   25.106338] pnp: PnP ACPI init
[   25.106346] ACPI: bus type pnp registered
[   25.110523] pnp: PnP ACPI: found 14 devices
[   25.110525] ACPI: ACPI bus type pnp unregistered
[   25.110530] PnPBIOS: Disabled by ACPI PNP
[   25.110589] PCI: Using ACPI for IRQ routing
[   25.110594] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   25.144557] NET: Registered protocol family 8
[   25.144560] NET: Registered protocol family 20
[   25.144631] pnp: 00:00: ioport range 0x4000-0x407f has been reserved
[   25.144634] pnp: 00:00: ioport range 0x4080-0x40ff has been reserved
[   25.144637] pnp: 00:00: ioport range 0x4400-0x447f has been reserved
[   25.144640] pnp: 00:00: ioport range 0x4480-0x44ff has been reserved
[   25.144642] pnp: 00:00: ioport range 0x4200-0x427f has been reserved
[   25.144645] pnp: 00:00: ioport range 0x4280-0x42ff has been reserved
[   25.144649] pnp: 00:01: ioport range 0x5000-0x503f has been reserved
[   25.144652] pnp: 00:01: ioport range 0x5100-0x513f has been reserved
[   25.144657] pnp: 00:02: iomem range 0xce200-0xcffff has been reserved
[   25.144660] pnp: 00:02: iomem range 0xf0000-0xf7fff could not be reserved
[   25.144663] pnp: 00:02: iomem range 0xf8000-0xfbfff could not be reserved
[   25.144665] pnp: 00:02: iomem range 0xfc000-0xfffff could not be reserved
[   25.146106] Time: tsc clocksource has been installed.
[   25.174969] PCI: Bridge: 0000:00:08.0
[   25.174970]   IO window: disabled.
[   25.174975]   MEM window: disabled.
[   25.174978]   PREFETCH window: disabled.
[   25.174985] PCI: Bridge: 0000:00:1e.0
[   25.174988]   IO window: c000-cfff
[   25.174992]   MEM window: e4000000-e5ffffff
[   25.174996]   PREFETCH window: d0000000-dfffffff
[   25.175007] PCI: Setting latency timer of device 0000:00:08.0 to 64
[   25.175024] NET: Registered protocol family 2
[   25.214114] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   25.214313] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[   25.216552] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   25.217365] TCP: Hash tables configured (established 131072 bind 65536)
[   25.217368] TCP reno registered
[   25.226195] checking if image is initramfs... it is
[   25.677709] Switched to high resolution mode on CPU 0
[   25.793614] Freeing initrd memory: 7104k freed
[   25.794097] audit: initializing netlink socket (disabled)
[   25.794114] audit(1195355759.048:1): initialized
[   25.794184] highmem bounce pool size: 64 pages
[   25.795980] VFS: Disk quotas dquot_6.5.1
[   25.796031] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   25.796132] io scheduler noop registered
[   25.796135] io scheduler anticipatory registered
[   25.796137] io scheduler deadline registered
[   25.796150] io scheduler cfq registered (default)
[   25.796197] Boot video device is 0000:02:00.0
[   25.796371] isapnp: Scanning for PnP cards...
[   26.150583] isapnp: No Plug & Play device found
[   26.174539] Real Time Clock Driver v1.12ac
[   26.174664] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   26.174783] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   26.174961] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   26.175539] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   26.175798] 00:0b: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   26.176582] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   26.176805] input: Macintosh mouse button emulation as /class/input/input0
[   26.176881] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[   26.176884] PNP: PS/2 controller doesn't have AUX irq; using default 12
[   26.429249] serio: i8042 KBD port at 0x60,0x64 irq 1
[   26.429444] mice: PS/2 mouse device common for all mice
[   26.429571] EISA: Probing bus 0 at eisa.0
[   26.429596] Cannot allocate resource for EISA slot 4
[   26.429599] Cannot allocate resource for EISA slot 5
[   26.429614] EISA: Detected 0 cards.
[   26.429726] TCP cubic registered
[   26.429736] NET: Registered protocol family 1
[   26.429758] Using IPI No-Shortcut mode
[   26.429945]   Magic number: 15:417:260
[   26.430003]   hash matches device ttyx2
[   26.430658] Freeing unused kernel memory: 364k freed
[   26.468982] input: AT Translated Set 2 keyboard as /class/input/input1
[   27.628129] AppArmor: AppArmor initialized<5>audit(1195355760.548:2):  type=1505 info="AppArmor initialized" pid=1218
[   27.636735] fuse init (API version 7.8)
[   27.642665] Failure registering capabilities with primary security module.
[   27.656159] ACPI: Fan [FAN] (on)
[   27.664264] ACPI: Thermal Zone [THRM] (45 C)
[   28.289533] usbcore: registered new interface driver usbfs
[   28.289566] usbcore: registered new interface driver hub
[   28.289599] usbcore: registered new device driver usb
[   28.290324] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   28.290739] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 22
[   28.290750] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [APCF] -> GSI 22 (level, high) -> IRQ 16
[   28.290765] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   28.290769] ohci_hcd 0000:00:02.0: OHCI Host Controller
[   28.291021] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[   28.291044] ohci_hcd 0000:00:02.0: irq 16, io mem 0xe6004000
[   28.323030] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.60.
[   28.344558] SCSI subsystem initialized
[   28.349495] libata version 2.21 loaded.
[   28.377397] usb usb1: configuration #1 chosen from 1 choice
[   28.377434] hub 1-0:1.0: USB hub found
[   28.377448] hub 1-0:1.0: 3 ports detected
[   28.461647] Floppy drive(s): fd0 is 1.44M
[   28.479615] ACPI: PCI Interrupt Link [APCG] enabled at IRQ 21
[   28.479627] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [APCG] -> GSI 21 (level, high) -> IRQ 17
[   28.479646] PCI: Setting latency timer of device 0000:00:02.1 to 64
[   28.479650] ohci_hcd 0000:00:02.1: OHCI Host Controller
[   28.479680] ohci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
[   28.479701] ohci_hcd 0000:00:02.1: irq 17, io mem 0xe6005000
[   28.505036] FDC 0 is a post-1991 82077
[   28.537205] usb usb2: configuration #1 chosen from 1 choice
[   28.537245] hub 2-0:1.0: USB hub found
[   28.537260] hub 2-0:1.0: 3 ports detected
[   28.639834] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 20
[   28.639847] ACPI: PCI Interrupt 0000:00:02.2[C] -> Link [APCL] -> GSI 20 (level, high) -> IRQ 18
[   28.639861] PCI: Setting latency timer of device 0000:00:02.2 to 64
[   28.639865] ehci_hcd 0000:00:02.2: EHCI Host Controller
[   28.639899] ehci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 3
[   28.639942] ehci_hcd 0000:00:02.2: debug port 1
[   28.639947] PCI: cache line size of 64 is not supported by device 0000:00:02.2
[   28.639959] ehci_hcd 0000:00:02.2: irq 18, io mem 0xe6000000
[   28.782816] usb 1-1: new full speed USB device using ohci_hcd and address 2
[   28.782846] ehci_hcd 0000:00:02.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   28.782979] usb usb3: configuration #1 chosen from 1 choice
[   28.783012] hub 3-0:1.0: USB hub found
[   28.783024] hub 3-0:1.0: 6 ports detected
[   28.887320] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 22
[   28.887327] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [APCH] -> GSI 22 (level, high) -> IRQ 16
[   28.887334] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   29.406727] eth0: forcedeth.c: subsystem: 0147b:1c02 bound to 0000:00:04.0
[   29.412167] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   29.412175] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   29.413988] NFORCE2: IDE controller at PCI slot 0000:00:09.0
[   29.414019] NFORCE2: chipset revision 162
[   29.414022] NFORCE2: not 100% native mode: will probe irqs later
[   29.414027] NFORCE2: BIOS didn't set cable bits correctly. Enabling workaround.
[   29.414030] NFORCE2: BIOS didn't set cable bits correctly. Enabling workaround.
[   29.414036] NFORCE2: 0000:00:09.0 (rev a2) UDMA133 controller
[   29.414049]     ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:DMA
[   29.414063]     ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdc:DMA, hdd:DMA
[   29.414073] Probing IDE interface ide0...
[   29.702099] hda: MAXTOR STM3250820A, ATA DISK drive
[   29.981844] hdb: MAXTOR 6L080L4, ATA DISK drive
[   30.038392] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   30.042610] Probing IDE interface ide1...
[   30.193534] usb 1-1: new full speed USB device using ohci_hcd and address 3
[   30.396789] usb 1-1: configuration #1 chosen from 1 choice
[   30.399744] hub 1-1:1.0: USB hub found
[   30.402690] hub 1-1:1.0: 4 ports detected
[   30.777124] hdc: CREATIVE CD5233E-N, ATAPI CD/DVD-ROM drive
[   30.824963] usb 1-2: new low speed USB device using ohci_hcd and address 4
[   31.038273] usb 1-2: configuration #1 chosen from 1 choice
[   31.344499] usb 2-1: new full speed USB device using ohci_hcd and address 2
[   31.560414] hdd: DVD-RW IDE1008, ATAPI CD/DVD-ROM drive
[   31.565840] usb 2-1: configuration #1 chosen from 1 choice
[   31.616728] ide1 at 0x170-0x177,0x376 on irq 15
[   31.625213] hda: max request size: 512KiB
[   31.663045] hda: 488397168 sectors (250059 MB) w/8192KiB Cache, CHS=30401/255/63, UDMA(100)
[   31.687413] hda: cache flushes supported
[   31.687479]  hda: hda1 hda2 hda3 hda4
[   31.725080] hdb: max request size: 128KiB
[   31.725217] hdb: 156355584 sectors (80054 MB) w/1819KiB Cache, CHS=65535/16/63, UDMA(133)
[   31.725395] hdb: cache flushes supported
[   31.725415]  hdb: hdb1 < hdb5 >
[   31.752347] hdc: ATAPI 52X CD-ROM drive, 128kB Cache, UDMA(33)
[   31.752357] Uniform CD-ROM driver Revision: 3.20
[   31.772720] hdd: ATAPI 40X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache<4>hdd: drive side 80-wire cable detection failed, limiting max speed to UDMA33
[   31.772730] 
[   31.785642] usb 1-1.3: new full speed USB device using ohci_hcd and address 5
[   31.893640] usb 1-1.3: configuration #1 chosen from 1 choice
[   32.105354] usb 1-1.4: new full speed USB device using ohci_hcd and address 6
[   32.211594] Attempting manual resume
[   32.211599] swsusp: Resume From Partition 3:3
[   32.211601] PM: Checking swsusp image.
[   32.211782] PM: Resume from disk failed.
[   32.228381] usb 1-1.4: configuration #1 chosen from 1 choice
[   32.241273] usbcore: registered new interface driver hiddev
[   32.248536] input: Microsoft Microsoft 5-Button Mouse with IntelliEye(TM) as /class/input/input2
[   32.248561] input: USB HID v1.10 Mouse [Microsoft Microsoft 5-Button Mouse with IntelliEye(TM)] on usb-0000:00:02.0-2
[   32.258313] hiddev96: USB HID v1.00 Device [Lexmark  2300 Series] on usb-0000:00:02.0-1.4
[   32.258336] usbcore: registered new interface driver usbhid
[   32.258341] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   32.304727] kjournald starting.  Commit interval 5 seconds
[   32.304742] EXT3-fs: mounted filesystem with ordered data mode.
[   39.245827] Linux agpgart interface v0.102 (c) Dave Jones
[   39.321181] agpgart: Detected NVIDIA nForce2 chipset
[   39.326219] agpgart: AGP aperture is 64M @ 0xe0000000
[   39.375760] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x5000
[   39.375793] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x5100
[   39.919507] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   39.921279] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   39.950976] Linux video capture interface: v2.00
[   39.989976] quickcam: QuickCam USB camera found (driver version QuickCam USB 0.6.6 $Date: 2006/11/04 08:38:14 $)
[   39.989983] quickcam: Kernel:2.6.22-14-generic bus:1 class:FF subclass:FF vendor:046D product:0840
[   40.003209] quickcam: Sensor HDCS-1000/1100 detected
[   40.009324] quickcam: Registered device: /dev/video0
[   40.009361] usbcore: registered new interface driver quickcam
[   40.342994] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 6 if 1 alt 0 proto 2 vid 0x043D pid 0x00BB
[   40.343022] usbcore: registered new interface driver usblp
[   40.343026] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[   40.508534] usbcore: registered new interface driver xpad
[   40.508541] /build/buildd/linux-source-2.6.22-2.6.22/drivers/input/joystick/xpad.c: driver for Xbox controllers v0.1.6
[   40.831369] Bluetooth: Core ver 2.11
[   40.831447] NET: Registered protocol family 31
[   40.831449] Bluetooth: HCI device and connection manager initialized
[   40.831454] Bluetooth: HCI socket layer initialized
[   40.871528] parport_pc 00:0c: reported by Plug and Play ACPI
[   40.871653] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   40.883683] input: PC Speaker as /class/input/input3
[   40.962923] Bluetooth: HCI USB driver ver 2.9
[   40.964796] usbcore: registered new interface driver hci_usb
[   41.340238] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 21
[   41.340246] ACPI: PCI Interrupt 0000:00:06.0[A] -> Link [APCJ] -> GSI 21 (level, high) -> IRQ 17
[   41.340274] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   41.663133] intel8x0_measure_ac97_clock: measured 52750 usecs
[   41.663138] intel8x0: clocking to 47475
[   42.225360] lp0: using parport0 (interrupt-driven).
[   42.263236] Adding 1044216k swap on /dev/hda3.  Priority:-1 extents:1 across:1044216k
[   42.594938] EXT3 FS on hda2, internal journal
[   43.317771] kjournald starting.  Commit interval 5 seconds
[   43.317931] EXT3 FS on hda4, internal journal
[   43.317937] EXT3-fs: mounted filesystem with ordered data mode.
[   43.326178] kjournald starting.  Commit interval 5 seconds
[   43.333796] EXT3 FS on hdb5, internal journal
[   43.333799] EXT3-fs: mounted filesystem with ordered data mode.
[   43.360086] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[   44.258868] No dock devices found.
[   44.345523] input: Power Button (FF) as /class/input/input4
[   44.350322] ACPI: Power Button (FF) [PWRF]
[   44.386412] input: Power Button (CM) as /class/input/input5
[   44.391187] ACPI: Power Button (CM) [PWRB]
[   47.941262] ppdev: user-space parallel port driver
[   47.966658] [drm] Initialized drm 1.1.0 20060810
[   48.003331] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[   48.003346] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [APC4] -> GSI 19 (level, high) -> IRQ 19
[   48.008015] [drm] Initialized radeon 1.27.0 20060524 on minor 0
[   48.359655] audit(1195355782.012:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5145 profile="/usr/sbin/cupsd"
[   49.177108] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[   49.177231] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[   49.177347] agpgart: Putting AGP V2 device at 0000:02:00.0 into 4x mode
[   49.304077] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   49.304085] apm: overridden by ACPI.
[   49.432235] [drm] Setting GART location based on new memory map
[   49.432249] [drm] Loading R200 Microcode
[   49.432299] [drm] writeback test succeeded in 1 usecs
[   60.717562] Failure registering capabilities with primary security module.
[   61.146331] Bluetooth: L2CAP ver 2.8
[   61.146337] Bluetooth: L2CAP socket layer initialized
[   61.169952] Bluetooth: RFCOMM socket layer initialized
[   61.170055] Bluetooth: RFCOMM TTY layer initialized
[   61.170058] Bluetooth: RFCOMM ver 1.8
[   65.734899] NET: Registered protocol family 17
[   80.276630] NET: Registered protocol family 10
[   80.276825] lo: Disabled Privacy Extensions
[   91.202220] eth0: no IPv6 routers present


==========/sbin/lsmod==========
Module                  Size  Used by
ipv6                  273892  8 
af_packet              24840  2 
binfmt_misc            12936  1 
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
radeon                125472  2 
drm                    83348  3 radeon
ppdev                  10244  0 
cpufreq_stats           7232  0 
cpufreq_userspace       5280  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9612  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     8072  0 
video                  18060  0 
sbs                    19592  0 
ac                      6148  0 
container               5504  0 
button                  8976  0 
dock                   10656  0 
battery                11012  0 
nls_utf8                3072  1 
nls_cp437               6784  1 
vfat                   14080  1 
fat                    54300  1 vfat
lp                     12580  0 
snd_intel8x0           34972  1 
snd_ac97_codec        100644  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44672  0 
snd_pcm                80388  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_mixer_oss          17664  1 snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
hci_usb                18332  2 
pcspkr                  4224  0 
parport_pc             37412  1 
parport                37448  3 ppdev,lp,parport_pc
bluetooth              57060  7 rfcomm,l2cap,hci_usb
snd                    54660  12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_pcm,snd_mixer_oss,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
xpad                    9988  0 
usblp                  15104  0 
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
quickcam               73124  0 
videodev               29312  1 quickcam
v4l2_common            18432  1 videodev
v4l1_compat            15364  1 videodev
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
i2c_nforce2             7040  0 
i2c_core               26112  1 i2c_nforce2
nvidia_agp              9756  1 
agpgart                35016  2 drm,nvidia_agp
evdev                  11136  3 
ext3                  133896  3 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
ide_cd                 32672  0 
cdrom                  37536  1 ide_cd
ide_disk               18560  7 
usbhid                 29536  0 
hid                    28928  1 usbhid
amd74xx                15260  0 [permanent]
ide_core              116804  3 ide_cd,ide_disk,amd74xx
floppy                 60004  0 
ata_generic             8452  0 
libata                125168  1 ata_generic
scsi_mod              147084  1 libata
forcedeth              51592  0 
ehci_hcd               36492  0 
ohci_hcd               22916  0 
usbcore               138632  8 hci_usb,xpad,usblp,quickcam,usbhid,ehci_hcd,ohci_hcd
thermal                14344  0 
processor              32072  1 thermal
fan                     5764  0 
fuse                   47124  1 
apparmor               40728  0 
commoncap               8320  1 apparmor

```

Now what?

---

### Post by banewman on 2007-11-18
In a terminal type - 
sudo dpkg-reconfigure xserver-xorg
accept the defaults as presented except the video card driver - scroll through for the one that seems best to match your card ( they sometimes have less then obvious names ).
After that is finished press   cntrl-alt-bksp   to restart X and you should be right. :)

---

### Post by Joedude on 2007-11-18
Thanx, that worked a treat~!

well, in the process, I found out the R200 is the driver for the Radeon 8500LE...oops RIF (Reading is Fundumbmental)

I made it all the way through, and changed some things I wanted to anyway...So now I have the right driver...I still can't get the control up to adjust the the display properties...

On second thought....now I can't enable the desktop effects...hmmm.....where to go now....even after changing everything back

GREAT!!! now a reboot gets me this:

[img]http://img147.imageshack.us/img147/9682/screenshotxsessionmanaglq2.png[/img]

And I can't see any of my other drives...it's like fstab was erased....


OK, the other drives are back...however, I still can not enable the  desktop effects...hehe, can you say poster child for Murphy's law?

---

### Post by Joedude on 2007-11-18
anybody?

---

