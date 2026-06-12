---
title: "No Sound on D945GCLF - Maybe a bug?"
date: 2009-04-25
forum: Multimedia Software
---

### Post by neilneil2000 on 2009-04-25
I can't get any sound from my [D945GCLF]("http://www.intel.com/Products/Desktop/Motherboards/D945GCLF/D945GCLF-overview.htm") board.  I seem to remember it working many moons ago but I can't remember what version of Ubuntu I was running at the time (I think it was 8.04 Desktop Edition)

I have been running 8.10 Desktop since it was released (sound didn't work), until about a month ago.  Then I did a fresh install with 8.10 Server (still no sound).  I upgraded to 9.04 yesterday and still no sound.

I tried a few things, like removing pulse and took a few snapshots using the alsa_info.sh script.  The output of those are here:

[alsa_info.sh - Take 1]("http://www.alsa-project.org/db/?f=7306f40e82f2009cae70e9737f879c32b9358c5c")
[alsa_info.sh - Take 2]("http://www.alsa-project.org/db/?f=4b8a63371fe23fa787c1cf1e3c5d75ed411c3688")
[alsa_info.sh - Take 3 (Pulse removed)]("http://www.alsa-project.org/db/?f=acf5e540d9b30ca1f2c1a5285a3be96ebe00ae16")

I did see that pulse wasn't running in the first two instances but removed it anyway just to make sure.  One thing I did notice however was that even with pulse removed, the option to choose "Pulseaudio Server" still exists in gnome-sound-properties.

I have followed the sticky on this topic at [http://ubuntuforums.org/showthread.php?t=769492]("http://ubuntuforums.org/showthread.php?t=769492")

However I still can't get anything working so have created this thread.

Here is the output I grabbed from following that guide:


1)
```
neil@Mediacentre:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC662 Analog [ALC662 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #

```
2)
```
neil@Mediacentre:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
	Subsystem: Intel Corporation Device 464c
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
	Subsystem: Intel Corporation Device 464c
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at 90200000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at 20c0 [size=8]
	Memory at 80000000 (32-bit, prefetchable) [size=256M]
	Memory at 90280000 (32-bit, non-prefetchable) [size=256K]
	Capabilities: <access denied>
	Kernel modules: intelfb

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
	Subsystem: Intel Corporation Device d603
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at 902c0000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00001000-00001fff
	Memory behind bridge: 90100000-901fffff
	Prefetchable memory behind bridge: 0000000090000000-00000000900fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
	Subsystem: Intel Corporation Device 464c
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at 2060 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
	Subsystem: Intel Corporation Device 464c
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 2040 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
	Subsystem: Intel Corporation Device 464c
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 2020 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01) (prog-if 20)
	Subsystem: Intel Corporation Device 464c
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at 902c4000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=32
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
	Subsystem: Intel Corporation Device 464c
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
	Subsystem: Intel Corporation Device 464c
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 2090 [size=16]
	Kernel driver in use: ata_piix

00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: Intel Corporation Device 464c
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
	I/O ports at 20a8 [size=8]
	I/O ports at 20cc [size=4]
	I/O ports at 20a0 [size=8]
	I/O ports at 20c8 [size=4]
	I/O ports at 2080 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
	Subsystem: Intel Corporation Device 464c
	Flags: medium devsel, IRQ 11
	I/O ports at 2000 [size=32]
	Kernel modules: i2c-i801

01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
	Subsystem: Intel Corporation Device 0001
	Flags: bus master, fast devsel, latency 0, IRQ 2300
	I/O ports at 1000 [size=256]
	Memory at 90100000 (64-bit, non-prefetchable) [size=4K]
	Memory at 90000000 (64-bit, prefetchable) [size=64K]
	[virtual] Expansion ROM at 90020000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: r8101
	Kernel modules: r8101, r8169

```
3)
Yes ICH7 family is supported

4)
neil@Mediacentre:~$ sudo modprobe snd-hda-intel
<NO OUTPUT>

/* Getting the ALSA drivers from a *fresh* kernel */

```
neil@Mediacentre:~$ aplay -l
aplay: device_list:217: no soundcards found...
```

/* ALSA driver compilation */

I used the module assistant and compiled with snd-hda-intel

```
neil@Mediacentre:~$ sudo modprobe snd-hda-intel 
WARNING: Error inserting snd_page_alloc (/lib/modules/2.6.28-11-server/updates/alsa/acore/snd-page-alloc.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_timer (/lib/modules/2.6.28-11-server/updates/alsa/acore/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_pcm (/lib/modules/2.6.28-11-server/updates/alsa/acore/snd-pcm.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.28-11-server/updates/alsa/pci/hda/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

Once I rebooted a second time

neil@Mediacentre:~$ sudo modprobe snd-hda-intel gives no output and

```
neil@Mediacentre:~$ aplay -l
aplay: device_list:217: no soundcards found...
```

Any ideas would be most welcome!!!

Here is the output from lsmod
```
Module                  Size  Used by
binfmt_misc            16776  1 
i915                   65540  2 
drm                    96424  3 i915
bridge                 56212  0 
stp                    10500  1 bridge
bnep                   20224  2 
ipt_ULOG               15140  1 
r8101                  39056  0 
video                  25360  0 
output                 11008  1 video
input_polldev          11784  0 
iptable_filter         10752  0 
iptable_mangle         10880  0 
iptable_nat            13700  0 
nf_nat                 25876  1 iptable_nat
nf_conntrack_ipv4      21388  3 iptable_nat,nf_nat
nf_conntrack           72008  3 iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4          9984  1 nf_conntrack_ipv4
ip_tables              19472  3 iptable_filter,iptable_mangle,iptable_nat
x_tables               23044  3 ipt_ULOG,iptable_nat,ip_tables
lp                     17156  0 
snd_hda_intel         452756  0 
snd_pcm_oss            53024  0 
snd_mixer_oss          23040  1 snd_pcm_oss
snd_pcm                88580  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         17160  2 snd_hda_intel,snd_pcm
snd_hwdep              15364  1 snd_hda_intel
snd_seq_oss            39552  0 
snd_seq_midi           14208  0 
snd_rawmidi            29568  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                61296  5 snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15372  4 snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
psmouse                61972  0 
iTCO_wdt               19236  0 
ppdev                  15492  0 
iTCO_vendor_support    11652  1 iTCO_wdt
serio_raw              13316  0 
pcspkr                 10496  0 
snd                    72132  11 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq_midi_event,snd_seq,snd_timer,snd_seq_device
parport_pc             40356  1 
intel_agp              34500  1 
parport                42220  3 lp,ppdev,parport_pc
agpgart                42696  3 drm,intel_agp
soundcore              15200  1 snd
usbhid                 42464  0 
mii                    13440  0 
vesafb                 13828  1 
fbcon                  45856  72 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13696  1 fbcon
softcursor              9984  1 bitblit
neil@Mediacentre:~$ lsmod 
Module                  Size  Used by
binfmt_misc            16776  1 
i915                   65540  2 
drm                    96424  3 i915
bridge                 56212  0 
stp                    10500  1 bridge
bnep                   20224  2 
ipt_ULOG               15140  1 
r8101                  39056  0 
video                  25360  0 
output                 11008  1 video
input_polldev          11784  0 
iptable_filter         10752  0 
iptable_mangle         10880  0 
iptable_nat            13700  0 
nf_nat                 25876  1 iptable_nat
nf_conntrack_ipv4      21388  3 iptable_nat,nf_nat
nf_conntrack           72008  3 iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4          9984  1 nf_conntrack_ipv4
ip_tables              19472  3 iptable_filter,iptable_mangle,iptable_nat
x_tables               23044  3 ipt_ULOG,iptable_nat,ip_tables
lp                     17156  0 
snd_hda_intel         452756  0 
snd_pcm_oss            53024  0 
snd_mixer_oss          23040  1 snd_pcm_oss
snd_pcm                88580  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         17160  2 snd_hda_intel,snd_pcm
snd_hwdep              15364  1 snd_hda_intel
snd_seq_oss            39552  0 
snd_seq_midi           14208  0 
snd_rawmidi            29568  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                61296  5 snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15372  4 snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
psmouse                61972  0 
iTCO_wdt               19236  0 
ppdev                  15492  0 
iTCO_vendor_support    11652  1 iTCO_wdt
serio_raw              13316  0 
pcspkr                 10496  0 
snd                    72132  11 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq_midi_event,snd_seq,snd_timer,snd_seq_device
parport_pc             40356  1 
intel_agp              34500  1 
parport                42220  3 lp,ppdev,parport_pc
agpgart                42696  3 drm,intel_agp
soundcore              15200  1 snd
usbhid                 42464  0 
mii                    13440  0 
vesafb                 13828  1 
fbcon                  45856  72 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13696  1 fbcon
softcursor              9984  1 bitblit

```

---

