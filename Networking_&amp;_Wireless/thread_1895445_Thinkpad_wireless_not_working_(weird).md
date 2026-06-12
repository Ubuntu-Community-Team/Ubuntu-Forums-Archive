---
title: "Thinkpad wireless not working (weird)"
date: 2011-12-14
forum: Networking &amp; Wireless
---

### Post by blommethomas on 2011-12-14
Hi all,

without any real reason my wireless stopped working on my Thinkpad laptop.  anyone who can help me out, I've been searching around the web for a while.  A lot of similar problems seem to exist, but none of the solutions proposed there worked for me.

Hope you can help me out on this!

(fyi: i have a dual boot with windows, wireless still works there)

```

thomas@OrsoBruno:/etc/modprobe.d$ rfkill list
0: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

```

```

thomas@OrsoBruno:/etc/modprobe.d$ lsmod
Module                  Size  Used by
rfcomm                 40544  4 
binfmt_misc             7952  1 
sco                     9954  2 
bnep                   11857  2 
l2cap                  42208  16 rfcomm,bnep
pci_stub                1622  1 
vboxpci                15608  0 
vboxnetadp              5806  0 
vboxnetflt             16638  0 
vboxdrv              1854270  3 vboxpci,vboxnetadp,vboxnetflt
parport_pc             30086  0 
ppdev                   6644  0 
snd_hda_codec_intelhdmi    11032  1 
snd_hda_codec_realtek   300109  1 
joydev                 11171  0 
btusb                  12961  2 
bluetooth              58989  9 rfcomm,sco,bnep,l2cap,btusb
uvcvideo               62379  0 
videodev               49327  1 uvcvideo
v4l1_compat            15519  2 uvcvideo,videodev
v4l2_compat_ioctl32    11137  1 videodev
snd_hda_intel          26147  1 
snd_hda_codec         100855  3 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6482  1 snd_hda_codec
thinkpad_acpi          78535  0 
snd_seq_midi            5932  0 
snd_rawmidi            21775  1 snd_seq_midi
snd_seq_midi_event      7291  1 snd_seq_midi
i915                  334529  3 
drm_kms_helper         32900  1 i915
snd_pcm                88118  2 snd_hda_intel,snd_hda_codec
snd_seq                57032  2 snd_seq_midi,snd_seq_midi_event
drm                   205238  3 i915,drm_kms_helper
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq
jmb38x_ms               8667  0 
snd_timer              23518  2 snd_pcm,snd_seq
psmouse                62080  0 
serio_raw               4942  0 
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm
i2c_algo_bit            6208  1 i915
memstick               10185  1 jmb38x_ms
intel_agp              32334  2 i915
snd                    63780  12 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,thinkpad_acpi,snd_rawmidi,snd_pcm,snd_seq,snd_seq_device,snd_timer
soundcore               1240  1 snd
nvram                   7926  1 thinkpad_acpi
video                  22144  1 i915
output                  2527  1 video
lp                     10169  0 
parport                36936  3 parport_pc,ppdev,lp
ahci                   22370  4 
libahci                26148  1 ahci
r8169                  42286  0 
mii                     5261  1 r8169
sdhci_pci               8115  0 
sdhci                  18400  1 sdhci_pci
led_class               3393  2 thinkpad_acpi,sdhci

```

```

05:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8176 (rev 01)
	Subsystem: Realtek Semiconductor Co., Ltd. Device 8195
	Flags: bus master, fast devsel, latency 0, IRQ 10
	I/O ports at 2000 [size=256]
	Memory at f2200000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel modules: r8192ce_pci

08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
	Subsystem: Lenovo Device 2131
	Flags: bus master, fast devsel, latency 0, IRQ 46
	I/O ports at 4000 [size=256]
	Memory at f2004000 (64-bit, prefetchable) [size=4K]
	Memory at f2000000 (64-bit, prefetchable) [size=16K]
	[virtual] Expansion ROM at f2020000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169

```

```

thomas@OrsoBruno:~$ lsb_release -d
Description:	Ubuntu 10.10
thomas@OrsoBruno:~$ uname -mr
2.6.35-31-server x86_64
thomas@OrsoBruno:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

thomas@OrsoBruno:~$ sudo lshw -C network
PCI (sysfs)  

  *-network UNCLAIMED     
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: ioport:2000(size=256) memory:f2200000-f2203fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 03
       serial: e8:9a:8f:a7:3a:4b
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=10.8.44.158 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:46 ioport:4000(size=256) memory:f2004000-f2004fff memory:f2000000-f2003fff memory:f2020000-f203ffff
thomas@OrsoBruno:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr e8:9a:8f:a7:3a:4b  
          inet addr:10.8.44.158  Bcast:10.8.47.255  Mask:255.255.252.0
          inet6 addr: fe80::ea9a:8fff:fea7:3a4b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:510373 errors:0 dropped:0 overruns:0 frame:0
          TX packets:296512 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:741672507 (741.6 MB)  TX bytes:25480490 (25.4 MB)
          Interrupt:46 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:88 errors:0 dropped:0 overruns:0 frame:0
          TX packets:88 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4588 (4.5 KB)  TX bytes:4588 (4.5 KB)

thomas@OrsoBruno:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


```
currently I have 3 modules blacklisted(was proposed in another thread):
blacklist r8192e_pci
blacklist r8192se_pci
blacklist r8192ce_pci

as you can notice, the latest one is blacklisted but still loaded
(sounded weird to me)

I have some experience with Ubuntu but I'm not really a pro so I don't think I'll be able to solve this on my own :-)

---

