---
title: "konnekt 6 firewire/irqs/jackd problems-confused ubuntu 10.10"
date: 2011-01-07
forum: Multimedia Software
---

### Post by xmariux on 2011-01-07
Hello every one,i tried very hard to make my tc electronic konnekt 6 work on ubuntu 10.10. After a lot of changes i&#8217;m finally stacked again. The konnekt 6 works but for a while, jack stops and i have to restart the konnekt 6 to have sound again.

jackd works very unstable, it depends the settings, the results are system freezes for a while,jack crashes.

So we have:
cat /proc/interrupts
```


           CPU0       CPU1       
  0:         46          0   IO-APIC-edge      timer
  1:          9        390   IO-APIC-edge      i8042
  6:          3          0   IO-APIC-edge      floppy
  7:          0          0   IO-APIC-edge      parport0
  8:          1          0   IO-APIC-edge      rtc0
  9:          0          0   IO-APIC-fasteoi   acpi
 16:          1          1   IO-APIC-fasteoi   uhci_hcd:usb3, ahci, nouveau
 17:        133          0   IO-APIC-fasteoi   uhci_hcd:usb4, pata_jmicron
 18:          0          0   IO-APIC-fasteoi   ehci_hcd:usb1, uhci_hcd:usb7
 19:       3386       9081   IO-APIC-fasteoi   ata_piix, ata_piix, uhci_hcd:usb6
 21:      92408          0   IO-APIC-fasteoi   ohci1394
 23:      46047          0   IO-APIC-fasteoi   ehci_hcd:usb2, uhci_hcd:usb5
 44:         74       6912   PCI-MSI-edge      eth0
NMI:          0          0   Non-maskable interrupts
LOC:     145724     192370   Local timer interrupts
SPU:          0          0   Spurious interrupts
PMI:          0          0   Performance monitoring interrupts
PND:          0          0   Performance pending work
RES:       6049     101507   Rescheduling interrupts
CAL:         47         67   Function call interrupts
TLB:       1565       1750   TLB shootdowns
TRM:          0          0   Thermal event interrupts
THR:          0          0   Threshold APIC interrupts
MCE:          0          0   Machine check exceptions
MCP:          3          3   Machine check polls
ERR:          1
MIS:          0


```

ffado-diag gives me:
```

FFADO diagnostic utility 2.999.0-
============================
(C) 2008 Pieter Palmers


=== CHECK ===
 Base system...
  kernel version............ 2.6.35-24-generic
FIXME: implement test for RT kernel
   RT patched............... False
  old 1394 stack present.... True
  old 1394 stack loaded..... True
  old 1394 stack active..... True
  new 1394 stack present.... True
  new 1394 stack loaded..... False
  new 1394 stack active..... False
  /dev/raw1394 node present. True
  /dev/raw1394 permissions.. True
 Prerequisites (dynamic at run-time)...
   gcc ............... gcc (Ubuntu/Linaro 4.4.4-14ubuntu5) 4.4.5
   g++ ............... g++ (Ubuntu/Linaro 4.4.4-14ubuntu5) 4.4.5
   PyQt4 (by pyuic4) . sh: pyuic4: not found
   jackd ............. no message buffer overruns
     path ............ /usr/bin/jackd
     flags ........... Package jack was not found in the pkg-config search path.
Perhaps you should add the directory containing `jack.pc'
to the PKG_CONFIG_PATH environment variable
No package 'jack' found
   libraw1394 ........ Package libraw1394 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libraw1394.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libraw1394' found
     flags ........... Package libraw1394 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libraw1394.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libraw1394' found
   libavc1394 ........ Package libavc1394 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libavc1394.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libavc1394' found
     flags ........... Package libavc1394 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libavc1394.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libavc1394' found
   libiec61883 ....... Package libiec61883 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libiec61883.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libiec61883' found
     flags ........... Package libiec61883 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libiec61883.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libiec61883' found
   libxml++-2.6 ...... Package libxml++-2.6 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libxml++-2.6.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libxml++-2.6' found
     flags ........... Package libxml++-2.6 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libxml++-2.6.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libxml++-2.6' found
   dbus-1 ............ Package dbus-1 was not found in the pkg-config search path.
Perhaps you should add the directory containing `dbus-1.pc'
to the PKG_CONFIG_PATH environment variable
No package 'dbus-1' found
     flags ........... Package dbus-1 was not found in the pkg-config search path.
Perhaps you should add the directory containing `dbus-1.pc'
to the PKG_CONFIG_PATH environment variable
No package 'dbus-1' found
 Prerequisites (static at compile-time)...
   gcc ............... gcc (Ubuntu/Linaro 4.4.4-8ubuntu1) 4.4.5 20100728 (prerelease)
   g++ ............... g++ (Ubuntu/Linaro 4.4.4-8ubuntu1) 4.4.5 20100728 (prerelease)
   PyQt4 (by pyuic4) . Python User Interface Compiler 4.7.4 for Qt version 4.7.0
   jackd ............. sh: jackd: not found
     path ............ 
     flags ........... Package jack was not found in the pkg-config search path.
   libraw1394 ........ 2.0.5
     flags ...........  -lraw1394  
   libavc1394 ........ Package libavc1394 was not found in the pkg-config search path.
     flags ........... Package libavc1394 was not found in the pkg-config search path.
   libiec61883 ....... 1.2.0
     flags ...........  -liec61883 -lraw1394  
   libxml++-2.6 ...... 2.30.0
     flags ........... -pthread -I/usr/include/libxml++-2.6 -I/usr/lib/libxml++-2.6/include -I/usr/include/libxml2 -I/usr/include/glibmm-2.4 -I/usr/lib/glibmm-2.4/include -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  -pthread -lxml++-2.6 -lxml2 -lglibmm-2.4 -lgobject-2.0 -lsigc-2.0 -lgthread-2.0 -lrt -lglib-2.0  
   dbus-1 ............ 1.2.24
     flags ........... -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include  -L/lib -ldbus-1 -lpthread -lrt  
 Hardware...
   Host controllers:
05:03.0 FireWire (IEEE 1394) [0c00]: VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller [1106:3044] (rev 80) (prog-if 10 [OHCI])
	Subsystem: ASUSTeK Computer Inc. Device [1043:2a22]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (8000ns max), Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 21
	Region 0: Memory at feaff800 (32-bit, non-prefetchable) [size=2K]
	Region 1: I/O ports at bc00 [size=128]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: firewire-ohci, ohci1394

   CPU info:
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 CPU          6600  @ 2.40GHz
stepping	: 6
cpu MHz		: 2402.147
cache size	: 4096 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm dts tpr_shadow
bogomips	: 4804.29
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 CPU          6600  @ 2.40GHz
stepping	: 6
cpu MHz		: 2402.147
cache size	: 4096 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm dts tpr_shadow
bogomips	: 4803.82
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

 Configuration...
  IRQ information
Hardware Interrupts:
--------------------
 IRQ    0: PID:  None, count:           [46, 46], Sched None (priority None), drivers: ['timer']
 IRQ    1: PID:  None, count:             [9, 9], Sched None (priority None), drivers: ['i8042']
 IRQ    6: PID:  None, count:             [3, 3], Sched None (priority None), drivers: ['floppy']
 IRQ    7: PID:  None, count:             [0, 0], Sched None (priority None), drivers: ['parport0']
 IRQ    8: PID:  None, count:             [1, 1], Sched None (priority None), drivers: ['rtc0']
 IRQ    9: PID:  None, count:             [0, 0], Sched None (priority None), drivers: ['acpi']
 IRQ   16: PID:  None, count:             [1, 1], Sched None (priority None), drivers: ['uhci_hcd:usb3', 'ahci', 'nouveau']
 IRQ   17: PID:  None, count:         [133, 133], Sched None (priority None), drivers: ['uhci_hcd:usb4', 'pata_jmicron']
 IRQ   18: PID:  None, count:             [0, 0], Sched None (priority None), drivers: ['ehci_hcd:usb1', 'uhci_hcd:usb7']
 IRQ   19: PID:  None, count:       [3386, 3386], Sched None (priority None), drivers: ['ata_piix', 'ata_piix', 'uhci_hcd:usb6']
 IRQ   21: PID:  None, count:     [92408, 92408], Sched None (priority None), drivers: ['ohci1394']
 IRQ   23: PID:  None, count:     [50157, 50157], Sched None (priority None), drivers: ['ehci_hcd:usb2', 'uhci_hcd:usb5']
 IRQ   44: PID:  None, count:           [74, 74], Sched None (priority None), drivers: ['eth0']

Software Interrupts:
--------------------


=== REPORT ===
FireWire kernel drivers:
[PASS] Kernel modules present and correctly loaded.
[PASS] /dev/raw1394 node present and accessible.

```

ffado-debus-server gives me:
```

sudo ffado-dbus-server 
-----------------------------------------------
FFADO Control DBUS service
Part of the FFADO project -- www.ffado.org
Version: 2.999.0-
(C) 2008, Pieter Palmers
This program comes with ABSOLUTELY NO WARRANTY.
-----------------------------------------------

00896064763:  (ffado-dbus-server.cpp)[ 270] main:  Discovering devices...
00896067552: Debug (devicemanager.cpp)[ 358] discover: Starting discovery...
00896155855: Debug (Configuration.cpp)[ 163] showSetting:   Group: (null)
00896155901: Debug (Configuration.cpp)[ 185] showSetting:     vendorid = 358 (0x00000166)
00896155917: Debug (Configuration.cpp)[ 185] showSetting:     modelid = 36 (0x00000024)
00896155929: Debug (Configuration.cpp)[ 209] showSetting:     vendorname = TC Electronic
00896155944: Debug (Configuration.cpp)[ 209] showSetting:     modelname = Desktop Konnekt 6
00896155953: Debug (Configuration.cpp)[ 185] showSetting:     driver = 20 (0x00000014)
00896156020: Debug (Configuration.cpp)[ 163] showSetting:   Group: (null)
00896156028: Debug (Configuration.cpp)[ 185] showSetting:     vendorid = 358 (0x00000166)
00896156038: Debug (Configuration.cpp)[ 185] showSetting:     modelid = 36 (0x00000024)
00896156043: Debug (Configuration.cpp)[ 209] showSetting:     vendorname = TC Electronic
00896156053: Debug (Configuration.cpp)[ 209] showSetting:     modelname = Desktop Konnekt 6
00896156057: Debug (Configuration.cpp)[ 185] showSetting:     driver = 20 (0x00000014)
00896156107: Debug (Configuration.cpp)[ 163] showSetting:   Group: (null)
00896156116: Debug (Configuration.cpp)[ 185] showSetting:     vendorid = 358 (0x00000166)
00896156126: Debug (Configuration.cpp)[ 185] showSetting:     modelid = 36 (0x00000024)
00896156131: Debug (Configuration.cpp)[ 209] showSetting:     vendorname = TC Electronic
00896156140: Debug (Configuration.cpp)[ 209] showSetting:     modelname = Desktop Konnekt 6
00896156145: Debug (Configuration.cpp)[ 185] showSetting:     driver = 20 (0x00000014)
00896156193: Debug (Configuration.cpp)[ 163] showSetting:   Group: (null)
00896156201: Debug (Configuration.cpp)[ 185] showSetting:     vendorid = 358 (0x00000166)
00896156210: Debug (Configuration.cpp)[ 185] showSetting:     modelid = 36 (0x00000024)
00896156215: Debug (Configuration.cpp)[ 209] showSetting:     vendorname = TC Electronic
00896156225: Debug (Configuration.cpp)[ 209] showSetting:     modelname = Desktop Konnekt 6
00896156231: Debug (Configuration.cpp)[ 185] showSetting:     driver = 20 (0x00000014)
00896156283: Debug (Configuration.cpp)[ 163] showSetting:   Group: (null)
00896156290: Debug (Configuration.cpp)[ 185] showSetting:     vendorid = 358 (0x00000166)
00896156300: Debug (Configuration.cpp)[ 185] showSetting:     modelid = 36 (0x00000024)
00896156305: Debug (Configuration.cpp)[ 209] showSetting:     vendorname = TC Electronic
00896156314: Debug (Configuration.cpp)[ 209] showSetting:     modelname = Desktop Konnekt 6
00896156319: Debug (Configuration.cpp)[ 185] showSetting:     driver = 20 (0x00000014)
00896156458: Debug (devicemanager.cpp)[ 620] discover: driver found for device 0
00896156501: Debug (Configuration.cpp)[ 163] showSetting:   Group: (null)
00896156516: Debug (Configuration.cpp)[ 185] showSetting:     vendorid = 358 (0x00000166)
00896156523: Debug (Configuration.cpp)[ 185] showSetting:     modelid = 36 (0x00000024)
00896156533: Debug (Configuration.cpp)[ 209] showSetting:     vendorname = TC Electronic
00896156540: Debug (Configuration.cpp)[ 209] showSetting:     modelname = Desktop Konnekt 6
00896156549: Debug (Configuration.cpp)[ 185] showSetting:     driver = 20 (0x00000014)
00896185072: Error (dice_avdevice.cpp)[1718] readReg: Could not read from node 0xFFC0 addr 0xFFFFE0200000
00896185096: Error (dice_eap.cpp)[ 113] init: Device does not support EAP
00896185106: Warning (dice_avdevice.cpp)[ 171] discover: Could not init EAP
00896185172: Debug (devicemanager.cpp)[ 657] discover: discovery of node 0 on port 0 done...
00896185185: Debug (devicemanager.cpp)[ 665] discover: Discovery finished...
00896185205: Debug (devicemanager.cpp)[1252] showDeviceInfo: ===== Device Manager =====
00896185215: Debug (Element.cpp)[ 121] show: Element DeviceManager
00896185228: Debug (devicemanager.cpp)[1260] showDeviceInfo: --- IEEE1394 Service  0 ---
Iso handler info:
Dumping IsoHandlerManager Stream handler information...
 State: 2
00896185263: Debug (devicemanager.cpp)[1270] showDeviceInfo: --- Device  0 ---
00896185274: Debug (dice_avdevice.cpp)[ 623] showDevice: Device is a DICE device
00896185287: Debug (ffadodevice.cpp)[ 214] showDevice: Attached to port.......: 0 (ohci1394)
00896185297: Debug (ffadodevice.cpp)[ 215] showDevice: Node...................: 0
00896185316: Debug (ffadodevice.cpp)[ 217] showDevice: Vendor name............: TC Electronic
00896185321: Debug (ffadodevice.cpp)[ 219] showDevice: Model name.............: DesktopKonnekt6
00896185330: Debug (ffadodevice.cpp)[ 221] showDevice: GUID...................: 000166040900261a
00896185342: Debug (ffadodevice.cpp)[ 226] showDevice: Assigned ID....: 000166040900261a
00896185363:  (dice_avdevice.cpp)[ 626] showDevice:  DICE Parameter Space info:
00896185368:  (dice_avdevice.cpp)[ 627] showDevice:   Global  : offset=0x0028 size=0360
00896185377:  (dice_avdevice.cpp)[ 628] showDevice:   TX      : offset=0x0190 size=0568
00896185380:  (dice_avdevice.cpp)[ 629] showDevice:                 nb=   1 size=0280
00896185388:  (dice_avdevice.cpp)[ 630] showDevice:   RX      : offset=0x03C8 size=1128
00896185392:  (dice_avdevice.cpp)[ 631] showDevice:                 nb=   1 size=0280
00896185399:  (dice_avdevice.cpp)[ 632] showDevice:   UNUSED1 : offset=0x0830 size=0016
00896185403:  (dice_avdevice.cpp)[ 633] showDevice:   UNUSED2 : offset=0x0000 size=0000
00896185411:  (dice_avdevice.cpp)[ 635] showDevice:  Global param space:
00896186690:  (dice_avdevice.cpp)[ 638] showDevice:   Owner            : 0xE0000000FFC1FFFF
00896188005:  (dice_avdevice.cpp)[ 641] showDevice:   Notification     : 0x00000040
00896190554:  (dice_avdevice.cpp)[ 644] showDevice:   Nick name        : DesktopKonnekt6
00896191893:  (dice_avdevice.cpp)[ 648] showDevice:   Clock Select     : 0x01 0x0C
00896193123:  (dice_avdevice.cpp)[ 652] showDevice:   Enable           : true
00896194434:  (dice_avdevice.cpp)[ 656] showDevice:   Clock Status     : locked 0x01
00896195661:  (dice_avdevice.cpp)[ 659] showDevice:   Extended Status  : 0x00000000
00896196890:  (dice_avdevice.cpp)[ 662] showDevice:   Samplerate       : 0x0000AC44 (44100)
00896198203:  (dice_avdevice.cpp)[ 665] showDevice:   Version          : 0x01000400
00896199430:  (dice_avdevice.cpp)[ 674] showDevice:   Version          : 0x01000400 (1.0.4.0)
00896200657:  (dice_avdevice.cpp)[ 677] showDevice:   Clock caps       : 0x1300007E
00896202310:  (dice_avdevice.cpp)[ 680] showDevice:   Clock sources    :
00896202324:  (dice_avdevice.cpp)[ 686] showDevice:     Unused
00896202337:  (dice_avdevice.cpp)[ 686] showDevice:     Unused
00896202342:  (dice_avdevice.cpp)[ 686] showDevice:     Unused
00896202353:  (dice_avdevice.cpp)[ 686] showDevice:     Unused
00896202358:  (dice_avdevice.cpp)[ 686] showDevice:     Unused
00896202368:  (dice_avdevice.cpp)[ 686] showDevice:     Unused
00896202373:  (dice_avdevice.cpp)[ 686] showDevice:     Unused
00896202384:  (dice_avdevice.cpp)[ 686] showDevice:     Unused
00896202389:  (dice_avdevice.cpp)[ 686] showDevice:     Unused
00896202400:  (dice_avdevice.cpp)[ 686] showDevice:     Unused
00896202404:  (dice_avdevice.cpp)[ 686] showDevice:     Unused
00896202415:  (dice_avdevice.cpp)[ 686] showDevice:     Unused
00896202420:  (dice_avdevice.cpp)[ 686] showDevice:     INTERNAL
00896202431:  (dice_avdevice.cpp)[ 689] showDevice:  TX param space:
00896202436:  (dice_avdevice.cpp)[ 690] showDevice:   Nb of xmit        : 1
00896202447:  (dice_avdevice.cpp)[ 692] showDevice:   Transmitter 0:
00896203600:  (dice_avdevice.cpp)[ 695] showDevice:    ISO channel       :   0
00896204828:  (dice_avdevice.cpp)[ 697] showDevice:    ISO speed         :   2
00896206053:  (dice_avdevice.cpp)[ 700] showDevice:    Nb audio channels :   6
00896207281:  (dice_avdevice.cpp)[ 702] showDevice:    Nb midi channels  :   0
00896208516:  (dice_avdevice.cpp)[ 705] showDevice:    AC3 caps          : 0x00000000
00896209755:  (dice_avdevice.cpp)[ 707] showDevice:    AC3 enable        : 0x00000000
00896211464:  (dice_avdevice.cpp)[ 710] showDevice:    Channel names     :
00896211484:  (dice_avdevice.cpp)[ 715] showDevice:      ch 1
00896211495:  (dice_avdevice.cpp)[ 715] showDevice:      ch 2
00896211509:  (dice_avdevice.cpp)[ 715] showDevice:       - 
00896211520:  (dice_avdevice.cpp)[ 715] showDevice:       - 
00896211534:  (dice_avdevice.cpp)[ 715] showDevice:       - 
00896211544:  (dice_avdevice.cpp)[ 715] showDevice:       - 
00896211559:  (dice_avdevice.cpp)[ 719] showDevice:  RX param space:
00896211572:  (dice_avdevice.cpp)[ 720] showDevice:   Nb of recv        : 1
00896211586:  (dice_avdevice.cpp)[ 722] showDevice:   Receiver 0:
00896212783:  (dice_avdevice.cpp)[ 725] showDevice:    ISO channel       :   1
00896214012:  (dice_avdevice.cpp)[ 727] showDevice:    Sequence start    :   0
00896215821:  (dice_avdevice.cpp)[ 730] showDevice:    Nb audio channels :   6
00896217188:  (dice_avdevice.cpp)[ 732] showDevice:    Nb midi channels  :   0
00896218414:  (dice_avdevice.cpp)[ 735] showDevice:    AC3 caps          : 0x00000000
00896219642:  (dice_avdevice.cpp)[ 737] showDevice:    AC3 enable        : 0x00000000
00896221101:  (dice_avdevice.cpp)[ 740] showDevice:    Channel names     :
00896221112:  (dice_avdevice.cpp)[ 745] showDevice:      main out 1
00896221116:  (dice_avdevice.cpp)[ 745] showDevice:      main out 2
00896221122:  (dice_avdevice.cpp)[ 745] showDevice:      phones out 1
00896221125:  (dice_avdevice.cpp)[ 745] showDevice:      phones out 2
00896221134:  (dice_avdevice.cpp)[ 745] showDevice:       - 
00896221137:  (dice_avdevice.cpp)[ 745] showDevice:       - 
00896221156: Debug (devicemanager.cpp)[1273] showDeviceInfo: Clock sync sources:
00896226459: Debug (devicemanager.cpp)[1282] showDeviceInfo:  Type: Compound Syt Match, Id:  8, Valid: 1, Active: 0, Locked 0, Slipping: 0, Description: Unused
00896226478: Debug (devicemanager.cpp)[1282] showDeviceInfo:  Type: Compound Syt Match, Id:  9, Valid: 1, Active: 0, Locked 0, Slipping: 0, Description: Unused
00896226485: Debug (devicemanager.cpp)[1282] showDeviceInfo:  Type: Internal          , Id: 12, Valid: 1, Active: 1, Locked 1, Slipping: 0, Description: INTERNAL
00896237498:  (ffado-dbus-server.cpp)[ 328] main: DBUS service running
00896237527:  (ffado-dbus-server.cpp)[ 329] main: press ctrl-c to stop it & exit
00896237542: Debug (ffado-dbus-server.cpp)[ 332] main: dispatching...

```

after a while prints:
```

00907868922: Warning (CycleTimerHelper.cpp)[ 514] Execute: rather large step: 70794993.280165 ticks (> 1sec)
00908068983: Error (CycleTimerHelper.cpp)[ 508] Execute: negative step: -24357675.517068! (correcting to nominal)
00908668931: Error (CycleTimerHelper.cpp)[ 508] Execute: negative step: -3280301.065451! (correcting to nominal)
00908868980: Error (CycleTimerHelper.cpp)[ 508] Execute: negative step: -55051868.064437! (correcting to nominal)
00909068832: Error (CycleTimerHelper.cpp)[ 508] Execute: negative step: -40226477.661857! (correcting to nominal)
00909269144: Error (CycleTimerHelper.cpp)[ 508] Execute: negative step: -51830982.099727! (correcting to nominal)
00909468971: Error (CycleTimerHelper.cpp)[ 508] Execute: negative step: -96324394.316863! (correcting to nominal)
00909668930: Error (CycleTimerHelper.cpp)[ 508] Execute: negative step: -121192127.899938! (correcting to nominal)

```

jackd works fine until stops and printing the following:
```

JackFFADODriver::ffado_driver_wait &#8211; unhandled xrun
firewire ERR: wait status < 0! (= -1)
JackAudioDriver::ProcessAsync: read error, skip cycle

```

Some times the system freezes but when i turn off/on the konnekt 6 comes back but i have to restart jack vlc etc.

Is IRQ's problem?
What sould i do?

---

### Post by schef on 2011-01-14
Hej..i have the same problem on Archlinux using Presonus Firebox firewire audio card..When i was using an USB audio interface from M-Audio i didn't expirience any crashes and sound quality was much better..I think it has something to do with FFADO..I have read on some other sites that it has to do with realtime prioritys..don't know..

---

### Post by schef on 2011-01-14
Hej..i have the same problem on Archlinux using Presonus Firebox firewire audio card..When i was using an USB audio interface from M-Audio i didn't expirience any crashes and sound quality was much better..I think it has something to do with FFADO..I have read on some other sites that it has to do with realtime prioritys..don't know..

---

