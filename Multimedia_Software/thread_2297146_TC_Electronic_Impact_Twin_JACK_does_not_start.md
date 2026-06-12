---
title: "TC Electronic Impact Twin JACK does not start"
date: 2015-10-01
forum: Multimedia Software
---

### Post by Kim_Ake on 2015-10-01
EDIT:
No matter what, I could not get Ubuntu to work, so I installed KXStudio instead, and now everything is running fine. So it was some configuration problem, bad drivers or something...

Hi, I have a problem that must be very easy to solve.

If I choose ALSA as the driver option in qjackctl, Jack starts OK, and I can use apps like Renoise & Audacity.

But if I choose firewire as the driver option, Jack refuses to start.... Wait, it ONCE started when I played around with the settings. I even made a 45 minute glitchless recording in Bitwig. But even with the same settings, never again.

Even the FFADO mixer recognises the interface.

So the soundcard works, but why not in firewire mode? (except that one time)

Here's some diags I ran:

```
---

kim@kim-desktop:~/Desktop$ lsmod | grep firewire
snd_firewire_lib       32768  1 snd_dice
snd_rawmidi            32768  4 snd_firewire_lib,snd_usbmidi_lib,snd_dice,snd_seq_midi
snd_pcm               106496  7 snd_firewire_lib,snd_usb_audio,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller,snd_dice
firewire_ohci          40960  0 
firewire_core          65536  3 snd_firewire_lib,firewire_ohci,snd_dice
crc_itu_t              16384  1 firewire_core




-----


kim@kim-desktop:~/Desktop$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 3: Twin [Impact Twin], device 0: DICE [Impact Twin]
  Subdevices: 1/1
  Subdevice #0: subdevice #0




-----


kim@kim-desktop:~/Desktop$ ffado-diag




FFADO diagnostic utility 2.2.1
============================
(C) 2008 Pieter Palmers
    2009-2010 Arnold Krille




=== CHECK ===
 Base system...
  kernel version............ 3.19.0-28-lowlatency
    Preempt (low latency)... True
    RT patched.............. False
  old 1394 stack present.... False
  old 1394 stack loaded..... False
  old 1394 stack active..... False
  new 1394 stack present.... True
  new 1394 stack loaded..... True
  new 1394 stack active..... True
  /dev/raw1394 node present. False
  /dev/fw* permissions:
crw-------  1 root root  251, 0 loka   1 17:23 /dev/fw0
crw-rw----+ 1 root audio 251, 1 loka   1 17:23 /dev/fw1
  User IDs:
uid=1000(kim) gid=1000(kim) groups=1000(kim),4(adm),24(cdrom),27(sudo),29(audio),30(dip),46(plugdev),115(lpadmin),130(sambashare)
 Prerequisites (dynamic at run-time)...
   gcc ............... gcc (Ubuntu 4.9.2-10ubuntu13) 4.9.2
   g++ ............... g++ (Ubuntu 4.9.2-10ubuntu13) 4.9.2
   PyQt4 (by pyuic4) . sh: 1: pyuic4: not found
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
   gcc ............... gcc (Ubuntu 4.9.2-7ubuntu3) 4.9.2
   g++ ............... g++ (Ubuntu 4.9.2-7ubuntu3) 4.9.2
   PyQt4 (by pyuic4) . Python User Interface Compiler 4.11.3 for Qt version 4.8.6
   jackd ............. sh: 1: jackd: not found
     path ............ 
     flags ........... Package jack was not found in the pkg-config search path.
   libraw1394 ........ 2.1.0
     flags ........... -lraw1394 
   libavc1394 ........ Package libavc1394 was not found in the pkg-config search path.
     flags ........... Package libavc1394 was not found in the pkg-config search path.
   libiec61883 ....... 1.2.0
     flags ........... -liec61883 -lraw1394 
   libxml++-2.6 ...... 2.36.0
     flags ........... -I/usr/include/libxml2 -I/usr/include/glibmm-2.4 -I/usr/lib/x86_64-linux-gnu/glibmm-2.4/include -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -I/usr/include/sigc++-2.0 -I/usr/lib/x86_64-linux-gnu/sigc++-2.0/include -I/usr/include/libxml++-2.6 -I/usr/lib/libxml++-2.6/include -lxml++-2.6 -lxml2 -lglibmm-2.4 -lgobject-2.0 -lglib-2.0 -lsigc-2.0 
   dbus-1 ............ 1.8.12
     flags ........... -I/usr/include/dbus-1.0 -I/usr/lib/x86_64-linux-gnu/dbus-1.0/include -ldbus-1 
 uname -a...
   Linux kim-desktop 3.19.0-28-lowlatency #30-Ubuntu SMP PREEMPT Mon Aug 31 16:36:36 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
 Hardware...
   Host controllers:
08:00.0 FireWire (IEEE 1394) [0c00]: Texas Instruments XIO2200A IEEE-1394a-2000 Controller (PHY/Link) [104c:8235] (rev 01) (prog-if 10 [OHCI])
    Subsystem: Texas Instruments Device [104c:8023]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32 (500ns min, 1000ns max), Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 20
    Region 0: Memory at fe604000 (32-bit, non-prefetchable) [size=2K]
    Region 1: Memory at fe600000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: firewire_ohci


   CPU info:
Architecture:          x86_64
CPU op-mode(s):        32-bit, 64-bit
Byte Order:            Little Endian
CPU(s):                6
On-line CPU(s) list:   0-5
Thread(s) per core:    1
Core(s) per socket:    6
Socket(s):             1
NUMA node(s):          1
Vendor ID:             AuthenticAMD
CPU family:            16
Model:                 10
Model name:            AMD Phenom(tm) II X6 1055T Processor
Stepping:              0
CPU MHz:               2809.503
BogoMIPS:              5619.00
Virtualization:        AMD-V
L1d cache:             64K
L1i cache:             64K
L2 cache:              512K
L3 cache:              6144K
NUMA node0 CPU(s):     0-5
 Configuration...
  IRQ information
Hardware Interrupts:
--------------------
 IRQ    0: PID:  None, count: [16029, 0, 0, 0, 0, 0], Sched None (priority None), drivers: ['timer']
 IRQ    1: PID:  None, count: [0, 0, 0, 0, 0, 2], Sched None (priority None), drivers: ['i8042']
 IRQ    7: PID:  None, count: [1, 0, 0, 0, 0, 0], Sched None (priority None), drivers: ['']
 IRQ    8: PID:  None, count: [0, 0, 0, 0, 0, 1], Sched None (priority None), drivers: ['rtc0']
 IRQ    9: PID:  None, count: [0, 0, 0, 0, 0, 0], Sched None (priority None), drivers: ['acpi']
 IRQ   12: PID:  None, count: [0, 0, 0, 0, 0, 4], Sched None (priority None), drivers: ['i8042']
 IRQ   17: PID:  None, count: [0, 0, 0, 0, 0, 3], Sched None (priority None), drivers: ['17-fasteoi   ehci_hcd:usb5']
 IRQ   18: PID:  None, count: [0, 0, 0, 4111, 3, 312], Sched None (priority None), drivers: ['18-fasteoi   ohci_hcd:usb8', 'ohci_hcd:usb10']
 IRQ   19: PID:  None, count: [0, 0, 2783, 0, 40, 12985], Sched None (priority None), drivers: ['19-fasteoi   0000:00:11']
 IRQ   20: PID:  None, count: [0, 0, 0, 0, 36, 8605], Sched None (priority None), drivers: ['20-fasteoi   ohci_hcd:usb9', 'firewire_ohci']
 IRQ   21: PID:  None, count: [2798, 0, 0, 0, 6, 3105], Sched None (priority None), drivers: ['21-fasteoi   ehci_hcd:usb6']
 IRQ   22: PID:  None, count: [0, 0, 0, 0, 0, 1], Sched None (priority None), drivers: ['22-fasteoi   ohci_hcd:usb11']
 IRQ   23: PID:  None, count: [0, 0, 0, 0, 0, 0], Sched None (priority None), drivers: ['23-fasteoi   ehci_hcd:usb7']
 IRQ   27: PID:  None, count: [0, 0, 0, 0, 0, 0], Sched None (priority None), drivers: ['xhci_hcd']
 IRQ   28: PID:  None, count: [0, 0, 0, 0, 0, 0], Sched None (priority None), drivers: ['xhci_hcd']
 IRQ   29: PID:  None, count: [0, 0, 0, 0, 0, 0], Sched None (priority None), drivers: ['xhci_hcd']
 IRQ   30: PID:  None, count: [0, 0, 0, 0, 0, 0], Sched None (priority None), drivers: ['xhci_hcd']
 IRQ   31: PID:  None, count: [0, 0, 0, 0, 0, 0], Sched None (priority None), drivers: ['xhci_hcd']
 IRQ   32: PID:  None, count: [0, 0, 0, 0, 0, 0], Sched None (priority None), drivers: ['xhci_hcd']
 IRQ   33: PID:  None, count: [0, 0, 0, 0, 0, 0], Sched None (priority None), drivers: ['xhci_hcd']
 IRQ   35: PID:  None, count: [0, 0, 0, 0, 0, 0], Sched None (priority None), drivers: ['xhci_hcd']
 IRQ   36: PID:  None, count: [0, 0, 0, 0, 0, 0], Sched None (priority None), drivers: ['xhci_hcd']
 IRQ   37: PID:  None, count: [0, 0, 0, 0, 0, 0], Sched None (priority None), drivers: ['xhci_hcd']
 IRQ   38: PID:  None, count: [0, 0, 0, 0, 0, 0], Sched None (priority None), drivers: ['xhci_hcd']
 IRQ   39: PID:  None, count: [0, 0, 0, 0, 0, 0], Sched None (priority None), drivers: ['xhci_hcd']
 IRQ   40: PID:  None, count: [0, 0, 0, 0, 0, 0], Sched None (priority None), drivers: ['xhci_hcd']
 IRQ   41: PID:  None, count: [0, 0, 0, 0, 0, 0], Sched None (priority None), drivers: ['xhci_hcd']
 IRQ   43: PID:  None, count: [0, 0, 0, 0, 0, 0], Sched None (priority None), drivers: ['eth0']
 IRQ   45: PID:  None, count: [0, 0, 0, 0, 0, 0], Sched None (priority None), drivers: ['0000:04:00']
 IRQ   47: PID:  None, count: [0, 0, 0, 0, 11, 225], Sched None (priority None), drivers: ['snd_hda_intel']
 IRQ   49: PID:  None, count: [0, 0, 0, 0, 6, 1081], Sched None (priority None), drivers: ['radeon']


Software Interrupts:
--------------------




=== REPORT ===
FireWire kernel drivers:


The new FireWire kernel stack is loaded. 
If running a kernel earlier than 2.6.37 and problems are experienced, either 
try with the old Firewire kernel stack or upgrade to a newer kernel 
(preferrably 2.6.37 or later).


----


kim@kim-desktop:~/Desktop$ ffado-test ListDevices
-----------------------------------------------
FFADO test and diagnostic utility
Part of the FFADO project -- www.ffado.org
Version: 2.2.1-
(C) 2008, Daniel Wagner, Pieter Palmers
This program comes with ABSOLUTELY NO WARRANTY.
-----------------------------------------------


=== 1394 PORT 0 ===
  Node id  GUID                  VendorId     ModelId   Vendor - Model
   0       0x0001660409c00629  0x00000166  0x00000027   TC Electronic - ImpactTwin
no message buffer overruns




----




kim@kim-desktop:~/Desktop$ sudo ffado-dbus-server
[sudo] password for kim: 
-----------------------------------------------
FFADO Control DBUS service
Part of the FFADO project -- www.ffado.org
Version: 2.2.1-
(C) 2008, Pieter Palmers
This program comes with ABSOLUTELY NO WARRANTY.
-----------------------------------------------


1443709917426518:  (ffado-dbus-server.cpp)[ 270] main:  Discovering devices...
00511435497: Debug (devicemanager.cpp)[ 354] discover: Starting discovery...
00511513544: Debug (Configuration.cpp)[ 163] showSetting:   Group: (null)
00511513561: Debug (Configuration.cpp)[ 185] showSetting:     vendorid = 358 (0x00000166)
00511513569: Debug (Configuration.cpp)[ 185] showSetting:     modelid = 39 (0x00000027)
00511513573: Debug (Configuration.cpp)[ 209] showSetting:     vendorname = TC Electronic
00511513579: Debug (Configuration.cpp)[ 209] showSetting:     modelname = ImpactTwin
00511513581: Debug (Configuration.cpp)[ 209] showSetting:     driver = DICE
00511513695: Debug (Configuration.cpp)[ 163] showSetting:   Group: (null)
00511513700: Debug (Configuration.cpp)[ 185] showSetting:     vendorid = 358 (0x00000166)
00511513704: Debug (Configuration.cpp)[ 185] showSetting:     modelid = 39 (0x00000027)
00511513706: Debug (Configuration.cpp)[ 209] showSetting:     vendorname = TC Electronic
00511513713: Debug (Configuration.cpp)[ 209] showSetting:     modelname = ImpactTwin
00511513715: Debug (Configuration.cpp)[ 209] showSetting:     driver = DICE
00511513786: Debug (Configuration.cpp)[ 163] showSetting:   Group: (null)
00511513790: Debug (Configuration.cpp)[ 185] showSetting:     vendorid = 358 (0x00000166)
00511513794: Debug (Configuration.cpp)[ 185] showSetting:     modelid = 39 (0x00000027)
00511513796: Debug (Configuration.cpp)[ 209] showSetting:     vendorname = TC Electronic
00511513800: Debug (Configuration.cpp)[ 209] showSetting:     modelname = ImpactTwin
00511513804: Debug (Configuration.cpp)[ 209] showSetting:     driver = DICE
00511513869: Debug (Configuration.cpp)[ 163] showSetting:   Group: (null)
00511513874: Debug (Configuration.cpp)[ 185] showSetting:     vendorid = 358 (0x00000166)
00511513878: Debug (Configuration.cpp)[ 185] showSetting:     modelid = 39 (0x00000027)
00511513881: Debug (Configuration.cpp)[ 209] showSetting:     vendorname = TC Electronic
00511513887: Debug (Configuration.cpp)[ 209] showSetting:     modelname = ImpactTwin
00511513889: Debug (Configuration.cpp)[ 209] showSetting:     driver = DICE
00511513959: Debug (Configuration.cpp)[ 163] showSetting:   Group: (null)
00511513963: Debug (Configuration.cpp)[ 185] showSetting:     vendorid = 358 (0x00000166)
00511513967: Debug (Configuration.cpp)[ 185] showSetting:     modelid = 39 (0x00000027)
00511513969: Debug (Configuration.cpp)[ 209] showSetting:     vendorname = TC Electronic
00511513976: Debug (Configuration.cpp)[ 209] showSetting:     modelname = ImpactTwin
00511513978: Debug (Configuration.cpp)[ 209] showSetting:     driver = DICE
00511514050: Debug (devicemanager.cpp)[ 616] discover: driver found for device 0
00511514106: Debug (Configuration.cpp)[ 163] showSetting:   Group: (null)
00511514114: Debug (Configuration.cpp)[ 185] showSetting:     vendorid = 358 (0x00000166)
00511514116: Debug (Configuration.cpp)[ 185] showSetting:     modelid = 39 (0x00000027)
00511514120: Debug (Configuration.cpp)[ 209] showSetting:     vendorname = TC Electronic
00511514122: Debug (Configuration.cpp)[ 209] showSetting:     modelname = ImpactTwin
00511514128: Debug (Configuration.cpp)[ 209] showSetting:     driver = DICE
00511543127: Error (dice_avdevice.cpp)[1731] readReg: Could not read from node 0xFFC0 addr 0xFFFFE0200000
00511543145: Warning (dice_eap.cpp)[ 115] init: no EAP mixer (device does not support EAP)
00511543147: Warning (dice_avdevice.cpp)[ 194] discover: Could not init EAP
00511543164: Debug (devicemanager.cpp)[ 653] discover: discovery of node 0 on port 0 done...
00511543168: Debug (devicemanager.cpp)[ 661] discover: Discovery finished...
00511543181: Debug (devicemanager.cpp)[1258] showDeviceInfo: ===== Device Manager =====
00511543184: Debug (Element.cpp)[ 121] show: Element DeviceManager
00511543192: Debug (devicemanager.cpp)[1266] showDeviceInfo: --- IEEE1394 Service  0 ---
00511543196: Debug (devicemanager.cpp)[1276] showDeviceInfo: --- Device  0 ---
00511543202: Debug (dice_avdevice.cpp)[ 703] showDevice: Device is a DICE device
00511543204:  (dice_avdevice.cpp)[ 706] showDevice:  DICE Parameter Space info:
00511543210:  (dice_avdevice.cpp)[ 707] showDevice:   Global  : offset=0x0028 size=0360
00511543212:  (dice_avdevice.cpp)[ 708] showDevice:   TX      : offset=0x0190 size=0568
00511543218:  (dice_avdevice.cpp)[ 709] showDevice:                 nb=   1 size=0280
00511543220:  (dice_avdevice.cpp)[ 710] showDevice:   RX      : offset=0x03C8 size=1128
00511543226:  (dice_avdevice.cpp)[ 711] showDevice:                 nb=   1 size=0280
00511543228:  (dice_avdevice.cpp)[ 712] showDevice:   UNUSED1 : offset=0x0830 size=0016
00511543234:  (dice_avdevice.cpp)[ 713] showDevice:   UNUSED2 : offset=0x0000 size=0000
00511543235:  (dice_avdevice.cpp)[ 715] showDevice:  Global param space:
00511544587:  (dice_avdevice.cpp)[ 718] showDevice:   Owner            : 0x00000000FFC10001
00511545912:  (dice_avdevice.cpp)[ 721] showDevice:   Notification     : 0x00000020
00511548630:  (dice_avdevice.cpp)[ 724] showDevice:   Nick name        : Impact Twin
00511549957:  (dice_avdevice.cpp)[ 728] showDevice:   Clock Select     : 0x01 0x0C
00511551255:  (dice_avdevice.cpp)[ 732] showDevice:   Enable           : false
00511552503:  (dice_avdevice.cpp)[ 736] showDevice:   Clock Status     : locked 0x01
00511554030:  (dice_avdevice.cpp)[ 739] showDevice:   Extended Status  : 0x00000040
00511555339:  (dice_avdevice.cpp)[ 742] showDevice:   Samplerate       : 0x0000AC44 (44100)
00511556655:  (dice_avdevice.cpp)[ 745] showDevice:   Version          : 0x01000400
00511557972:  (dice_avdevice.cpp)[ 754] showDevice:   Version          : 0x01000400 (1.0.4.0)
00511559294:  (dice_avdevice.cpp)[ 757] showDevice:   Clock caps       : 0x1F29007E
00511560870:  (dice_avdevice.cpp)[ 760] showDevice:   Clock sources    :
00511560887:  (dice_avdevice.cpp)[ 766] showDevice:     TOS
00511560889:  (dice_avdevice.cpp)[ 766] showDevice:     Unused
00511560892:  (dice_avdevice.cpp)[ 766] showDevice:     Unused
00511560894:  (dice_avdevice.cpp)[ 766] showDevice:     S/PDIF
00511560897:  (dice_avdevice.cpp)[ 766] showDevice:     Unused
00511560899:  (dice_avdevice.cpp)[ 766] showDevice:     ADAT
00511560902:  (dice_avdevice.cpp)[ 766] showDevice:     Unused
00511560903:  (dice_avdevice.cpp)[ 766] showDevice:     Unused
00511560906:  (dice_avdevice.cpp)[ 766] showDevice:     Unused
00511560908:  (dice_avdevice.cpp)[ 766] showDevice:     Unused
00511560911:  (dice_avdevice.cpp)[ 766] showDevice:     Unused
00511560913:  (dice_avdevice.cpp)[ 766] showDevice:     Unused
00511560916:  (dice_avdevice.cpp)[ 766] showDevice:     INTERNAL
00511560918:  (dice_avdevice.cpp)[ 769] showDevice:  TX param space:
00511560925:  (dice_avdevice.cpp)[ 770] showDevice:   Nb of xmit        : 1
00511560927:  (dice_avdevice.cpp)[ 772] showDevice:   Transmitter 0:
00511562159:  (dice_avdevice.cpp)[ 775] showDevice:    ISO channel       :  -1
00511563455:  (dice_avdevice.cpp)[ 777] showDevice:    ISO speed         :   2
00511564872:  (dice_avdevice.cpp)[ 780] showDevice:    Nb audio channels :  14
00511566180:  (dice_avdevice.cpp)[ 782] showDevice:    Nb midi channels  :   1
00511567506:  (dice_avdevice.cpp)[ 785] showDevice:    AC3 caps          : 0x00000000
00511568823:  (dice_avdevice.cpp)[ 787] showDevice:    AC3 enable        : 0x00000000
00511570364:  (dice_avdevice.cpp)[ 790] showDevice:    Channel names     :
00511570376:  (dice_avdevice.cpp)[ 795] showDevice:      FW 1 (main)
00511570382:  (dice_avdevice.cpp)[ 795] showDevice:      FW 2 (main)
00511570384:  (dice_avdevice.cpp)[ 795] showDevice:      FW 3 (line)
00511570387:  (dice_avdevice.cpp)[ 795] showDevice:      FW 4 (line)
00511570388:  (dice_avdevice.cpp)[ 795] showDevice:      FW 5 (spdif)
00511570391:  (dice_avdevice.cpp)[ 795] showDevice:      FW 6 (spdif)
00511570393:  (dice_avdevice.cpp)[ 795] showDevice:      FW 7 (adat|tos)
00511570396:  (dice_avdevice.cpp)[ 795] showDevice:      FW 8 (adat|tos)
00511570397:  (dice_avdevice.cpp)[ 795] showDevice:      FW 9 (adat)
00511570400:  (dice_avdevice.cpp)[ 795] showDevice:      FW 10 (adat)
00511570402:  (dice_avdevice.cpp)[ 795] showDevice:      FW 11 (adat)
00511570405:  (dice_avdevice.cpp)[ 795] showDevice:      FW 12 (adat)
00511570407:  (dice_avdevice.cpp)[ 795] showDevice:      FW 13 (adat)
00511570414:  (dice_avdevice.cpp)[ 795] showDevice:      FW 14 (adat)
00511570416:  (dice_avdevice.cpp)[ 799] showDevice:  RX param space:
00511570424:  (dice_avdevice.cpp)[ 800] showDevice:   Nb of recv        : 1
00511570426:  (dice_avdevice.cpp)[ 802] showDevice:   Receiver 0:
00511571680:  (dice_avdevice.cpp)[ 805] showDevice:    ISO channel       :  -1
00511572997:  (dice_avdevice.cpp)[ 807] showDevice:    Sequence start    :   0
00511574417:  (dice_avdevice.cpp)[ 810] showDevice:    Nb audio channels :  14
00511575728:  (dice_avdevice.cpp)[ 812] showDevice:    Nb midi channels  :   1
00511577047:  (dice_avdevice.cpp)[ 815] showDevice:    AC3 caps          : 0x00000000
00511578354:  (dice_avdevice.cpp)[ 817] showDevice:    AC3 enable        : 0x00000000
00511579906:  (dice_avdevice.cpp)[ 820] showDevice:    Channel names     :
00511579918:  (dice_avdevice.cpp)[ 825] showDevice:      FW 1 (main)
00511579925:  (dice_avdevice.cpp)[ 825] showDevice:      FW 2 (main)
00511579927:  (dice_avdevice.cpp)[ 825] showDevice:      FW 3 (line)
00511579930:  (dice_avdevice.cpp)[ 825] showDevice:      FW 4 (line)
00511579932:  (dice_avdevice.cpp)[ 825] showDevice:      FW 5 (spdif)
00511579935:  (dice_avdevice.cpp)[ 825] showDevice:      FW 6 (spdif)
00511579936:  (dice_avdevice.cpp)[ 825] showDevice:      FW 7 (adat|tos)
00511579940:  (dice_avdevice.cpp)[ 825] showDevice:      FW 8 (adat|tos)
00511579941:  (dice_avdevice.cpp)[ 825] showDevice:      FW 9 (adat)
00511579944:  (dice_avdevice.cpp)[ 825] showDevice:      FW 10 (adat)
00511579946:  (dice_avdevice.cpp)[ 825] showDevice:      FW 11 (adat)
00511579953:  (dice_avdevice.cpp)[ 825] showDevice:      FW 12 (adat)
00511579955:  (dice_avdevice.cpp)[ 825] showDevice:      FW 13 (adat)
00511579962:  (dice_avdevice.cpp)[ 825] showDevice:      FW 14 (adat)
00511579983: Debug (devicemanager.cpp)[1279] showDeviceInfo: Clock sync sources:
00511585434: Debug (devicemanager.cpp)[1288] showDeviceInfo:  Type: AES               , Id:  0, Valid: 1, Active: 0, Locked 0, Slipping: 0, Description: TOS
00511585443: Debug (devicemanager.cpp)[1288] showDeviceInfo:  Type: AES               , Id:  3, Valid: 1, Active: 0, Locked 0, Slipping: 0, Description: S/PDIF
00511585450: Debug (devicemanager.cpp)[1288] showDeviceInfo:  Type: ADAT              , Id:  5, Valid: 1, Active: 0, Locked 0, Slipping: 0, Description: ADAT
00511585453: Debug (devicemanager.cpp)[1288] showDeviceInfo:  Type: Compound Syt Match, Id:  8, Valid: 1, Active: 0, Locked 1, Slipping: 0, Description: Unused
00511585457: Debug (devicemanager.cpp)[1288] showDeviceInfo:  Type: Compound Syt Match, Id:  9, Valid: 1, Active: 0, Locked 0, Slipping: 0, Description: Unused
00511585459: Debug (devicemanager.cpp)[1288] showDeviceInfo:  Type: Compound Syt Match, Id: 10, Valid: 1, Active: 0, Locked 0, Slipping: 0, Description: Unused
00511585463: Debug (devicemanager.cpp)[1288] showDeviceInfo:  Type: Compound Syt Match, Id: 11, Valid: 1, Active: 0, Locked 0, Slipping: 0, Description: Unused
00511585465: Debug (devicemanager.cpp)[1288] showDeviceInfo:  Type: Internal          , Id: 12, Valid: 1, Active: 1, Locked 1, Slipping: 0, Description: INTERNAL
00511596214:  (ffado-dbus-server.cpp)[ 329] main: DBUS service running
00511596225:  (ffado-dbus-server.cpp)[ 330] main: press ctrl-c to stop it & exit
00511596229: Debug (ffado-dbus-server.cpp)[ 333] main: dispatching...


----


Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
17:43:17.068 D-BUS: JACK server could not be started. Sorry
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
Thu Oct  1 17:43:16 2015: ------------------
Thu Oct  1 17:43:16 2015: Controller activated. Version 1.9.10 (unknown) built on Fri Nov 14 03:56:50 2014
Thu Oct  1 17:43:16 2015: Loading settings from "/home/kim/.config/jack/conf.xml" using expat_2.1.0 ...
Thu Oct  1 17:43:16 2015: setting parameter 'engine':'driver':'(null)' to value "firewire"
Thu Oct  1 17:43:16 2015: setting parameter 'engine':'realtime':'(null)' to value "true"
Thu Oct  1 17:43:16 2015: setting parameter 'engine':'verbose':'(null)' to value "true"
Thu Oct  1 17:43:16 2015: setting parameter 'engine':'client-timeout':'(null)' to value "500"
Thu Oct  1 17:43:16 2015: setting parameter 'drivers':'alsa':'device' to value "hw:Twin"
Thu Oct  1 17:43:16 2015: setting parameter 'drivers':'alsa':'capture' to value "hw:Twin"
Thu Oct  1 17:43:16 2015: setting parameter 'drivers':'alsa':'playback' to value "hw:Twin"
Thu Oct  1 17:43:16 2015: setting parameter 'drivers':'alsa':'rate' to value "44100"
Thu Oct  1 17:43:16 2015: setting parameter 'drivers':'alsa':'period' to value "512"
Thu Oct  1 17:43:16 2015: setting parameter 'drivers':'alsa':'nperiods' to value "3"
Thu Oct  1 17:43:16 2015: setting parameter 'drivers':'alsa':'hwmon' to value "false"
Thu Oct  1 17:43:16 2015: setting parameter 'drivers':'alsa':'hwmeter' to value "false"
Thu Oct  1 17:43:16 2015: setting parameter 'drivers':'alsa':'duplex' to value "true"
Thu Oct  1 17:43:16 2015: setting parameter 'drivers':'alsa':'softmode' to value "false"
Thu Oct  1 17:43:16 2015: setting parameter 'drivers':'alsa':'monitor' to value "false"
Thu Oct  1 17:43:16 2015: setting parameter 'drivers':'alsa':'dither' to value "n"
Thu Oct  1 17:43:16 2015: setting parameter 'drivers':'alsa':'shorts' to value "false"
Thu Oct  1 17:43:16 2015: setting parameter 'drivers':'firewire':'device' to value "hw:Twin"
Thu Oct  1 17:43:16 2015: setting parameter 'drivers':'firewire':'period' to value "512"
Thu Oct  1 17:43:16 2015: setting parameter 'drivers':'firewire':'nperiods' to value "2"
Thu Oct  1 17:43:16 2015: setting parameter 'drivers':'firewire':'rate' to value "44100"
Thu Oct  1 17:43:16 2015: setting parameter 'drivers':'firewire':'capture' to value "true"
Thu Oct  1 17:43:16 2015: setting parameter 'drivers':'firewire':'playback' to value "true"
Thu Oct  1 17:43:16 2015: setting parameter 'drivers':'firewire':'duplex' to value "true"
Thu Oct  1 17:43:16 2015: setting parameter 'drivers':'firewire':'inchannels' to value "2"
Thu Oct  1 17:43:16 2015: setting parameter 'drivers':'firewire':'outchannels' to value "2"
Thu Oct  1 17:43:16 2015: setting parameter 'drivers':'firewire':'snoop' to value "true"
Thu Oct  1 17:43:16 2015: Listening for D-Bus messages
Thu Oct  1 17:43:16 2015: Starting jack server...
Thu Oct  1 17:43:16 2015: JACK server starting in realtime mode with priority 10
Thu Oct  1 17:43:16 2015: self-connect-mode is "Don't restrict self connect requests"
Thu Oct  1 17:43:16 2015: Jack: JackPosixThread::StartImp : create non RT thread
Thu Oct  1 17:43:16 2015: Jack: JackPosixThread::ThreadHandler : start
Thu Oct  1 17:43:16 2015: Jack: JackDriver::Open capture_driver_name = 
Thu Oct  1 17:43:16 2015: Jack: JackDriver::Open playback_driver_name = 
Thu Oct  1 17:43:16 2015: Jack: Check protocol client = 8 server = 8
Thu Oct  1 17:43:16 2015: Jack: JackEngine::ClientInternalOpen: name = system
Thu Oct  1 17:43:16 2015: Jack: JackEngine::AllocateRefNum ref = 0
Thu Oct  1 17:43:16 2015: Jack: JackPosixSemaphore::Allocate name = jack_sem.1000_default_system val = 0
Thu Oct  1 17:43:16 2015: Jack: JackEngine::NotifyAddClient: name = system
Thu Oct  1 17:43:16 2015: Jack: JackGraphManager::SetBufferSize size = 512
Thu Oct  1 17:43:16 2015: Jack: JackConnectionManager::DirectConnect first: ref1 = 0 ref2 = 0
Thu Oct  1 17:43:16 2015: Jack: JackGraphManager::ConnectRefNum cur_index = 0 ref1 = 0 ref2 = 0
Thu Oct  1 17:43:16 2015: Jack: JackDriver::SetupDriverSync driver sem in flush mode
Thu Oct  1 17:43:16 2015: Jack: JackSocketServerChannel::Open
Thu Oct  1 17:43:16 2015: Jack: JackServerSocket::Bind : addr.sun_path /dev/shm/jack_default_1000_0
Thu Oct  1 17:43:16 2015: Jack: JackSocketServerChannel::BuildPoolTable size = 1
Thu Oct  1 17:43:16 2015: Jack: JackEngine::Open
Thu Oct  1 17:43:16 2015: Jack: JackClientSocket::Connect : addr.sun_path /dev/shm/jack_default_1000_0
Thu Oct  1 17:43:16 2015: Jack: JackEngine::ClientInternalOpen: name = freewheel
Thu Oct  1 17:43:16 2015: Jack: JackEngine::AllocateRefNum ref = 1
Thu Oct  1 17:43:16 2015: Jack: JackPosixSemaphore::Allocate name = jack_sem.1000_default_freewheel val = 0
Thu Oct  1 17:43:16 2015: Jack: JackEngine::NotifyAddClient: name = freewheel
Thu Oct  1 17:43:16 2015: Jack: JackDriver::ClientNotify ref = 1 driver = system name = freewheel notify = 0
Thu Oct  1 17:43:16 2015: Jack: JackDriver::ClientNotify ref = 0 driver = freewheel name = system notify = 0
Thu Oct  1 17:43:16 2015: Jack: JackConnectionManager::DirectConnect first: ref1 = 1 ref2 = 1
Thu Oct  1 17:43:16 2015: Jack: JackGraphManager::ConnectRefNum cur_index = 0 ref1 = 1 ref2 = 1
Thu Oct  1 17:43:16 2015: Jack: JackDriver::SetupDriverSync driver sem in flush mode
Thu Oct  1 17:43:16 2015: Jack: JackFFADODriver::Attach fBufferSize 512 fSampleRate 44100
Thu Oct  1 17:43:17 2015: ERROR: firewire MSG: Streaming thread running with Realtime scheduling, priority 15
Thu Oct  1 17:43:17 2015: ERROR: firewire MSG: Registering audio capture port firewire_pcm:0001660409c00629_FW 1 (main)_in
Thu Oct  1 17:43:17 2015: Jack: JackEngine::PortRegister ref = 0 name = firewire_pcm:0001660409c00629_FW 1 (main)_in type = 32 bit float mono audio flags = 22 buffer_size = 512
Thu Oct  1 17:43:17 2015: Jack: JackGraphManager::AllocatePortAux port_index = 1 name = firewire_pcm:0001660409c00629_FW 1 (main)_in type = 32 bit float mono audio
Thu Oct  1 17:43:17 2015: Jack: JackConnectionManager::AddOutputPort ref = 0 port = 1
Thu Oct  1 17:43:17 2015: Jack: JackEngine::ClientNotify: no callback for notification = 9
Thu Oct  1 17:43:17 2015: Jack: JackEngine::ClientNotify: no callback for notification = 9
Thu Oct  1 17:43:17 2015: Jack: JackFFADODriver::Attach fCapturePortList[i] 1 
Thu Oct  1 17:43:17 2015: ERROR: firewire MSG: Registering audio capture port firewire_pcm:0001660409c00629_FW 2 (main)_in
Thu Oct  1 17:43:17 2015: Jack: JackEngine::PortRegister ref = 0 name = firewire_pcm:0001660409c00629_FW 2 (main)_in type = 32 bit float mono audio flags = 22 buffer_size = 512
Thu Oct  1 17:43:17 2015: Jack: JackGraphManager::AllocatePortAux port_index = 2 name = firewire_pcm:0001660409c00629_FW 2 (main)_in type = 32 bit float mono audio
Thu Oct  1 17:43:17 2015: Jack: JackConnectionManager::AddOutputPort ref = 0 port = 2
Thu Oct  1 17:43:17 2015: Jack: JackEngine::ClientNotify: no callback for notification = 9
Thu Oct  1 17:43:17 2015: Jack: JackEngine::ClientNotify: no callback for notification = 9
Thu Oct  1 17:43:17 2015: Jack: JackFFADODriver::Attach fCapturePortList[i] 2 
Thu Oct  1 17:43:17 2015: ERROR: firewire MSG: Registering audio capture port firewire_pcm:0001660409c00629_FW 3 (line)_in
Thu Oct  1 17:43:17 2015: Jack: JackEngine::PortRegister ref = 0 name = firewire_pcm:0001660409c00629_FW 3 (line)_in type = 32 bit float mono audio flags = 22 buffer_size = 512
Thu Oct  1 17:43:17 2015: Jack: JackGraphManager::AllocatePortAux port_index = 3 name = firewire_pcm:0001660409c00629_FW 3 (line)_in type = 32 bit float mono audio
Thu Oct  1 17:43:17 2015: Jack: JackConnectionManager::AddOutputPort ref = 0 port = 3
Thu Oct  1 17:43:17 2015: Jack: JackEngine::ClientNotify: no callback for notification = 9
Thu Oct  1 17:43:17 2015: Jack: JackEngine::ClientNotify: no callback for notification = 9
Thu Oct  1 17:43:17 2015: Jack: JackFFADODriver::Attach fCapturePortList[i] 3 
Thu Oct  1 17:43:17 2015: ERROR: firewire MSG: Registering audio capture port firewire_pcm:0001660409c00629_FW 4 (line)_in
Thu Oct  1 17:43:17 2015: Jack: JackEngine::PortRegister ref = 0 name = firewire_pcm:0001660409c00629_FW 4 (line)_in type = 32 bit float mono audio flags = 22 buffer_size = 512
Thu Oct  1 17:43:17 2015: Jack: JackGraphManager::AllocatePortAux port_index = 4 name = firewire_pcm:0001660409c00629_FW 4 (line)_in type = 32 bit float mono audio
Thu Oct  1 17:43:17 2015: Jack: JackConnectionManager::AddOutputPort ref = 0 port = 4
Thu Oct  1 17:43:17 2015: Jack: JackEngine::ClientNotify: no callback for notification = 9
Thu Oct  1 17:43:17 2015: Jack: JackEngine::ClientNotify: no callback for notification = 9
Thu Oct  1 17:43:17 2015: Jack: JackFFADODriver::Attach fCapturePortList[i] 4 
Thu Oct  1 17:43:17 2015: ERROR: firewire MSG: Registering audio capture port firewire_pcm:0001660409c00629_FW 5 (spdif)_in
Thu Oct  1 17:43:17 2015: Jack: JackEngine::PortRegister ref = 0 name = firewire_pcm:0001660409c00629_FW 5 (spdif)_in type = 32 bit float mono audio flags = 22 buffer_size = 512
Thu Oct  1 17:43:17 2015: Jack: JackGraphManager::AllocatePortAux port_index = 5 name = firewire_pcm:0001660409c00629_FW 5 (spdif)_in type = 32 bit float mono audio
Thu Oct  1 17:43:17 2015: Jack: JackConnectionManager::AddOutputPort ref = 0 port = 5
Thu Oct  1 17:43:17 2015: Jack: JackEngine::ClientNotify: no callback for notification = 9
Thu Oct  1 17:43:17 2015: Jack: JackEngine::ClientNotify: no callback for notification = 9
Thu Oct  1 17:43:17 2015: Jack: JackFFADODriver::Attach fCapturePortList[i] 5 
Thu Oct  1 17:43:17 2015: ERROR: firewire MSG: Registering audio capture port firewire_pcm:0001660409c00629_FW 6 (spdif)_in
Thu Oct  1 17:43:17 2015: Jack: JackEngine::PortRegister ref = 0 name = firewire_pcm:0001660409c00629_FW 6 (spdif)_in type = 32 bit float mono audio flags = 22 buffer_size = 512
Thu Oct  1 17:43:17 2015: Jack: JackGraphManager::AllocatePortAux port_index = 6 name = firewire_pcm:0001660409c00629_FW 6 (spdif)_in type = 32 bit float mono audio
Thu Oct  1 17:43:17 2015: Jack: JackConnectionManager::AddOutputPort ref = 0 port = 6
Thu Oct  1 17:43:17 2015: Jack: JackEngine::ClientNotify: no callback for notification = 9
Thu Oct  1 17:43:17 2015: Jack: JackEngine::ClientNotify: no callback for notification = 9
Thu Oct  1 17:43:17 2015: Jack: JackFFADODriver::Attach fCapturePortList[i] 6 
Thu Oct  1 17:43:17 2015: ERROR: firewire MSG: Registering audio capture port firewire_pcm:0001660409c00629_FW 7 (adat|tos)_in
Thu Oct  1 17:43:17 2015: Jack: JackEngine::PortRegister ref = 0 name = firewire_pcm:0001660409c00629_FW 7 (adat|tos)_in type = 32 bit float mono audio flags = 22 buffer_size = 512
Thu Oct  1 17:43:17 2015: Jack: JackGraphManager::AllocatePortAux port_index = 7 name = firewire_pcm:0001660409c00629_FW 7 (adat|tos)_in type = 32 bit float mono audio
Thu Oct  1 17:43:17 2015: Jack: JackConnectionManager::AddOutputPort ref = 0 port = 7
Thu Oct  1 17:43:17 2015: Jack: JackEngine::ClientNotify: no callback for notification = 9
Thu Oct  1 17:43:17 2015: Jack: JackEngine::ClientNotify: no callback for notification = 9
Thu Oct  1 17:43:17 2015: Jack: JackFFADODriver::Attach fCapturePortList[i] 7 
Thu Oct  1 17:43:17 2015: ERROR: firewire MSG: Registering audio capture port firewire_pcm:0001660409c00629_FW 8 (adat|tos)_in
Thu Oct  1 17:43:17 2015: Jack: JackEngine::PortRegister ref = 0 name = firewire_pcm:0001660409c00629_FW 8 (adat|tos)_in type = 32 bit float mono audio flags = 22 buffer_size = 512
Thu Oct  1 17:43:17 2015: Jack: JackGraphManager::AllocatePortAux port_index = 8 name = firewire_pcm:0001660409c00629_FW 8 (adat|tos)_in type = 32 bit float mono audio
Thu Oct  1 17:43:17 2015: Jack: JackConnectionManager::AddOutputPort ref = 0 port = 8
Thu Oct  1 17:43:17 2015: Jack: JackEngine::ClientNotify: no callback for notification = 9
Thu Oct  1 17:43:17 2015: Jack: JackEngine::ClientNotify: no callback for notification = 9
Thu Oct  1 17:43:17 2015: Jack: JackFFADODriver::Attach fCapturePortList[i] 8 
Thu Oct  1 17:43:17 2015: ERROR: firewire MSG: Registering audio capture port firewire_pcm:0001660409c00629_FW 9 (adat)_in
Thu Oct  1 17:43:17 2015: Jack: JackEngine::PortRegister ref = 0 name = firewire_pcm:0001660409c00629_FW 9 (adat)_in type = 32 bit float mono audio flags = 22 buffer_size = 512
Thu Oct  1 17:43:17 2015: Jack: JackGraphManager::AllocatePortAux port_index = 9 name = firewire_pcm:0001660409c00629_FW 9 (adat)_in type = 32 bit float mono audio
Thu Oct  1 17:43:17 2015: Jack: JackConnectionManager::AddOutputPort ref = 0 port = 9
Thu Oct  1 17:43:17 2015: Jack: JackEngine::ClientNotify: no callback for notification = 9
Thu Oct  1 17:43:17 2015: Jack: JackEngine::ClientNotify: no callback for notification = 9
Thu Oct  1 17:43:17 2015: Jack: JackFFADODriver::Attach fCapturePortList[i] 9 
Thu Oct  1 17:43:17 2015: ERROR: firewire MSG: Registering audio capture port firewire_pcm:0001660409c00629_FW 10 (adat)_in
Thu Oct  1 17:43:17 2015: Jack: JackEngine::PortRegister ref = 0 name = firewire_pcm:0001660409c00629_FW 10 (adat)_in type = 32 bit float mono audio flags = 22 buffer_size = 512
Thu Oct  1 17:43:17 2015: Jack: JackGraphManager::AllocatePortAux port_index = 10 name = firewire_pcm:0001660409c00629_FW 10 (adat)_in type = 32 bit float mono audio
Thu Oct  1 17:43:17 2015: Jack: JackConnectionManager::AddOutputPort ref = 0 port = 10
Thu Oct  1 17:43:17 2015: Jack: JackEngine::ClientNotify: no callback for notification = 9
Thu Oct  1 17:43:17 2015: Jack: JackEngine::ClientNotify: no callback for notification = 9
Thu Oct  1 17:43:17 2015: Jack: JackFFADODriver::Attach fCapturePortList[i] 10 
Thu Oct  1 17:43:17 2015: ERROR: firewire MSG: Registering audio capture port firewire_pcm:0001660409c00629_FW 11 (adat)_in
Thu Oct  1 17:43:17 2015: Jack: JackEngine::PortRegister ref = 0 name = firewire_pcm:0001660409c00629_FW 11 (adat)_in type = 32 bit float mono audio flags = 22 buffer_size = 512
Thu Oct  1 17:43:17 2015: Jack: JackGraphManager::AllocatePortAux port_index = 11 name = firewire_pcm:0001660409c00629_FW 11 (adat)_in type = 32 bit float mono audio
Thu Oct  1 17:43:17 2015: Jack: JackConnectionManager::AddOutputPort ref = 0 port = 11
Thu Oct  1 17:43:17 2015: Jack: JackEngine::ClientNotify: no callback for notification = 9
Thu Oct  1 17:43:17 2015: Jack: JackEngine::ClientNotify: no callback for notification = 9
Thu Oct  1 17:43:17 2015: Jack: JackFFADODriver::Attach fCapturePortList[i] 11 
Thu Oct  1 17:43:17 2015: ERROR: firewire MSG: Registering audio capture port firewire_pcm:0001660409c00629_FW 12 (adat)_in
Thu Oct  1 17:43:17 2015: Jack: JackEngine::PortRegister ref = 0 name = firewire_pcm:0001660409c00629_FW 12 (adat)_in type = 32 bit float mono audio flags = 22 buffer_size = 512
Thu Oct  1 17:43:17 2015: Jack: JackGraphManager::AllocatePortAux port_index = 12 name = firewire_pcm:0001660409c00629_FW 12 (adat)_in type = 32 bit float mono audio
Thu Oct  1 17:43:17 2015: Jack: JackConnectionManager::AddOutputPort ref = 0 port = 12
Thu Oct  1 17:43:17 2015: Jack: JackEngine::ClientNotify: no callback for notification = 9
Thu Oct  1 17:43:17 2015: Jack: JackEngine::ClientNotify: no callback for notification = 9
Thu Oct  1 17:43:17 2015: Jack: JackFFADODriver::Attach fCapturePortList[i] 12 
Thu Oct  1 17:43:17 2015: ERROR: firewire MSG: Registering audio capture port firewire_pcm:0001660409c00629_FW 13 (adat)_in
Thu Oct  1 17:43:17 2015: Jack: JackEngine::PortRegister ref = 0 name = firewire_pcm:0001660409c00629_FW 13 (adat)_in type = 32 bit float mono audio flags = 22 buffer_size = 512
Thu Oct  1 17:43:17 2015: Jack: JackGraphManager::AllocatePortAux port_index = 13 name = firewire_pcm:0001660409c00629_FW 13 (adat)_in type = 32 bit float mono audio
Thu Oct  1 17:43:17 2015: Jack: JackConnectionManager::AddOutputPort ref = 0 port = 13
Thu Oct  1 17:43:17 2015: Jack: JackEngine::ClientNotify: no callback for notification = 9
Thu Oct  1 17:43:17 2015: Jack: JackEngine::ClientNotify: no callback for notification = 9
Thu Oct  1 17:43:17 2015: Jack: JackFFADODriver::Attach fCapturePortList[i] 13 
Thu Oct  1 17:43:17 2015: ERROR: firewire MSG: Registering audio capture port firewire_pcm:0001660409c00629_FW 14 (adat)_in
Thu Oct  1 17:43:17 2015: Jack: JackEngine::PortRegister ref = 0 name = firewire_pcm:0001660409c00629_FW 14 (adat)_in type = 32 bit float mono audio flags = 22 buffer_size = 512
Thu Oct  1 17:43:17 2015: Jack: JackGraphManager::AllocatePortAux port_index = 14 name = firewire_pcm:0001660409c00629_FW 14 (adat)_in type = 32 bit float mono audio
Thu Oct  1 17:43:17 2015: Jack: JackConnectionManager::AddOutputPort ref = 0 port = 14
Thu Oct  1 17:43:17 2015: Jack: JackEngine::ClientNotify: no callback for notification = 9
Thu Oct  1 17:43:17 2015: Jack: JackEngine::ClientNotify: no callback for notification = 9
Thu Oct  1 17:43:17 2015: Jack: JackFFADODriver::Attach fCapturePortList[i] 14 
Thu Oct  1 17:43:17 2015: ERROR: firewire MSG: Registering midi capture port firewire_pcm:0001660409c00629_midi 0_in
Thu Oct  1 17:43:17 2015: Jack: JackEngine::PortRegister ref = 0 name = firewire_pcm:0001660409c00629_midi 0_in type = 8 bit raw midi flags = 22 buffer_size = 512
Thu Oct  1 17:43:17 2015: Jack: JackGraphManager::AllocatePortAux port_index = 15 name = firewire_pcm:0001660409c00629_midi 0_in type = 8 bit raw midi
Thu Oct  1 17:43:17 2015: Jack: JackConnectionManager::AddOutputPort ref = 0 port = 15
Thu Oct  1 17:43:17 2015: Jack: JackEngine::ClientNotify: no callback for notification = 9
Thu Oct  1 17:43:17 2015: Jack: JackEngine::ClientNotify: no callback for notification = 9
Thu Oct  1 17:43:17 2015: Jack: JackFFADODriver::Attach fCapturePortList[i] 15 
Thu Oct  1 17:43:17 2015: ERROR: firewire MSG: Registering audio capture port firewire_pcm:0001660409c00629_FW 1 (main)_in
Thu Oct  1 17:43:17 2015: Jack: JackEngine::PortRegister ref = 0 name = firewire_pcm:0001660409c00629_FW 1 (main)_in type = 32 bit float mono audio flags = 22 buffer_size = 512
Thu Oct  1 17:43:17 2015: ERROR: port_name "firewire_pcm:0001660409c00629_FW 1 (main)_in" already exists
Thu Oct  1 17:43:17 2015: ERROR: driver: cannot register port for firewire_pcm:0001660409c00629_FW 1 (main)_in
Thu Oct  1 17:43:17 2015: ERROR: Cannot attach audio driver
Thu Oct  1 17:43:17 2015: Jack: JackDriver::Close
Thu Oct  1 17:43:17 2015: Jack: JackConnectionManager::DirectDisconnect last: ref1 = 1 ref2 = 1
Thu Oct  1 17:43:17 2015: Jack: JackGraphManager::DisconnectRefNum cur_index = 0 ref1 = 1 ref2 = 1
Thu Oct  1 17:43:17 2015: Jack: JackEngine::ClientInternalClose ref = 1
Thu Oct  1 17:43:17 2015: Jack: JackEngine::ClientCloseAux ref = 1
Thu Oct  1 17:43:17 2015: Jack: JackGraphManager::RemoveAllPorts ref = 1
Thu Oct  1 17:43:17 2015: Jack: JackDriver::ClientNotify ref = 1 driver = system name = freewheel notify = 1
Thu Oct  1 17:43:17 2015: Jack: JackPosixSemaphore::Destroy name = jack_sem.1000_default_freewheel
Thu Oct  1 17:43:17 2015: Jack: JackEngine::Close
Thu Oct  1 17:43:17 2015: Jack: JackClientSocket::Close
Thu Oct  1 17:43:17 2015: Jack: JackServerSocket::Close /dev/shm/jack_default_1000_0
Thu Oct  1 17:43:17 2015: Jack: JackDriver::Close
Thu Oct  1 17:43:17 2015: Jack: JackConnectionManager::DirectDisconnect last: ref1 = 0 ref2 = 0
Thu Oct  1 17:43:17 2015: Jack: JackGraphManager::DisconnectRefNum cur_index = 0 ref1 = 0 ref2 = 0
Thu Oct  1 17:43:17 2015: Jack: JackEngine::ClientInternalClose ref = 0
Thu Oct  1 17:43:17 2015: Jack: JackEngine::ClientCloseAux ref = 0
Thu Oct  1 17:43:17 2015: Jack: JackEngine::PortUnRegister ref = 0 port_index = 1
Thu Oct  1 17:43:17 2015: Jack: JackEngine::PortDisconnect ref = -1 src = 1 dst = 65535
Thu Oct  1 17:43:17 2015: Jack: JackGraphManager::DisconnectAllOutput port_index = 1 
Thu Oct  1 17:43:17 2015: Jack: JackConnectionManager::RemoveOutputPort ref = 0 port_index = 1 
Thu Oct  1 17:43:17 2015: Jack: JackEngine::PortUnRegister ref = 0 port_index = 2
Thu Oct  1 17:43:17 2015: Jack: JackEngine::PortDisconnect ref = -1 src = 2 dst = 65535
Thu Oct  1 17:43:17 2015: Jack: JackGraphManager::DisconnectAllOutput port_index = 2 
Thu Oct  1 17:43:17 2015: Jack: JackConnectionManager::RemoveOutputPort ref = 0 port_index = 2 
Thu Oct  1 17:43:17 2015: Jack: JackEngine::PortUnRegister ref = 0 port_index = 3
Thu Oct  1 17:43:17 2015: Jack: JackEngine::PortDisconnect ref = -1 src = 3 dst = 65535
Thu Oct  1 17:43:17 2015: Jack: JackGraphManager::DisconnectAllOutput port_index = 3 
Thu Oct  1 17:43:17 2015: Jack: JackConnectionManager::RemoveOutputPort ref = 0 port_index = 3 
Thu Oct  1 17:43:17 2015: Jack: JackEngine::PortUnRegister ref = 0 port_index = 4
Thu Oct  1 17:43:17 2015: Jack: JackEngine::PortDisconnect ref = -1 src = 4 dst = 65535
Thu Oct  1 17:43:17 2015: Jack: JackGraphManager::DisconnectAllOutput port_index = 4 
Thu Oct  1 17:43:17 2015: Jack: JackConnectionManager::RemoveOutputPort ref = 0 port_index = 4 
Thu Oct  1 17:43:17 2015: Jack: JackEngine::PortUnRegister ref = 0 port_index = 5
Thu Oct  1 17:43:17 2015: Jack: JackEngine::PortDisconnect ref = -1 src = 5 dst = 65535
Thu Oct  1 17:43:17 2015: Jack: JackGraphManager::DisconnectAllOutput port_index = 5 
Thu Oct  1 17:43:17 2015: Jack: JackConnectionManager::RemoveOutputPort ref = 0 port_index = 5 
Thu Oct  1 17:43:17 2015: Jack: JackEngine::PortUnRegister ref = 0 port_index = 6
Thu Oct  1 17:43:17 2015: Jack: JackEngine::PortDisconnect ref = -1 src = 6 dst = 65535
Thu Oct  1 17:43:17 2015: Jack: JackGraphManager::DisconnectAllOutput port_index = 6 
Thu Oct  1 17:43:17 2015: Jack: JackConnectionManager::RemoveOutputPort ref = 0 port_index = 6 
Thu Oct  1 17:43:17 2015: Jack: JackEngine::PortUnRegister ref = 0 port_index = 7
Thu Oct  1 17:43:17 2015: Jack: JackEngine::PortDisconnect ref = -1 src = 7 dst = 65535
Thu Oct  1 17:43:17 2015: Jack: JackGraphManager::DisconnectAllOutput port_index = 7 
Thu Oct  1 17:43:17 2015: Jack: JackConnectionManager::RemoveOutputPort ref = 0 port_index = 7 
Thu Oct  1 17:43:17 2015: Jack: JackEngine::PortUnRegister ref = 0 port_index = 8
Thu Oct  1 17:43:17 2015: Jack: JackEngine::PortDisconnect ref = -1 src = 8 dst = 65535
Thu Oct  1 17:43:17 2015: Jack: JackGraphManager::DisconnectAllOutput port_index = 8 
Thu Oct  1 17:43:17 2015: Jack: JackConnectionManager::RemoveOutputPort ref = 0 port_index = 8 
Thu Oct  1 17:43:17 2015: Jack: JackEngine::PortUnRegister ref = 0 port_index = 9
Thu Oct  1 17:43:17 2015: Jack: JackEngine::PortDisconnect ref = -1 src = 9 dst = 65535
Thu Oct  1 17:43:17 2015: Jack: JackGraphManager::DisconnectAllOutput port_index = 9 
Thu Oct  1 17:43:17 2015: Jack: JackConnectionManager::RemoveOutputPort ref = 0 port_index = 9 
Thu Oct  1 17:43:17 2015: Jack: JackEngine::PortUnRegister ref = 0 port_index = 10
Thu Oct  1 17:43:17 2015: Jack: JackEngine::PortDisconnect ref = -1 src = 10 dst = 65535
Thu Oct  1 17:43:17 2015: Jack: JackGraphManager::DisconnectAllOutput port_index = 10 
Thu Oct  1 17:43:17 2015: Jack: JackConnectionManager::RemoveOutputPort ref = 0 port_index = 10 
Thu Oct  1 17:43:17 2015: Jack: JackEngine::PortUnRegister ref = 0 port_index = 11
Thu Oct  1 17:43:17 2015: Jack: JackEngine::PortDisconnect ref = -1 src = 11 dst = 65535
Thu Oct  1 17:43:17 2015: Jack: JackGraphManager::DisconnectAllOutput port_index = 11 
Thu Oct  1 17:43:17 2015: Jack: JackConnectionManager::RemoveOutputPort ref = 0 port_index = 11 
Thu Oct  1 17:43:17 2015: Jack: JackEngine::PortUnRegister ref = 0 port_index = 12
Thu Oct  1 17:43:17 2015: Jack: JackEngine::PortDisconnect ref = -1 src = 12 dst = 65535
Thu Oct  1 17:43:17 2015: Jack: JackGraphManager::DisconnectAllOutput port_index = 12 
Thu Oct  1 17:43:17 2015: Jack: JackConnectionManager::RemoveOutputPort ref = 0 port_index = 12 
Thu Oct  1 17:43:17 2015: Jack: JackEngine::PortUnRegister ref = 0 port_index = 13
Thu Oct  1 17:43:17 2015: Jack: JackEngine::PortDisconnect ref = -1 src = 13 dst = 65535
Thu Oct  1 17:43:17 2015: Jack: JackGraphManager::DisconnectAllOutput port_index = 13 
Thu Oct  1 17:43:17 2015: Jack: JackConnectionManager::RemoveOutputPort ref = 0 port_index = 13 
Thu Oct  1 17:43:17 2015: Jack: JackEngine::PortUnRegister ref = 0 port_index = 14
Thu Oct  1 17:43:17 2015: Jack: JackEngine::PortDisconnect ref = -1 src = 14 dst = 65535
Thu Oct  1 17:43:17 2015: Jack: JackGraphManager::DisconnectAllOutput port_index = 14 
Thu Oct  1 17:43:17 2015: Jack: JackConnectionManager::RemoveOutputPort ref = 0 port_index = 14 
Thu Oct  1 17:43:17 2015: Jack: JackEngine::PortUnRegister ref = 0 port_index = 15
Thu Oct  1 17:43:17 2015: Jack: JackEngine::PortDisconnect ref = -1 src = 15 dst = 65535
Thu Oct  1 17:43:17 2015: Jack: JackGraphManager::DisconnectAllOutput port_index = 15 
Thu Oct  1 17:43:17 2015: Jack: JackConnectionManager::RemoveOutputPort ref = 0 port_index = 15 
Thu Oct  1 17:43:17 2015: Jack: JackGraphManager::RemoveAllPorts ref = 0
Thu Oct  1 17:43:17 2015: Jack: JackPosixSemaphore::Destroy name = jack_sem.1000_default_system
Thu Oct  1 17:43:17 2015: Jack: no message buffer overruns
Thu Oct  1 17:43:17 2015: Jack: JackPosixThread::Stop
Thu Oct  1 17:43:17 2015: Jack: JackPosixThread::ThreadHandler : exit
Thu Oct  1 17:43:17 2015: ERROR: JackServer::Open failed with -1
Thu Oct  1 17:43:17 2015: Jack: Succeeded in unlocking 82274202 byte memory area
Thu Oct  1 17:43:17 2015: Jack: JackShmMem::delete size = 0 index = 0
Thu Oct  1 17:43:17 2015: Jack: ~JackDriver
Thu Oct  1 17:43:17 2015: Jack: ~JackDriver
Thu Oct  1 17:43:17 2015: Jack: Succeeded in unlocking 1186 byte memory area
Thu Oct  1 17:43:17 2015: Jack: JackShmMem::delete size = 0 index = 1
Thu Oct  1 17:43:17 2015: Jack: Cleaning up shared memory
Thu Oct  1 17:43:17 2015: Jack: Cleaning up files
Thu Oct  1 17:43:17 2015: Jack: Unregistering server `default'
Thu Oct  1 17:43:17 2015: ERROR: Failed to open server
Thu Oct  1 17:43:17 2015: ERROR: Segmentation Fault!
Thu Oct  1 17:43:17 2015: ERROR: Segmentation Fault!
Thu Oct  1 17:43:17 2015: ERROR: info.si_signo = 11
Thu Oct  1 17:43:17 2015: ERROR: info.si_signo = 11
Thu Oct  1 17:43:17 2015: ERROR: info.si_errno = 0
Thu Oct  1 17:43:17 2015: ERROR: info.si_errno = 0
Thu Oct  1 17:43:17 2015: ERROR: info.si_code  = 1 (SEGV_MAPERR)
Thu Oct  1 17:43:17 2015: ERROR: info.si_addr  = 0x7ff28ea207c6
Thu Oct  1 17:43:17 2015: ERROR: info.si_code  = 1 (SEGV_MAPERR)
Thu Oct  1 17:43:17 2015: ERROR: reg[00]       = 0x00000000000000d4
Thu Oct  1 17:43:17 2015: ERROR: info.si_addr  = 0x7ff28ea207c6
Thu Oct  1 17:43:17 2015: ERROR: reg[01]       = 0x00007ff28eb2b4d5
Thu Oct  1 17:43:17 2015: ERROR: reg[00]       = 0x00000000000000d4
Thu Oct  1 17:43:17 2015: ERROR: reg[02]       = 0x00007ff268000030
Thu Oct  1 17:43:17 2015: ERROR: reg[01]       = 0x00007ff28eb2b4d5
Thu Oct  1 17:43:17 2015: ERROR: reg[03]       = 0x0000000000000000
Thu Oct  1 17:43:17 2015: ERROR: reg[02]       = 0x00007ff25c000030
Thu Oct  1 17:43:17 2015: ERROR: reg[04]       = 0x00007ff29333c660
Thu Oct  1 17:43:17 2015: ERROR: reg[03]       = 0x0000000000000000
Thu Oct  1 17:43:17 2015: ERROR: reg[05]       = 0x00000000010e9ba0
Thu Oct  1 17:43:17 2015: ERROR: reg[04]       = 0x00007ff29333c660
Thu Oct  1 17:43:17 2015: ERROR: reg[06]       = 0x00007ff28eb2d621
Thu Oct  1 17:43:17 2015: ERROR: reg[05]       = 0x00000000010e9da0
Thu Oct  1 17:43:17 2015: ERROR: reg[07]       = 0x0000000000000000
Thu Oct  1 17:43:17 2015: ERROR: reg[06]       = 0x00007ff28eb2d69a
Thu Oct  1 17:43:17 2015: ERROR: reg[08]       = 0x0000000000000000
Thu Oct  1 17:43:17 2015: ERROR: reg[07]       = 0x0000000000000000
Thu Oct  1 17:43:17 2015: ERROR: reg[09]       = 0x0000000000000000
Thu Oct  1 17:43:17 2015: ERROR: reg[08]       = 0x0000000000000000
Thu Oct  1 17:43:17 2015: ERROR: reg[10]       = 0x00007ff28edac6e0
Thu Oct  1 17:43:17 2015: ERROR: reg[11]       = 0x00000000010e9ba0
Thu Oct  1 17:43:17 2015: ERROR: reg[09]       = 0x0000000000000000
Thu Oct  1 17:43:17 2015: ERROR: reg[12]       = 0x0000000000000000
Thu Oct  1 17:43:17 2015: ERROR: reg[10]       = 0x00007ff28edac6e0
Thu Oct  1 17:43:17 2015: ERROR: reg[13]       = 0x0000000000000000
Thu Oct  1 17:43:17 2015: ERROR: reg[11]       = 0x00000000010e9da0
Thu Oct  1 17:43:17 2015: ERROR: reg[14]       = 0x00007ff292d2ec4d
Thu Oct  1 17:43:17 2015: ERROR: reg[12]       = 0x0000000000000000
Thu Oct  1 17:43:17 2015: ERROR: reg[15]       = 0x00007ff281e1ce50
Thu Oct  1 17:43:17 2015: ERROR: reg[13]       = 0x0000000000000000
Thu Oct  1 17:43:17 2015: ERROR: reg[16]       = 0x00007ff28ea207c6
Thu Oct  1 17:43:17 2015: ERROR: reg[14]       = 0x00007ff292d2ec4d
Thu Oct  1 17:43:17 2015: ERROR: reg[15]       = 0x00007ff28161be50
Thu Oct  1 17:43:17 2015: ERROR: reg[17]       = 0x0000000000010206
Thu Oct  1 17:43:17 2015: ERROR: reg[16]       = 0x00007ff28ea207c6
Thu Oct  1 17:43:17 2015: ERROR: reg[18]       = 0x0000000000000033
Thu Oct  1 17:43:17 2015: ERROR: reg[17]       = 0x0000000000010206
Thu Oct  1 17:43:17 2015: ERROR: reg[19]       = 0x0000000000000014
Thu Oct  1 17:43:17 2015: ERROR: reg[18]       = 0x0000000000000033
Thu Oct  1 17:43:17 2015: ERROR: reg[20]       = 0x000000000000000e
Thu Oct  1 17:43:17 2015: ERROR: reg[19]       = 0x0000000000000014
Thu Oct  1 17:43:17 2015: ERROR: reg[21]       = 0x0000000000005a07
Thu Oct  1 17:43:17 2015: ERROR: reg[20]       = 0x000000000000000e
Thu Oct  1 17:43:17 2015: ERROR: reg[21]       = 0x0000000000005a07
Thu Oct  1 17:43:17 2015: ERROR: reg[22]       = 0x00007ff28ea207c6
Thu Oct  1 17:43:17 2015: ERROR: reg[22]       = 0x00007ff28ea207c6
Thu Oct  1 17:43:17 2015: ERROR: Stack trace:
Thu Oct  1 17:43:17 2015: ERROR: Stack trace:
Thu Oct  1 17:43:17 2015: ERROR: End of stack trace
Thu Oct  1 17:43:17 2015: ERROR: End of stack trace
17:43:19.098 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
```

---

