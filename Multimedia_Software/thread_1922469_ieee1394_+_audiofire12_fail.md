---
title: "ieee1394 + audiofire12 fail"
date: 2012-02-08
forum: Multimedia Software
---

### Post by david.medine on 2012-02-08
I have been trying to figure this out for a couple days now and I can't drum up any previous posts that address this issue.

I have an audiofire12 and Ubuntu 11.10 and xfce. Everything looks like it should work, but it doesn't. When I run
```

ffado-diag

```I get something that looks very good:
```

FFADO diagnostic utility 2.999.0-
============================
(C) 2008 Pieter Palmers
    2009-2010 Arnold Krille


=== CHECK ===
 Base system...
  kernel version............ 3.0.0-15-generic
  old 1394 stack present.... False
  old 1394 stack loaded..... False
  old 1394 stack active..... False
  new 1394 stack present.... True
  new 1394 stack loaded..... True
  new 1394 stack active..... True
  /dev/raw1394 node present. False
 Prerequisites (dynamic at run-time)...
   gcc ............... gcc (Ubuntu/Linaro 4.6.1-9ubuntu3) 4.6.1
   g++ ............... g++ (Ubuntu/Linaro 4.6.1-9ubuntu3) 4.6.1
   PyQt4 (by pyuic4) . sh: pyuic4: not found
   jackd ............. no message buffer overruns
     path ............ /usr/bin/jackd
     flags ...........  -ljack  
   libraw1394 ........ 2.0.7
     flags ...........  -lraw1394  
   libavc1394 ........ 0.5.3
     flags ...........  -lavc1394 -lrom1394 -lraw1394  
   libiec61883 ....... 1.2.0
     flags ...........  -liec61883 -lraw1394  
   libxml++-2.6 ...... 2.34.1
     flags ........... -pthread -I/usr/include/glib-2.0 -I/usr/lib
/x86_64-linux-gnu/glib-2.0/include -I/usr/include/libxml++-2.6 -I/
usr/lib/libxml++-2.6/include -I/usr/include/libxml2 -I/usr/include
/glibmm-2.4 -I/usr/lib/glibmm-2.4/include -I/usr/include/sigc++-2.
0 -I/usr/lib/sigc++-2.0/include  -pthread -lxml++-2.6 -lxml2 -lgli
bmm-2.4 -lgobject-2.0 -lsigc-2.0 -lgthread-2.0 -lrt -lglib-2.0  
   dbus-1 ............ 1.4.14
     flags ........... -I/usr/include/dbus-1.0 -I/usr/lib/x86_64-l
inux-gnu/dbus-1.0/include  -ldbus-1 -lpthread -lrt  
 Prerequisites (static at compile-time)...
   gcc ............... gcc (Ubuntu/Linaro 4.6.1-9ubuntu3) 4.6.1
   g++ ............... g++ (Ubuntu/Linaro 4.6.1-9ubuntu3) 4.6.1
   PyQt4 (by pyuic4) . Python User Interface Compiler 4.8.5 for Qt
 version 4.7.3
   jackd ............. sh: jackd: not found
     path ............ 
     flags ........... Package jack was not found in the pkg-confi
g search path.
   libraw1394 ........ 2.0.7
     flags ...........  -lraw1394  
   libavc1394 ........ Package libavc1394 was not found in the pkg
-config search path.
     flags ........... Package libavc1394 was not found in the pkg
-config search path.
   libiec61883 ....... 1.2.0
     flags ...........  -liec61883 -lraw1394  
   libxml++-2.6 ...... 2.34.1
     flags ........... -pthread -I/usr/include/glib-2.0 -I/usr/lib
/x86_64-linux-gnu/glib-2.0/include -I/usr/include/libxml++-2.6 -I/
usr/lib/libxml++-2.6/include -I/usr/include/libxml2 -I/usr/include
/glibmm-2.4 -I/usr/lib/glibmm-2.4/include -I/usr/include/sigc++-2.
0 -I/usr/lib/sigc++-2.0/include  -pthread -lxml++-2.6 -lxml2 -lgli
bmm-2.4 -lgobject-2.0 -lsigc-2.0 -lgthread-2.0 -lrt -lglib-2.0  
   dbus-1 ............ 1.4.14
     flags ........... -I/usr/include/dbus-1.0 -I/usr/lib/x86_64-l
inux-gnu/dbus-1.0/include  -ldbus-1 -lpthread -lrt  
 Hardware...
   Host controllers:
03:0e.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB43AB23 I
EEE-1394a-2000 Controller (PHY/Link) [104c:8024] (prog-if 10 [OHCI
])
    Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard [1
458:1000]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop
- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >T
Abort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32 (500ns min, 1000ns max), Cache Line Size: 4 by
tes
    Interrupt: pin A routed to IRQ 22
    Region 0: Memory at fddff000 (32-bit, non-prefetchable) [s
ize=2K]
    Region 1: Memory at fddf8000 (32-bit, non-prefetchable) [s
ize=16K]
    Capabilities: <access denied>
    Kernel driver in use: firewire_ohci
    Kernel modules: firewire-ohci

   CPU info:
Architecture:          x86_64
CPU op-mode(s):        32-bit, 64-bit
Byte Order:            Little Endian
CPU(s):                4
On-line CPU(s) list:   0-3
Thread(s) per core:    1
Core(s) per socket:    4
CPU socket(s):         1
NUMA node(s):          1
Vendor ID:             AuthenticAMD
CPU family:            16
Model:                 4
Stepping:              3
CPU MHz:               800.000
BogoMIPS:              6830.93
Virtualization:        AMD-V
L1d cache:             64K
L1i cache:             64K
L2 cache:              512K
L3 cache:              6144K
NUMA node0 CPU(s):     0-3
 Configuration...
  IRQ information
Hardware Interrupts:
--------------------
 IRQ    0: PID:  None, count:   [41, 41, 41, 41], Sched None (prio
rity None), drivers: ['timer']
 IRQ    1: PID:  None, count:       [0, 0, 0, 0], Sched None (prio
rity None), drivers: ['i8042']
 IRQ    6: PID:  None, count:       [0, 0, 0, 0], Sched None (prio
rity None), drivers: ['floppy']
 IRQ    7: PID:  None, count:       [1, 1, 1, 1], Sched None (prio
rity None), drivers: ['parport0']
 IRQ    8: PID:  None, count:       [0, 0, 0, 0], Sched None (prio
rity None), drivers: ['rtc0']
 IRQ    9: PID:  None, count:       [0, 0, 0, 0], Sched None (prio
rity None), drivers: ['acpi']
 IRQ   14: PID:  None, count:       [0, 0, 0, 0], Sched None (prio
rity None), drivers: ['pata_atiixp']
 IRQ   15: PID:  None, count:       [0, 0, 0, 0], Sched None (prio
rity None), drivers: ['pata_atiixp']
 IRQ   16: PID:  None, count: [3026, 3026, 3026, 3026], Sched None
 (priority None), drivers: ['ohci_hcd:usb3', 'ohci_hcd:usb4']
 IRQ   17: PID:  None, count:       [0, 0, 0, 0], Sched None (prio
rity None), drivers: ['ehci_hcd:usb1']
 IRQ   18: PID:  None, count:       [0, 0, 0, 0], Sched None (prio
rity None), drivers: ['ohci_hcd:usb5', 'ohci_hcd:usb6', 'ohci_hcd:
usb7']
 IRQ   19: PID:  None, count:       [0, 0, 0, 0], Sched None (prio
rity None), drivers: ['ehci_hcd:usb2']
 IRQ   20: PID:  None, count: [146, 146, 146, 146], Sched None (pr
iority None), drivers: ['ICE1712']
 IRQ   21: PID:  None, count: [12913, 12913, 12913, 12913], Sched 
None (priority None), drivers: ['0000:03:07']
 IRQ   22: PID:  None, count: [5236, 5236, 5236, 5236], Sched None
 (priority None), drivers: ['ahci', 'firewire_ohci']
 IRQ   42: PID:  None, count:       [0, 0, 0, 0], Sched None (prio
rity None), drivers: ['eth0']
 IRQ   43: PID:  None, count:       [0, 0, 0, 0], Sched None (prio
rity None), drivers: ['fglrx']

Software Interrupts:
--------------------


=== REPORT ===
FireWire kernel drivers:

The new FireWire kernel stack is loaded. 
This is still kind of experimental. If you encounter problems, ple
ase also check
with the old stack.


```The only thing that looks suspect to me is:
```

 /dev/raw1394 node present. False

```When I run 
```

ffado-test ListDevices

```I get this

```

-----------------------------------------------
FFADO test and diagnostic utility
Part of the FFADO project -- www.ffado.org
Version: 2.999.0-
(C) 2008, Daniel Wagner, Pieter Palmers
This program comes with ABSOLUTELY NO WARRANTY.
-----------------------------------------------

=== 1394 PORT 0 ===
  Node id  GUID                  VendorId     ModelId   Vendor - Model
   0       0x0014865e73669127  0x00001486  0x0000AF12   Echo Digital Audio - AudioFire12
00735496020: Error (configrom.cpp)[ 150] initialize: Could not parse config rom of node 1 on port 0
no message buffer overruns


```And when I run 
```

ffado-test Discover

```I get this:
```

-----------------------------------------------
FFADO test and diagnostic utility
Part of the FFADO project -- www.ffado.org
Version: 2.999.0-
(C) 2008, Daniel Wagner, Pieter Palmers
This program comes with ABSOLUTELY NO WARRANTY.
-----------------------------------------------

Could not initialize device manager
01047492287: Fatal (devicemanager.cpp)[ 191] initialize: No firewire adapters (ports) found.
no message buffer overruns


```The 1394 light on my interface is lit up, which means it is connected, but the computer doesn't seem to agree with the device.

I am pretty sure all permissions are correct. I have put myself in the 'audio' group and everything, but fail fail fail.

Should I just install UbuntuStudio? I don't really want to have to reinstall the whole OS. I have all my software and libraries just the way I like them. Is there a way to get the -realtime kernel (or whatever it is that Studio seems to have over generic) without a whole re-make? (Actually, I know that there is, but I have no idea how to do it). Is this even necessary? 

Anyway, thanks in advance for your suggestions, kindly linux folk!

---

### Post by david.medine on 2012-02-09
Ok, so I did have a small permissions problem and that is now solved:

```

sudo chmod 777 /dev/fw*

```but the damn thing still doesn't want to work. I am having identical problems hooking this audiofire12 up to another Ubuntu machine with a slightly different (custom) kernel than the generic one that I am running in my office. This leads me to believe that there is a firmware issue on my audiofire. I find out that you can change the firmware:

[http://subversion.ffado.org/wiki/FireworksFirmwareTool](http://subversion.ffado.org/wiki/FireworksFirmwareTool)

and I read somewhere that 4.8 seems to work better (although that was years ago). However, I cannot even test my hypothesis since when I follow the instructions on the url above I get the following error when I try to hit the flash:

```

david is at ~ : ffado-fireworks-downloader -m 0x001807198000LL -g 0x0014865e73669127 upload ~/Desktop/4.8/bootstrap.dat ~/Desktop/4.8/audiofire12.dat ~/Desktop/4.8/audiofire12_E.dat ~/Desktop/4.8/Fireworks3.dat 
-----------------------------------------------
ECHO FireWorks platform firmware downloader
Part of the FFADO project -- www.ffado.org
Version: 2.999.0-
(C) 2008, Pieter Palmers
This program comes with ABSOLUTELY NO WARRANTY.
-----------------------------------------------

YOU HAVE SPECIFIED THE CORRECT MAGIC NUMBER.
HENCE YOU ACCEPT THE RISKS INVOLVED.
Uploading /home/david/Desktop/4.8/bootstrap.dat to device
 loading file...
 checking file...
  seems to be valid firmware for this device...
 lock flash...
  Could not lock flash
no message buffer overruns


```The 'could not lock flash' message is eerily similar to the error I get when I try to run jack:
```

david is at ~ : jackd -dfirewire
jackdmp 1.9.7
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2011 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
no message buffer overruns
no message buffer overruns
JACK server starting in realtime mode with priority 10
libffado 2.999.0- built Oct 10 2011 08:11:23
02690135305: Error (fireworks_session_block.cpp)[ 129] loadFromDevice: Flash read failed
Segmentation fault


```The firewire chipset on my machine is a TI one, which everyone says is what you want. I will try to take a look at the thing on my Mac and see if that turns up any clues.

---

### Post by david.medine on 2012-02-10
I just upgraded the firmware on the audiofire from my MacBook. I get exactly the same errors as before when I try to use it with linux.

---

