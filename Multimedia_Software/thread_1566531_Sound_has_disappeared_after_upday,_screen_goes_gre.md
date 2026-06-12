---
title: "Sound has disappeared after upday, screen goes grey and locks too!"
date: 2010-09-02
forum: Multimedia Software
---

### Post by brawd on 2010-09-02
Hi all,

Last night, or was it the night before, I did quite a big update which required a restart. Since then I haven't had sound and intermittently the screen tends to go a pale grey and loses all colour. In that grey condition few buttons respond. After a couple of minutes it comes back and seems to behave itself for another five minutes or so before going through the grey cycle again.

I've just been through synaptic to ask for upgrades which have been installed.

Turning back to the sound I found nothing listed in Hardware and Output offering just a Dummy - but in stereo!! Previously I had the onboard stereo and HDMI on offer. (Not that I could get the HDMI to work with my tele).

So inputting to Terminal cat /proc/asound/version tells me I have
Advanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on Aug 26 2010 for kernel 2.6.32-24-generic (SMP).

Any and all ideas gratefully accepted.

regards,

brawd.

---

### Post by brawd on 2010-09-02
Sorry I didn't know there was a howto posted. I've been working my way through it and so far I've got this lot

dad@dad-ubuntu64:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on Aug 26 2010 for kernel 2.6.32-24-generic (SMP).
dad@dad-ubuntu64:~$ aplay -l
aplay: device_list:235: no soundcards found...
dad@dad-ubuntu64:~$ lspci -v
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
	Subsystem: ASRock Incorporation Device 03ea
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: <access denied>

00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
	Subsystem: ASRock Incorporation Device 03e0
	Flags: bus master, 66MHz, fast devsel, latency 0

00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
	Subsystem: ASRock Incorporation Device 03eb
	Flags: 66MHz, fast devsel, IRQ 11
	I/O ports at cc00 [size=64]
	I/O ports at 5000 [size=64]
	I/O ports at 6000 [size=64]
	Capabilities: <access denied>
	Kernel driver in use: nForce2_smbus
	Kernel modules: i2c-nforce2

00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
	Subsystem: ASRock Incorporation Device 03eb
	Flags: 66MHz, fast devsel

00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3) (prog-if 10)
	Subsystem: ASRock Incorporation Device 03f1
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
	Memory at ddeff000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ohci_hcd

00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3) (prog-if 20)
	Subsystem: ASRock Incorporation Device 03f2
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
	Memory at ddefec00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1) (prog-if 01)
	Flags: bus master, 66MHz, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
	Memory behind bridge: ddf00000-ddffffff
	Capabilities: <access denied>

00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
	Subsystem: ASRock Incorporation Device 3662
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 11
	Memory at ddef8000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel modules: snd-hda-intel

00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2) (prog-if 8a [Master SecP PriP])
	Subsystem: ASRock Incorporation Device 03ec
	Flags: bus master, 66MHz, fast devsel, latency 0
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at ffa0 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: pata_amd
	Kernel modules: pata_amd

00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
	Subsystem: ASRock Incorporation Device 03ef
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 27
	Memory at ddefd000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at c480 [size=8]
	Capabilities: <access denied>
	Kernel driver in use: forcedeth
	Kernel modules: forcedeth

00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2) (prog-if 85 [Master SecO PriO])
	Subsystem: ASRock Incorporation Device 03f6
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	I/O ports at c400 [size=8]
	I/O ports at c080 [size=4]
	I/O ports at c000 [size=8]
	I/O ports at bc00 [size=4]
	I/O ports at b880 [size=16]
	Memory at ddefc000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: sata_nv
	Kernel modules: sata_nv

00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2) (prog-if 85 [Master SecO PriO])
	Subsystem: ASRock Incorporation Device 03f6
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	I/O ports at b800 [size=8]
	I/O ports at b480 [size=4]
	I/O ports at b400 [size=8]
	I/O ports at b080 [size=4]
	I/O ports at b000 [size=16]
	Memory at ddef7000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: sata_nv
	Kernel modules: sata_nv

00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: de000000-df7fffff
	Prefetchable memory behind bridge: 00000000c0000000-00000000d9ffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=04, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: df800000-dfffffff
	Prefetchable memory behind bridge: 00000000da000000-00000000dcffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
	Flags: fast devsel
	Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
	Flags: fast devsel
	Kernel modules: amd64_edac_mod

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
	Flags: fast devsel
	Capabilities: <access denied>
	Kernel driver in use: k8temp
	Kernel modules: k8temp

01:08.0 Network controller: RaLink Device 3060
	Subsystem: Edimax Computer Co. Device 7711
	Flags: bus master, slow devsel, latency 32, IRQ 11
	Memory at ddff0000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>

02:00.0 VGA compatible controller: nVidia Corporation GT216 [GeForce GT 220] (rev a2)
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at de000000 (32-bit, non-prefetchable) [size=16M]
	Memory at c0000000 (64-bit, prefetchable) [size=256M]
	Memory at d8000000 (64-bit, prefetchable) [size=32M]
	I/O ports at dc00 [size=128]
	[virtual] Expansion ROM at df780000 [disabled] [size=512K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia-current, nvidiafb, nouveau

02:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
	Flags: bus master, fast devsel, latency 0, IRQ 10
	Memory at df77c000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel modules: snd-hda-intel

dad@dad-ubuntu64:~$ sudo modprobe snd-
[sudo] password for dad: 
WARNING: /etc/modprobe.d/blacklist.conf line 56: ignoring bad line starting with 'blacklist.rt2800usb'
FATAL: Module snd_ not found.
dad@dad-ubuntu64:~$ sudo modprobe snd-
WARNING: /etc/modprobe.d/blacklist.conf line 56: ignoring bad line starting with 'blacklist.rt2800usb'
FATAL: Module snd_ not found.
dad@dad-ubuntu64:~$ alsamixer
cannot open mixer: No such file or directory
dad@dad-ubuntu64:~$ sudo modprobe snd-

It's nothing that makes sense to me but I hope it helps.

regards,

brawd.

---

### Post by brawd on 2010-09-02
Ok all resolved - for the present.

I re-installed the Alsa drivers from here

[http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/)

and life is once again a bowl of cherries.

regards,

brawd.

---

