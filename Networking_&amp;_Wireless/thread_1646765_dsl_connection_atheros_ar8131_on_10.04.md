---
title: "dsl connection atheros ar8131 on 10.04"
date: 2010-12-16
forum: Networking &amp; Wireless
---

### Post by zissshh on 2010-12-16
PLS HELP ME SOLVE THIS PROBLEM ,THE DSL IS WORKING AND WORKS ON MY OTHER SYSTEM,BUT ETHERNET CARD ATHEROS AR8131 NOT WORKING

sudhir@sudhir-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:24:1d:59:72:fa  
          inet6 addr: fe80::224:1dff:fe59:72fa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1553 errors:0 dropped:0 overruns:0 frame:0
          TX packets:182 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:142811 (142.8 KB)  TX bytes:11136 (11.1 KB)
          Interrupt:27 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:92 errors:0 dropped:0 overruns:0 frame:0
          TX packets:92 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6960 (6.9 KB)  TX bytes:6960 (6.9 KB)

sudhir@sudhir-desktop:~$  dmesg | grep eth
[    7.210080] atheros_eth 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    7.210089] atheros_eth 0000:02:00.0: setting latency timer to 64
[    8.451671] atheros_eth 0000:02:00.0: irq 27 for MSI/MSI-X
[    8.508443] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   10.016219] atheros_eth 0000:02:00.0: ATL1C: eth0 NIC Link is Up<100 Mbps Full Duplex>
[   10.016348] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   20.380007] eth0: no IPv6 routers present

---

### Post by MooPi on 2010-12-16
Can you give us the results of terminal command ```
lsmod
```
Also ```
lspci -v
```
Sorry I just noticed that it looks like the correct module is loaded for your card. Which is atl1c and the same device I have on my computer. Instead can you print out ```
less /etc/network/interfaces
```

---

### Post by zissshh on 2010-12-16
sudhir@sudhir-desktop:~$ lsmod
Module                  Size  Used by
nls_iso8859_1           3249  1 
nls_cp437               4919  1 
vfat                    8901  1 
fat                    47767  1 vfat
pppoe                   8943  0 
pppox                   2074  1 pppoe
binfmt_misc             6587  1 
snd_hda_codec_realtek   203168  1 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_hda_intel          21877  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
atl1c                  28083  0 
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
i915                  282354  3 
drm_kms_helper         29297  1 i915
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ppdev                   5259  0 
drm                   162471  4 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
parport_pc             25962  1 
intel_agp              24177  2 i915
snd                    54148  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                63245  0 
serio_raw               3978  0 
lp                      7028  0 
atl1e                  60162  0 
agpgart                31724  2 drm,intel_agp
video                  17375  1 i915
output                  1871  1 video
parport                32635  3 ppdev,parport_pc,lp
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
usb_storage            39425  1 


sudhir@sudhir-desktop:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 10)
    Subsystem: Giga-byte Technology Device 5000
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 10)
    Subsystem: Giga-byte Technology Device d000
    Flags: bus master, fast devsel, latency 0, IRQ 26
    Memory at f0200000 (32-bit, non-prefetchable) [size=512K]
    I/O ports at e000 [size=8]
    Memory at e0000000 (32-bit, prefetchable) [size=256M]
    Memory at f0000000 (32-bit, non-prefetchable) [size=1M]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
    Subsystem: Giga-byte Technology Device a002
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at f0280000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000c000-0000cfff
    Memory behind bridge: 80000000-801fffff
    Prefetchable memory behind bridge: 0000000080200000-00000000803fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: f0100000-f01fffff
    Prefetchable memory behind bridge: 0000000080400000-00000000805fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 01)
    Subsystem: Giga-byte Technology Device 5004
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at e100 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
    Subsystem: Giga-byte Technology Device 5004
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at e200 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
    Subsystem: Giga-byte Technology Device 5004
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at e300 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
    Subsystem: Giga-byte Technology Device 5004
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at e400 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01) (prog-if 20)
    Subsystem: Giga-byte Technology Device 5006
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at f0284000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1) (prog-if 01)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=32
    I/O behind bridge: 0000b000-0000bfff
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
    Subsystem: Giga-byte Technology Device 5001
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: iTCO_wdt, intel-rng

00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
    Subsystem: Giga-byte Technology Device b002
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at f000 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
    Subsystem: Giga-byte Technology Device 5001
    Flags: medium devsel, IRQ 11
    I/O ports at 0500 [size=32]
    Kernel modules: i2c-i801

02:00.0 Ethernet controller: Atheros Communications AR8131 Gigabit Ethernet (rev c0)
    Subsystem: Giga-byte Technology Device e000
    Flags: bus master, fast devsel, latency 0, IRQ 27
    Memory at f0100000 (64-bit, non-prefetchable) [size=256K]
    I/O ports at d000 [size=128]
    Capabilities: <access denied>
    Kernel driver in use: atheros_eth
    Kernel modules: atl1c, atl1e



auto lo
iface lo inet loopback





auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

auto eth0
iface eth0 inet manual

---

### Post by dineshs on 2010-12-17
Have you tried DSL tab in NM?
[http://ubuntuforums.org/showpost.php?p=9611450&postcount=2](http://ubuntuforums.org/showpost.php?p=9611450&postcount=2)
Note : If you want to connect using ```
pon dsl-provider
```please follow step-I and II in the same link then do pon dsl-provider to connect.If you have any problem please post the output of ```
ping 4.2.2.1 -c3
```

---

### Post by zissshh on 2010-12-17
sudhir@sudhir-desktop:~$ pon dsl-provider
Error: only members of the 'dip' group can use this command.
sudhir@sudhir-desktop:~$ ping 4.2.2.1 -c3
connect: Network is unreachable

---

### Post by zissshh on 2010-12-17
i have tried editing etc network interfaces to no avail

---

### Post by dineshs on 2010-12-17
> Error: only members of the 'dip' group can use this command.try
```
sudo pon dsl-provider
```

---

### Post by zissshh on 2010-12-17
sudhir@sudhir-desktop:~$ sudo pon dsl-provider
[sudo] password for sudhir: 
Plugin rp-pppoe.so loaded.
RP-PPPoE plugin version 3.8p compiled against pppd 2.4.5
sudhir@sudhir-desktop:~$ ping 4.2.2.1 -c3
connect: Network is unreachable

---

