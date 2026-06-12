---
title: "Trying to make the PC sound card work - stuck."
date: 2008-08-03
forum: Multimedia Software
---

### Post by capricon on 2008-08-03
Hello,
Never had sound of of my PC and was troubleshooting 
Following the comprehensive guide and got stuck in the following step.

*If you chose module-assistant*

```
sudo module-assistant a-i   alsa-source
```

I am getting the following error:

```

&#9474; /usr/src/modules/alsa-driver/include/adriver.h: In function                &#9618; 
 &#9474; ‘snd_pci_orig_restore_state’:                                              &#9618; 
 &#9474; /usr/src/modules/alsa-driver/include/adriver.h:1103: error: too many       &#9618; 
 &#9474; arguments to function ‘pci_restore_state’                                  &#9618; 
 &#9474; make[6]: *** [/usr/src/modules/alsa-driver/acore/memalloc.o] Error 1       &#9618; 
 &#9474; make[5]: *** [/usr/src/modules/alsa-driver/acore] Error 2                  &#9618; 
 &#9474; make[4]: *** [_module_/usr/src/modules/alsa-driver] Error 2                &#9618; 
 &#9474; make[3]: *** [modules] Error 2                                             &#9618; 
 &#9474; make[3]: Leaving directory `/usr/src/linux-headers-2.6.20-17-generic'      &#9618; 
 &#9474; make[2]: *** [compile] Error 2                                             &#9618; 
 &#9474; make[2]: Leaving directory `/usr/src/modules/alsa-driver'                  &#9618; 
 &#9474; make[1]: *** [build-stamp] Error 2                                         &#9618; 
 &#9474; make[1]: Leaving directory `/usr/src/modules/alsa-driver'                  &#9646; 
 &#9474; make: *** [kdist_image] Error 2 

```


Please help.

Other info:
```

arsa@arsa-desktop:~$ aplay -l**** List of PLAYBACK Hardware Devices ****
card 0: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 4/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```

arsa@arsa-desktop:~$ lspci -v
00:00.0 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
        Subsystem: Elitegroup Computer Systems Unknown device 2122
        Flags: bus master, 66MHz, medium devsel, latency 8
        Memory at f8000000 (32-bit, prefetchable) [size=64M]
        Capabilities: <access denied>

00:00.1 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
        Subsystem: Elitegroup Computer Systems Unknown device 2122
        Flags: bus master, medium devsel, latency 0

00:00.2 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
        Subsystem: Elitegroup Computer Systems Unknown device 2122
        Flags: bus master, medium devsel, latency 0

00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
        Flags: bus master, medium devsel, latency 0

00:00.4 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
        Subsystem: Elitegroup Computer Systems Unknown device 2122
        Flags: bus master, medium devsel, latency 0

00:00.7 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
        Subsystem: Elitegroup Computer Systems Unknown device 2122
        Flags: bus master, medium devsel, latency 0

00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        Memory behind bridge: fca00000-feafffff
        Prefetchable memory behind bridge: eff00000-f7efffff
        Capabilities: <access denied>

00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: Elitegroup Computer Systems Unknown device 2122
        Flags: bus master, medium devsel, latency 64, IRQ 17
        I/O ports at ec00 [size=8]
        I/O ports at e880 [size=4]
        I/O ports at e800 [size=8]
        I/O ports at e480 [size=4]
        I/O ports at e400 [size=16]
        I/O ports at e000 [size=256]
        Capabilities: <access denied>

00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06) (prog-if 8a [Master SecP PriP])
        Subsystem: Elitegroup Computer Systems Unknown device 2122
        Flags: bus master, medium devsel, latency 32, IRQ 17
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
        I/O ports at fc00 [size=16]
        Capabilities: <access denied>

00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
        Subsystem: Elitegroup Computer Systems Unknown device 2122
        Flags: bus master, medium devsel, latency 64, IRQ 16
        I/O ports at dc00 [size=32]
        Capabilities: <access denied>

00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
        Subsystem: Elitegroup Computer Systems Unknown device 2122
        Flags: bus master, medium devsel, latency 64, IRQ 16
        I/O ports at d880 [size=32]
        Capabilities: <access denied>

00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
        Subsystem: Elitegroup Computer Systems Unknown device 2122
        Flags: bus master, medium devsel, latency 64, IRQ 16
        I/O ports at d800 [size=32]
        Capabilities: <access denied>

00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
        Subsystem: Elitegroup Computer Systems Unknown device 2122
        Flags: bus master, medium devsel, latency 64, IRQ 16
        I/O ports at d480 [size=32]
        Capabilities: <access denied>

00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86) (prog-if 20 [EHCI])
        Subsystem: Elitegroup Computer Systems Unknown device 2122
        Flags: bus master, medium devsel, latency 64, IRQ 16
        Memory at febffc00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
        Subsystem: Elitegroup Computer Systems Unknown device 2122
        Flags: bus master, stepping, medium devsel, latency 0
        Capabilities: <access denied>

00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
        Subsystem: Elitegroup Computer Systems Unknown device 1877
        Flags: medium devsel, IRQ 19
        I/O ports at d000 [size=256]
        Capabilities: <access denied>

00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
        Subsystem: Elitegroup Computer Systems Unknown device 0102
        Flags: bus master, medium devsel, latency 64, IRQ 18
        I/O ports at ee00 [size=256]
        Memory at febff800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

01:00.0 VGA compatible controller: VIA Technologies, Inc. UniChrome Pro IGP (rev 01) (prog-if 00 [VGA])
        Subsystem: Elitegroup Computer Systems Unknown device 2122
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 10
        Memory at f0000000 (32-bit, prefetchable) [size=64M]
        Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
        Expansion ROM at feaf0000 [disabled] [size=64K]
        Capabilities: <access denied>

```

---

### Post by capricon on 2008-08-05
Bump for help. Please.

---

### Post by capricon on 2008-08-07
Anybody there?

---

### Post by capricon on 2008-08-13
Any ubuntu loving helpers out there ?

---

