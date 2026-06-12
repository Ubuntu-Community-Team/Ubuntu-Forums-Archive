---
title: "Presonus Firepod, JACK, xruns (not just a newbie with these issues.)"
date: 2011-02-24
forum: Multimedia Software
---

### Post by Brendo613 on 2011-02-24
I've been reluctant to start a new forum post because of the amount of information I've learned by searching previous postings; however, I am ready to admit to the online community (as I turn to you for help) that I do not understand how to get a reliable multitrack recording setup set up.

This is how I've been running my system.  I have 8 mic channels coming in from the Presonus Firepod.  The computer is a Pentium dual core 1.46GHz.  Using A. Bogani's 2.6.38-1-lowlatency kernel while running Ubuntu 10.10, I open JACK with "gksudo qjackctl," start the server, then invoke Audacity the same way.  (JACK needs to be run as root, otherwise I can't get realtime to work, I believe because of a cgroups issue; Audacity must be run as root, else it doesn't "see" JACK running.)

**JACK incurs xruns.**  JACK is ignorantly configured:
[LIST]
[*]realtime enabled
[*]memory unlocked
[*]priority: 89
[*]frames/period: 512
[*]44100k
[*]periods/buffer: 8
[*]port maximum: 128
[*]1sec startup delay
[*]timeout: 500ms
[*]default interface; capture only; input channels: default
[/LIST]

[center]**the issue**[/center]
JACK crashes, which crashes Audacity and I lose my work; I also incur xruns [seemingly] unpredictably, if I am lucky enough to not have JACK crash.  I can't start JACK again without powering off/on the board or unplugging/replugging the   data cable.  I haven't caught an error log where JACK has out and out crashed, but I do have a log saved from today.  I was recording 8 inputs when this happened, using only one mic  (can't figure out how to single out one channel out a time).  

```
[...]
Jack: fPollTable i = 1 fd = 51
Jack: fPollTable i = 2 fd = 52
Jack: fPollTable i = 3 fd = 54
Jack: fPollTable i = 1 fd = 51
Jack: fPollTable i = 2 fd = 52
Jack: fPollTable i = 3 fd = 54
Jack: FFADO XRun
JackAudioDriver::ProcessAsync: read error, skip cycle
18:46:08.988 XRUN callback (1).
Jack: fPollTable i = 1 fd = 51
Jack: JackRequest::Notification
Jack: JackEngine::NotifyClient: no callback for event = 3
Jack: JackEngine::NotifyClient: no callback for event = 3
JackPosixMutex::Unlock res = 1
Jack: JackExternalClient::ClientNotify ref = 2 name = qjackctl notify = 3
JackPosixMutex::Unlock res = 1
Jack: JackExternalClient::ClientNotify ref = 3 name = PortAudio notify = 3
Jack: fPollTable i = 2 fd = 52
Jack: fPollTable i = 3 fd = 54
[...]
```

Look at this error message - it mentions a FFADO xrun.  When I run ffado-diag, I get:
```
FFADO diagnostic utility 2.999.0-
============================
(C) 2008 Pieter Palmers


=== CHECK ===
 Base system...
  kernel version............ 2.6.38-1-lowlatency
FIXME: implement test for RT kernel
   RT patched............... False
  old 1394 stack present.... False
  old 1394 stack loaded..... False
  old 1394 stack active..... False
  new 1394 stack present.... True
  new 1394 stack loaded..... True
  new 1394 stack active..... True
  /dev/raw1394 node present. False
 Prerequisites (dynamic at run-time)...
   gcc ............... gcc (Ubuntu/Linaro 4.4.4-14ubuntu5) 4.4.5
   g++ ............... sh: g++: not found
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
0a:09.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05) (prog-if 10 [OHCI])
	Subsystem: Acer Incorporated [ALI] Device [1025:011d]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32 (500ns min, 1000ns max), Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at f0400000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: [dc] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=2 PME+
	Kernel driver in use: firewire_ohci
	Kernel modules: firewire-ohci

   CPU info:
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Pentium(R) Dual  CPU  T2310  @ 1.46GHz
stepping	: 13
cpu MHz		: 1467.000
cache size	: 1024 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm dts
bogomips	: 2933.55
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Pentium(R) Dual  CPU  T2310  @ 1.46GHz
stepping	: 13
cpu MHz		: 800.000
cache size	: 1024 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm dts
bogomips	: 2933.26
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

 Configuration...
  IRQ information
Hardware Interrupts:
--------------------
 IRQ    0: PID:  None, count: [7523629, 7523629], Sched None (priority None), drivers: ['timer']
 IRQ    1: PID:  None, count:     [17397, 17397], Sched None (priority None), drivers: ['i8042']
 IRQ    8: PID:  None, count:             [1, 1], Sched None (priority None), drivers: ['rtc0']
 IRQ    9: PID:  None, count:       [1489, 1489], Sched None (priority None), drivers: ['acpi']
 IRQ   12: PID:  None, count:           [51, 51], Sched None (priority None), drivers: ['i8042']
 IRQ   14: PID:  None, count:     [16882, 16882], Sched None (priority None), drivers: ['ata_piix']
 IRQ   15: PID:  None, count:             [0, 0], Sched None (priority None), drivers: ['ata_piix']
 IRQ   16: PID:  None, count: [1750897, 1750897], Sched None (priority None), drivers: ['uhci_hcd:usb3', 'firewire_ohci']
 IRQ   17: PID:  None, count:   [184463, 184463], Sched None (priority None), drivers: ['mmc0', 'r852', 'ath']
 IRQ   18: PID:  None, count:             [0, 0], Sched None (priority None), drivers: ['ehci_hcd:usb1', 'uhci_hcd:usb7']
 IRQ   19: PID:  None, count:             [0, 0], Sched None (priority None), drivers: ['uhci_hcd:usb6']
 IRQ   21: PID:  None, count:             [0, 0], Sched None (priority None), drivers: ['uhci_hcd:usb4']
 IRQ   23: PID:  None, count:           [10, 10], Sched None (priority None), drivers: ['ehci_hcd:usb2', 'uhci_hcd:usb5']
 IRQ   43: PID:  None, count:     [46437, 46437], Sched None (priority None), drivers: ['ahci']
 IRQ   44: PID:  None, count:         [477, 477], Sched None (priority None), drivers: ['i915']
 IRQ   45: PID:  None, count:             [3, 3], Sched None (priority None), drivers: ['eth0']
 IRQ   46: PID:  None, count:         [179, 179], Sched None (priority None), drivers: ['hda_intel']

Software Interrupts:
--------------------


=== REPORT ===
FireWire kernel drivers:

The new FireWire kernel stack is loaded. 
This stack is not supported by FFADO. Please use the old stack.

```

How is FFADO being used by JACK, when the stack it requires is not loaded?
Today, while recording vocals only (nothing on playback), I noticed a ~1sec repeated line of what I had just sung being played back through the speakers; I also saw the output meter on Audacity rise in correspondence with the audio played.  If this playback glitch happens while recording, could this be screwing with the "buffer zone" and overloading it?  The xruns and instability can't be caused by other programs' workloads - there have been times when nothing else is open and xruns occur, as well as vice versa.

Please help!  I don't want to give up on Linux, just to record.

---

### Post by Brendo613 on 2011-02-28
[A sister thread]("http://ubuntuforums.org/showthread.php?p=10506815") has been started in the Ubuntu Studio section of the site.  Still needing help in this matter

---

