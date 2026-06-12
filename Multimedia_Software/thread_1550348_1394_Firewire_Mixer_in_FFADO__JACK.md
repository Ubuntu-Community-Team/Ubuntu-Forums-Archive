---
title: "1394 Firewire Mixer in FFADO / JACK"
date: 2010-08-10
forum: Multimedia Software
---

### Post by Brendo613 on 2010-08-10
Really need some help with this issue.  I'm using a Phonic Helixboard 18 Universal mixer, and having NO luck configuring it for use with recording.  Using Audacity, I was able to record with one of ALSA's inputs, but it spread what should have been one channel's signal across all 8 channels, and the quality was terrible.  This tells me that the computer is using the firewire interface at least party correctly, but as far as getting FFADO to be happy with the board, I have no clue how.

```
ffado-test ListDevices
-----------------------------------------------
FFADO test and diagnostic utility
Part of the FFADO project -- www.ffado.org
Version: 2.999.0-1880
(C) 2008, Daniel Wagner, Pieter Palmers
This program comes with ABSOLUTELY NO WARRANTY.
-----------------------------------------------

=== 1394 PORT 0 ===
  Node id  GUID                  VendorId     ModelId   Vendor - Model
09317248788: Error (configrom.cpp)[ 150] initialize: Could not parse config rom of node 0 on port 0
no message buffer overruns

```

I can't possibly post everything I did in the past 5 hours of configuring and toying with installs - but I DO need to mention that I keep getting this from JACK and FFADO:

```
09544002855: Fatal (ffado.cpp)[ 174] ffado_streaming_init: There are no devices on the bus

```

as well as:

```
09544002067: Error (configrom.cpp)[ 150] initialize: Could not parse config rom of node 0 on port 0

```


What am I missing?

---

### Post by Brendo613 on 2010-08-10
Here is JACK's output

```
23:45:13.996 JACK is starting...
23:45:13.996 /usr/bin/jackd -r -p128 -u -dfirewire -r44100 -p512 -n16 -i8 -o2
jackd 0.118.0
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
23:45:14.025 JACK was started with PID=17534.
no message buffer overruns
JACK compiled with System V SHM support.
loading driver ..
10144780395:  (ffado.cpp)[  92] ffado_streaming_init: libffado 2.999.0-1880 built Aug 10 2010 19:49:42
10144793527: [31mError (configrom.cpp)[ 150] initialize: Could not parse config rom of node 0 on port 0
[0m10144800648: [31mError (configrom.cpp)[ 150] initialize: Could not parse config rom of node 0 on port 0
[0mfirewire ERR: Error creating FFADO streaming device
cannot load driver module firewire
no message buffer overruns
23:45:15.705 JACK was stopped successfully.
23:45:15.707 Post-shutdown script...
23:45:15.708 killall jackd
jackd: no process found
23:45:16.143 Post-shutdown script terminated with exit status=256.
23:45:16.597 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
```

---

### Post by cchhrriiss121212 on 2010-08-11
Check over [this]("https://help.ubuntu.com/community/FireWire") if you have not seen it. Are you using 10.04? If you are you will need to install the rt kernel.
If you are still stuck then you may find more help in[ this thread]("http://ubuntuforums.org/showthread.php?t=1505953").

---

### Post by Brendo613 on 2010-08-12
Been through a LOT in the past few days working on this.  According to FFADO's site, in order to use the new firewire stack, kernel 2.6.32 or later is needed, and version 2.0.5 or later of libraw, too.  Full [posting is here]("http://www.ffado.org/?q=node/1316"), which I will not summarize.  I noticed (reading from ffado-diag's output) that many libraries were not found, that the .pc files were not generated with pkg-config.  It turns out if you install each dependency library's "[library name]-dev" package, then the .pc files will be placed in the appropriate folder.  Basically, the .pc files are config files used by pkg-config which, in this instance, tell ffado where the library files are.  Otherwise, without the dependency libraries' corresponding "[library name]-dev" files installed, ffado had no knowledge of where the files were located.

Furthermore, by visiting the many sites and forum posts attempting to address errors I got along the way, the notion got into my head that I need at least a 2.6.32 kernel to make FFADO work right in 10.04 (which I'm using).  Today consisted of me building a RT Patch kernel (following the guide from [the Realtime Wiki Page]("https://rt.wiki.kernel.org/index.php/RT_PREEMPT_HOWTO")), which directed me to a kernel build page at [Digital Hermit]("http://www.digitalhermit.com/linux/Kernel-Build-HOWTO.html"), a website who's title I completely empathize with.  At the LAST steps of the kernel build - using mkinitrd to create an image file of the kernel in /boot/ - I had no luck.  mkinitrd only exists in /etc/bash_completion.d/mkinitrd, but is not executable, and I get "command not found" when attempting to run "mkinitrd" in terminal.  Thus, I have no image of the new kernel I spent all day compiling, so I cannot try out the new RT kernel I think I patched correctly.  This was all done to fix the error from ffado-diag:```
ffado-diag


FFADO diagnostic utility 2.999.0-
============================
(C) 2008 Pieter Palmers


=== CHECK ===
 Base system...
  kernel version............ 2.6.31-11-rt
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
   gcc ............... gcc (Ubuntu 4.4.3-4ubuntu5) 4.4.3
   g++ ............... g++ (Ubuntu 4.4.3-4ubuntu5) 4.4.3
   PyQt4 (by pyuic4) . Python User Interface Compiler 4.7.2 for Qt version 4.6.2
   jackd ............. jackd version 0.118.0 tmpdir /dev/shm protocol 24
     path ............ /usr/bin/jackd
     flags ...........  -ljack -lpthread -lrt  
   libraw1394 ........ 2.0.5
     flags ...........  -lraw1394  
   libavc1394 ........ 0.5.3
     flags ...........  -lavc1394 -lrom1394 -lraw1394  
   libiec61883 ....... 1.2.0
     flags ...........  -liec61883 -lraw1394  
   libxml++-2.6 ...... 2.30.0
     flags ........... -pthread -I/usr/include/libxml++-2.6 -I/usr/lib/libxml++-2.6/include -I/usr/include/libxml2 -I/usr/include/glibmm-2.4 -I/usr/lib/glibmm-2.4/include -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  -pthread -lxml++-2.6 -lxml2 -lglibmm-2.4 -lgobject-2.0 -lsigc-2.0 -lgthread-2.0 -lrt -lglib-2.0  
   dbus-1 ............ 1.2.16
     flags ........... -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include  -L/lib -ldbus-1 -lpthread -lrt  
 Prerequisites (static at compile-time)...
   gcc ............... gcc (Debian 4.4.4-5) 4.4.4
   g++ ............... g++ (Debian 4.4.4-5) 4.4.4
   PyQt4 (by pyuic4) . Python User Interface Compiler 4.7.3 for Qt version 4.6.2
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
     flags ........... -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include  -ldbus-1 -lpthread -lrt  
 Hardware...
   Host controllers:
0a:09.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05) (prog-if 10 [OHCI])
	Subsystem: Acer Incorporated [ALI] Device [1025:011d]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32 (500ns min, 1000ns max), Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at f0400000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: firewire-ohci, ohci1394

   CPU info:
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Pentium(R) Dual  CPU  T2310  @ 1.46GHz
stepping	: 13
cpu MHz		: 800.000
cache size	: 1024 KB
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
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm
bogomips	: 2933.46
clflush size	: 64
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Pentium(R) Dual  CPU  T2310  @ 1.46GHz
stepping	: 13
cpu MHz		: 1467.000
cache size	: 1024 KB
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
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm
bogomips	: 2933.25
clflush size	: 64
power management:

 Configuration...
  IRQ information
Hardware Interrupts:
--------------------
 IRQ    0: PID:  None, count:         [135, 135], Sched None (priority None), drivers: ['timer']
 IRQ    1: PID:  None, count:           [16, 16], Sched None (priority None), drivers: ['i8042']
 IRQ    8: PID:  None, count:             [1, 1], Sched None (priority None), drivers: ['rtc0']
 IRQ    9: PID:  None, count:       [4211, 4211], Sched None (priority None), drivers: ['acpi']
 IRQ   12: PID:  None, count:   [147624, 147624], Sched None (priority None), drivers: ['i8042']
 IRQ   14: PID:  None, count:       [4255, 4255], Sched None (priority None), drivers: ['ata_piix']
 IRQ   15: PID:  None, count:             [0, 0], Sched None (priority None), drivers: ['ata_piix']
 IRQ   16: PID:  None, count:           [41, 41], Sched None (priority None), drivers: ['uhci_hcd:usb3', 'ohci1394']
 IRQ   17: PID:  None, count:             [1, 1], Sched None (priority None), drivers: ['mmc0', 'ath']
 IRQ   18: PID:  None, count:             [0, 0], Sched None (priority None), drivers: ['ehci_hcd:usb1', 'uhci_hcd:usb7']
 IRQ   19: PID:  None, count:             [0, 0], Sched None (priority None), drivers: ['uhci_hcd:usb6']
 IRQ   21: PID:  None, count:             [0, 0], Sched None (priority None), drivers: ['uhci_hcd:usb4']
 IRQ   22: PID:  None, count:         [140, 140], Sched None (priority None), drivers: ['HDA Intel']
 IRQ   23: PID:  None, count:           [10, 10], Sched None (priority None), drivers: ['ehci_hcd:usb2', 'uhci_hcd:usb5']
 IRQ   27: PID:  None, count:       [1942, 1942], Sched None (priority None), drivers: ['ahci']
 IRQ   28: PID:  None, count:           [21, 21], Sched None (priority None), drivers: ['i915']
 IRQ   29: PID:  None, count:             [2, 2], Sched None (priority None), drivers: ['eth0']

Software Interrupts:
--------------------


=== REPORT ===
FireWire kernel drivers:
[PASS] Kernel modules present and correctly loaded.
[PASS] /dev/raw1394 node present and accessible.

```

Couple of questions.  The line at the top, about the RT patch: False - this has me concerned, and is the basis of why I decided to build a RT kernel.  No luck there.  Oh well, maybe someone can help me.  I'm out of guesses with that mkinitrd not-existing-anywhere / not-being-runnable crap.

I don't know about this new stack / old stack discrepancy; I just want to use my new mixer.  I don't care which one I use, but from what I notice, kernel modules firewire-ohci and firewire-core are part of the new stack, while ohci1394, raw1394, sbp2, and ieee1394 are part of the old stack.  I fooled around with modprobe, lsmod, and depmod -a to come to this conclusion.  If **all** of these are loaded, ffado-diag complains that my config is bogus because both are loaded.  If I single the new stack out, ffado's report tells me that it won't be able to use the new stack, and that I need to use the old one.  This suggests I'm using the old version of ffado, 2.0 not 2.0.1, the revision that allows the new stack to be used - which is false.  I manually downloaded the 2.0.1 ffado .deb files and installed them, after completely removing ffado from synaptic.

________________________________________________________

I'm at a complete loss.  I thought I could use a RT patch, but it turns out I guess I have no idea what I'm doing, since mkinitrd commands yield me nothing.  Furthermore, ffado makes no sense, rejecting the use of the new stack.  I really, really and sincerely hope someone can give me some pointers with any of the issues mentioned here.

---

### Post by cchhrriiss121212 on 2010-08-13
There is no need to compile your own kernel, just download one from the repos or from here:
[https://launchpad.net/~abogani/+archive/ppa/+packages]("https://launchpad.net/%7Eabogani/+archive/ppa/+packages")
You might be making this a bit more complicated than it needs to be, just ask what to do before spending a few days trying to iron this all out. I would not recommend compiling your own libraries as it is just not necessary, the versions in the repos may be older but they will still work.

---

### Post by Brendo613 on 2010-08-13
I am currently using 2.6.33-29-realtime, which I got from ABogani.  I'll try installing the kernel again later today.  It's possible I didn't install it "correctly" from the site you last linked me to; which realtime files do I need to install?  There are many listed under the [linux-realtime dropdown menu.]("https://launchpad.net/~abogani/+archive/ppa/+sourcepub/1258598/+listing-archive-extra")  I know to choose the i386 architecture, but what is the realtime-pae vs. just the realtime 2.6.33-29 kernel?

And, the library work I did earlier - installing the files' associated .dev packages - was necessary for ffado-diag to have the .pc files, which pkg-config used to locate libraries with.  Without that, ffado-diag was telling me many libraries were missing, though I knew *were* installed on my computer.  I do agree, that the kernel work may have been un-needed - but like I said, I'm running 2.6.33-29-realtime right now (though possibly incorrectly installed).

Thanks for helping me through this, btw

---

### Post by cchhrriiss121212 on 2010-08-13
The pae means that you can use more than 3.2GB of RAM on a 32bit OS. 
Is there any reason you think the kernel did not install correctly? You need the headers and image installed and then update GRUB, after that make sure you boot into it by selecting it from the GRUB menu (press shift when booting).

---

### Post by Brendo613 on 2010-08-13
Wow.  I confirmed a suspicion that the mixer was defective: on my friend's macbook, version 10.4.11 of OSX, the mixer was not working correctly - was not recognized at all with neither firewire nor USB.  According to the manual, OSX 10.3.5 or older supports the Phonic Helix Board 18.  

Pause on this whole saga.

---

