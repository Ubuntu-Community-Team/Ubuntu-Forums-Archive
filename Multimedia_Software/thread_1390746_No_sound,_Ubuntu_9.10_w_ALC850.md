---
title: "No sound, Ubuntu 9.10 w/ ALC850"
date: 2010-01-26
forum: Multimedia Software
---

### Post by Questor_ix on 2010-01-26
I have an ASUS A8N-E mainboard with an integrated Realtek ALC850 sound card.  I believe the southside bus is made in partnership with NVIDIA.  

On a fresh install I had no sound.  I downloaded their driver AC97 driver, alsa-driver-1.0.14-4.06a.tar.bz2, and followed the configure / make / make install steps.

On the make step, it fails thusly:

```
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
scripts/Makefile.build:49: *** CFLAGS was changed in "/home/theoden/drivers/32bit/realtek-audio/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/acore/Makefile". Fix it to use EXTRA_CFLAGS.  Stop.
make[2]: *** [/home/theoden/drivers/32bit/realtek-audio/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/acore] Error 2
make[1]: *** [_module_/home/theoden/drivers/32bit/realtek-audio/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
make: *** [compile] Error 2

```

If I attempt the following:

KBUILD_NOPEDANTIC=1 make

I get:

```
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
  CC [M]  /home/theoden/drivers/32bit/realtek-audio/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/acore/hwdep.o
/home/theoden/drivers/32bit/realtek-audio/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/acore/hwdep.c:22:26: error: sound/driver.h: No such file or directory
/home/theoden/drivers/32bit/realtek-audio/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/acore/hwdep.c: In function ‘snd_hwdep_new’:
/home/theoden/drivers/32bit/realtek-audio/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/acore/hwdep.c:377: error: implicit declaration of function ‘snd_assert’
/home/theoden/drivers/32bit/realtek-audio/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/acore/hwdep.c:377: error: expected expression before ‘return’
/home/theoden/drivers/32bit/realtek-audio/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/acore/hwdep.c:379: error: expected expression before ‘return’
/home/theoden/drivers/32bit/realtek-audio/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/acore/hwdep.c: In function ‘snd_hwdep_free’:
/home/theoden/drivers/32bit/realtek-audio/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/acore/hwdep.c:404: error: expected expression before ‘return’
/home/theoden/drivers/32bit/realtek-audio/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/acore/hwdep.c: In function ‘snd_hwdep_dev_disconnect’:
/home/theoden/drivers/32bit/realtek-audio/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/acore/hwdep.c:464: error: expected expression before ‘return’
make[3]: *** [/home/theoden/drivers/32bit/realtek-audio/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/acore/hwdep.o] Error 1
make[2]: *** [/home/theoden/drivers/32bit/realtek-audio/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/acore] Error 2
make[1]: *** [_module_/home/theoden/drivers/32bit/realtek-audio/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
make: *** [compile] Error 2

```

So, I followed the "[Comprehensive Sound Guide]("http://ubuntuforums.org/showthread.php?t=205449&highlight=ac97")" and when at last I was at "Using alsa-source" step 4, I did not see a "Realtek" or "ALC850" driver amongst the possibilities.  

Nothing else in the sound guide helped, either.  

Here are some command outputs for your review:

```
~/drivers/32bit/realtek-audio/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
 
```
~/drivers/32bit/realtek-audio/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
theoden@meduseld:~/drivers/32bit/realtek-audio/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a$ lspci -v
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
	Subsystem: ASUSTeK Computer Inc. Device 815a
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: <access denied>

00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
	Subsystem: ASUSTeK Computer Inc. Device 815a
	Flags: bus master, 66MHz, fast devsel, latency 0

00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
	Subsystem: ASUSTeK Computer Inc. Device 815a
	Flags: 66MHz, fast devsel, IRQ 5
	I/O ports at e400 [size=32]
	I/O ports at 4c00 [size=64]
	I/O ports at 4c40 [size=64]
	Capabilities: <access denied>
	Kernel driver in use: nForce2_smbus
	Kernel modules: i2c-nforce2

00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2) (prog-if 10)
	Subsystem: ASUSTeK Computer Inc. Device 815a
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
	Memory at d3004000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ohci_hcd

00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3) (prog-if 20)
	Subsystem: ASUSTeK Computer Inc. Device 815a
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
	Memory at feb00000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
	Subsystem: ASUSTeK Computer Inc. Device 812a
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	I/O ports at dc00 [size=256]
	I/O ports at e000 [size=256]
	Memory at d3003000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0

00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2) (prog-if 8a [Master SecP PriP])
	Subsystem: ASUSTeK Computer Inc. Device 815a
	Flags: bus master, 66MHz, fast devsel, latency 0
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at f000 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: pata_amd

00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3) (prog-if 85 [Master SecO PriO])
	Subsystem: ASUSTeK Computer Inc. Device 815a
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	I/O ports at 09f0 [size=8]
	I/O ports at 0bf0 [size=4]
	I/O ports at 0970 [size=8]
	I/O ports at 0b70 [size=4]
	I/O ports at d800 [size=16]
	Memory at d3002000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: sata_nv

00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3) (prog-if 85 [Master SecO PriO])
	Subsystem: ASUSTeK Computer Inc. Device 815a
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	I/O ports at 09e0 [size=8]
	I/O ports at 0be0 [size=4]
	I/O ports at 0960 [size=8]
	I/O ports at 0b60 [size=4]
	I/O ports at c400 [size=16]
	Memory at d3001000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: sata_nv

00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2) (prog-if 01)
	Flags: bus master, 66MHz, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=128

00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
	Subsystem: ASUSTeK Computer Inc. Device 8141
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	Memory at d3000000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at b000 [size=8]
	Capabilities: <access denied>
	Kernel driver in use: forcedeth
	Kernel modules: forcedeth

00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: d0000000-d2ffffff
	Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
	Flags: fast devsel
	Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
	Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
	Flags: fast devsel
	Kernel driver in use: k8temp
	Kernel modules: k8temp

01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7800 GT] (rev a1)
	Subsystem: eVga.com. Corp. Device c517
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at d0000000 (32-bit, non-prefetchable) [size=16M]
	Memory at c0000000 (64-bit, prefetchable) [size=256M]
	Memory at d1000000 (64-bit, non-prefetchable) [size=16M]
	I/O ports at a000 [size=128]
	[virtual] Expansion ROM at d2000000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia, nvidiafb

```

```
~/drivers/32bit/realtek-audio/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a$ alsamixer
alsamixer: relocation error: alsamixer: symbol snd_mixer_selem_is_enum_capture, version ALSA_0.9 not defined in file libasound.so.2 with link time reference

```

In closing, I do like Ubuntu but going without sound is disappointing.  I would rather not.  If you can help, I would greatly appreciate it.  I will gladly try anything that you suggest.  

Thank you!

---

### Post by amaroKer on 2010-01-26
Is it off mute?  I've been fooled...

---

### Post by Questor21 on 2010-01-26
Yeah I moved the slider towards max volume, but nada.

---

### Post by Questor_ix on 2010-01-26
Bump

---

### Post by Yellow Pasque on 2010-01-27
That sound guide is terribly dated. I don't know hwy it's still stickied.. :\
If you want to build the latest ALSA: [http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)

FYI, your sound chip is 'driven' by the snd-hda-intel driver.

---

### Post by Questor_ix on 2010-02-01
> **Temüjin said:**
> That sound guide is terribly dated. I don't know hwy it's still stickied.. :\
If you want to build the latest ALSA: [http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)

FYI, your sound chip is 'driven' by the snd-hda-intel driver.

Thank you, by telling me that my driver is the snd-hda-intel driver, you have resolved my issue!

---

### Post by Rodney9 on 2012-03-17
wrong post sorry

---

