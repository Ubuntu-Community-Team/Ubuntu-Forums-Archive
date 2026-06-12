---
title: "Wireless: works on live CD, does not work after install"
date: 2011-06-12
forum: Networking &amp; Wireless
---

### Post by bg1256 on 2011-06-12
Per the HowTo post a Wireless Issue Sticky, I have included the information in the 10 steps below.

Here is the description of my problem: 

I am getting back into Linux after purchasing a new PC (have not owned one personally for several months). I purchased an HP, as I've had personal success with them. It is an HP Pavilion g4 Notebook.

When I booted the Live CD, I was pleased that wireless just worked.

However, after installing, wireless does not work.

The Additional Drivers Tool appears to recognize my wireless card; however, when I attempt to active the driver, I receive an "installation failed" dialog. 

Here are two screenshots:

[IMG]http://dl.dropbox.com/u/3553792/Additional%20Drivers_001.png[/IMG]

[IMG]http://dl.dropbox.com/u/3553792/Untitled%20window_002.png[/IMG]

And here are the results of the file from the second screenshot:

```
2011-06-12 11:04:58,837 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-06-12 11:06:10,760 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-06-12 11:06:13,848 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-06-12 11:06:13,850 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2011-06-12 11:06:13,950 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-06-12 11:23:54,589 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-06-12 11:23:54,656 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-06-12 11:23:54,868 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-06-12 11:23:54,935 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-06-12 11:23:54,998 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
```

In the past, I have used fwcutter, but it's been some time since I've used Ubuntu, and there may be a more elegant, useful solution.

I would certainly appreciate any help anyone can provide, as obviously, having a functioning wireless card is critical for a notebook!

Thanks in advance!

1) HP Pavilion g4 Notebook

2) 

lspci:

```
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS880 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (int gfx)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 5)
00:11.0 SATA controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 42)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:16.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:16.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc M880G [Mobility Radeon HD 4200]
01:05.1 Audio device: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200]
02:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5209 (rev 01)

```

lsusb

```
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS880 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (int gfx)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 5)
00:11.0 SATA controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 42)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:16.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:16.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc M880G [Mobility Radeon HD 4200]
01:05.1 Audio device: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200]
02:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5209 (rev 01)

```

3)

ifconfig:

```
benjamin@benjamin-HP-Pavilion-g4-Notebook-PC:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 2c:27:d7:c5:0a:c5  
          inet addr:192.168.1.6  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2e27:d7ff:fec5:ac5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:42212 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25151 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:57673190 (57.6 MB)  TX bytes:2331131 (2.3 MB)
          Interrupt:43 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1200 (1.2 KB)  TX bytes:1200 (1.2 KB)

```

iwconfig:

```
lo        no wireless extensions.

eth0      no wireless extensions.

```

4) lsmod

```
Module                  Size  Used by
parport_pc             32111  0 
ppdev                  12849  0 
vesafb                 13449  1 
joydev                 17322  0 
binfmt_misc            13213  1 
snd_hda_codec_hdmi     27479  1 
snd_hda_codec_idt      60537  1 
snd_hda_intel          24140  2 
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
fglrx                2434640  52 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               66851  0 
snd                    55295  14 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videodev               75143  1 uvcvideo
hp_wmi                 13418  0 
sparse_keymap          13666  1 hp_wmi
sp5100_tco             13456  0 
psmouse                59039  0 
rts_pstor             348243  0 
soundcore              12600  1 snd
serio_raw              12990  0 
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
i2c_piix4              13095  0 
k10temp                12951  0 
shpchp                 32345  0 
video                  18951  0 
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
ahci                   21591  2 
r8169                  46630  0 
libahci                25548  1 ahci
benjamin@benjamin-HP-Pavilion-g4-Notebook-PC:~$ lsmod | grep "wlan_module_name"
benjamin@benjamin-HP-Pavilion-g4-Notebook-PC:~$ lsmod
Module                  Size  Used by
parport_pc             32111  0 
ppdev                  12849  0 
vesafb                 13449  1 
joydev                 17322  0 
binfmt_misc            13213  1 
snd_hda_codec_hdmi     27479  1 
snd_hda_codec_idt      60537  1 
snd_hda_intel          24140  2 
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
fglrx                2434640  52 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               66851  0 
snd                    55295  14 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videodev               75143  1 uvcvideo
hp_wmi                 13418  0 
sparse_keymap          13666  1 hp_wmi
sp5100_tco             13456  0 
psmouse                59039  0 
rts_pstor             348243  0 
soundcore              12600  1 snd
serio_raw              12990  0 
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
i2c_piix4              13095  0 
k10temp                12951  0 
shpchp                 32345  0 
video                  18951  0 
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
ahci                   21591  2 
r8169                  46630  0 
libahci                25548  1 ahci

```

5) dmesg

```
[    0.646753] pnp 00:09: [io  0x04d6]
[    0.646754] pnp 00:09: [io  0x0550]
[    0.646756] pnp 00:09: [io  0x0680-0x06ff]
[    0.646757] pnp 00:09: [io  0x077a]
[    0.646759] pnp 00:09: [io  0x0c00-0x0c01]
[    0.646761] pnp 00:09: [io  0x0c14]
[    0.646762] pnp 00:09: [io  0x0c50-0x0c52]
[    0.646764] pnp 00:09: [io  0x0c6c]
[    0.646765] pnp 00:09: [io  0x0c6f]
[    0.646767] pnp 00:09: [io  0x0cd0-0x0cdb]
[    0.646769] pnp 00:09: [io  0x0380-0x0387]
[    0.646820] system 00:09: [io  0x0400-0x04cf] has been reserved
[    0.646823] system 00:09: [io  0x04d0-0x04d1] has been reserved
[    0.646825] system 00:09: [io  0x04d6] has been reserved
[    0.646827] system 00:09: [io  0x0550] has been reserved
[    0.646832] system 00:09: [io  0x0680-0x06ff] has been reserved
[    0.646834] system 00:09: [io  0x077a] has been reserved
[    0.646836] system 00:09: [io  0x0c00-0x0c01] has been reserved
[    0.646838] system 00:09: [io  0x0c14] has been reserved
[    0.646840] system 00:09: [io  0x0c50-0x0c52] has been reserved
[    0.646843] system 00:09: [io  0x0c6c] has been reserved
[    0.646845] system 00:09: [io  0x0c6f] has been reserved
[    0.646847] system 00:09: [io  0x0cd0-0x0cdb] has been reserved
[    0.646849] system 00:09: [io  0x0380-0x0387] has been reserved
[    0.646852] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.646885] pnp 00:0a: [mem 0x000e0000-0x000fffff]
[    0.646887] pnp 00:0a: [mem 0xffe00000-0xffffffff]
[    0.646932] system 00:0a: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.646935] system 00:0a: [mem 0xffe00000-0xffffffff] has been reserved
[    0.646938] system 00:0a: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.844306] pnp: PnP ACPI: found 11 devices
[    0.844310] ACPI: ACPI bus type pnp unregistered
[    0.844313] PnPBIOS: Disabled by ACPI PNP
[    0.880271] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.880274] pci 0000:00:01.0:   bridge window [io  0x3000-0x3fff]
[    0.880278] pci 0000:00:01.0:   bridge window [mem 0xf0300000-0xf04fffff]
[    0.880281] pci 0000:00:01.0:   bridge window [mem 0xe0000000-0xefffffff 64bit pref]
[    0.880285] pci 0000:00:05.0: PCI bridge to [bus 02-02]
[    0.880287] pci 0000:00:05.0:   bridge window [io  disabled]
[    0.880290] pci 0000:00:05.0:   bridge window [mem 0xf0200000-0xf02fffff]
[    0.880292] pci 0000:00:05.0:   bridge window [mem pref disabled]
[    0.880295] pci 0000:00:06.0: PCI bridge to [bus 03-03]
[    0.880298] pci 0000:00:06.0:   bridge window [io  0x2000-0x2fff]
[    0.880300] pci 0000:00:06.0:   bridge window [mem disabled]
[    0.880303] pci 0000:00:06.0:   bridge window [mem 0xf0000000-0xf00fffff 64bit pref]
[    0.880307] pci 0000:00:0a.0: PCI bridge to [bus 04-04]
[    0.880308] pci 0000:00:0a.0:   bridge window [io  disabled]
[    0.880311] pci 0000:00:0a.0:   bridge window [mem 0xf0100000-0xf01fffff]
[    0.880314] pci 0000:00:0a.0:   bridge window [mem pref disabled]
[    0.880317] pci 0000:00:14.4: PCI bridge to [bus 05-05]
[    0.880319] pci 0000:00:14.4:   bridge window [io  disabled]
[    0.880327] pci 0000:00:14.4:   bridge window [mem disabled]
[    0.880330] pci 0000:00:14.4:   bridge window [mem pref disabled]
[    0.880341] pci 0000:00:01.0: setting latency timer to 64
[    0.880353] pci 0000:00:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.880356] pci 0000:00:05.0: setting latency timer to 64
[    0.880363] pci 0000:00:06.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.880366] pci 0000:00:06.0: setting latency timer to 64
[    0.880370] pci 0000:00:0a.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.880373] pci 0000:00:0a.0: setting latency timer to 64
[    0.880380] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.880382] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.880384] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.880386] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000c3fff]
[    0.880389] pci_bus 0000:00: resource 8 [mem 0x000c4000-0x000c7fff]
[    0.880391] pci_bus 0000:00: resource 9 [mem 0x000c8000-0x000cbfff]
[    0.880393] pci_bus 0000:00: resource 10 [mem 0x000d0000-0x000d3fff]
[    0.880395] pci_bus 0000:00: resource 11 [mem 0x000d4000-0x000d7fff]
[    0.880397] pci_bus 0000:00: resource 12 [mem 0x000d8000-0x000dbfff]
[    0.880399] pci_bus 0000:00: resource 13 [mem 0x000dc000-0x000dffff]
[    0.880401] pci_bus 0000:00: resource 14 [mem 0x000e0000-0x000e3fff]
[    0.880403] pci_bus 0000:00: resource 15 [mem 0x000e4000-0x000e7fff]
[    0.880405] pci_bus 0000:00: resource 16 [mem 0x000e8000-0x000ebfff]
[    0.880407] pci_bus 0000:00: resource 17 [mem 0x000ec000-0x000effff]
[    0.880409] pci_bus 0000:00: resource 18 [mem 0xe0000000-0xf6ffffff]
[    0.880411] pci_bus 0000:00: resource 19 [mem 0xf8000000-0xfed3ffff]
[    0.880413] pci_bus 0000:00: resource 20 [mem 0xfed45000-0xffffffff]
[    0.880416] pci_bus 0000:01: resource 0 [io  0x3000-0x3fff]
[    0.880418] pci_bus 0000:01: resource 1 [mem 0xf0300000-0xf04fffff]
[    0.880420] pci_bus 0000:01: resource 2 [mem 0xe0000000-0xefffffff 64bit pref]
[    0.880423] pci_bus 0000:02: resource 1 [mem 0xf0200000-0xf02fffff]
[    0.880425] pci_bus 0000:03: resource 0 [io  0x2000-0x2fff]
[    0.880427] pci_bus 0000:03: resource 2 [mem 0xf0000000-0xf00fffff 64bit pref]
[    0.880429] pci_bus 0000:04: resource 1 [mem 0xf0100000-0xf01fffff]
[    0.880432] pci_bus 0000:05: resource 4 [io  0x0000-0x0cf7]
[    0.880434] pci_bus 0000:05: resource 5 [io  0x0d00-0xffff]
[    0.880436] pci_bus 0000:05: resource 6 [mem 0x000a0000-0x000bffff]
[    0.880438] pci_bus 0000:05: resource 7 [mem 0x000c0000-0x000c3fff]
[    0.880440] pci_bus 0000:05: resource 8 [mem 0x000c4000-0x000c7fff]
[    0.880442] pci_bus 0000:05: resource 9 [mem 0x000c8000-0x000cbfff]
[    0.880444] pci_bus 0000:05: resource 10 [mem 0x000d0000-0x000d3fff]
[    0.880446] pci_bus 0000:05: resource 11 [mem 0x000d4000-0x000d7fff]
[    0.880448] pci_bus 0000:05: resource 12 [mem 0x000d8000-0x000dbfff]
[    0.880450] pci_bus 0000:05: resource 13 [mem 0x000dc000-0x000dffff]
[    0.880452] pci_bus 0000:05: resource 14 [mem 0x000e0000-0x000e3fff]
[    0.880454] pci_bus 0000:05: resource 15 [mem 0x000e4000-0x000e7fff]
[    0.880456] pci_bus 0000:05: resource 16 [mem 0x000e8000-0x000ebfff]
[    0.880458] pci_bus 0000:05: resource 17 [mem 0x000ec000-0x000effff]
[    0.880460] pci_bus 0000:05: resource 18 [mem 0xe0000000-0xf6ffffff]
[    0.880462] pci_bus 0000:05: resource 19 [mem 0xf8000000-0xfed3ffff]
[    0.880464] pci_bus 0000:05: resource 20 [mem 0xfed45000-0xffffffff]
[    0.880497] NET: Registered protocol family 2
[    0.880548] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.880728] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.881179] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.881423] TCP: Hash tables configured (established 131072 bind 65536)
[    0.881425] TCP reno registered
[    0.881429] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.881438] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.881514] NET: Registered protocol family 1
[    0.881526] pci 0000:00:01.0: MSI quirk detected; subordinate MSI disabled
[    1.072119] pci 0000:01:05.0: Boot video device
[    1.072135] PCI: CLS 64 bytes, default 64
[    1.072160] Simple Boot Flag at 0x44 set to 0x1
[    1.072404] cpufreq-nforce2: No nForce2 chipset.
[    1.072509] audit: initializing netlink socket (disabled)
[    1.072518] type=2000 audit(1307876129.072:1): initialized
[    1.081683] highmem bounce pool size: 64 pages
[    1.081689] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.083235] VFS: Disk quotas dquot_6.5.2
[    1.083301] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.083985] fuse init (API version 7.16)
[    1.084113] msgmni has been set to 1651
[    1.084437] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    1.084491] io scheduler noop registered
[    1.084495] io scheduler deadline registered
[    1.084525] io scheduler cfq registered (default)
[    1.084646] pcieport 0000:00:05.0: setting latency timer to 64
[    1.084680] pcieport 0000:00:05.0: irq 40 for MSI/MSI-X
[    1.084723] pcieport 0000:00:06.0: setting latency timer to 64
[    1.084745] pcieport 0000:00:06.0: irq 41 for MSI/MSI-X
[    1.084781] pcieport 0000:00:0a.0: setting latency timer to 64
[    1.084802] pcieport 0000:00:0a.0: irq 42 for MSI/MSI-X
[    1.084858] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.084877] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.136291] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    1.188264] ACPI: AC Adapter [ACAD] (on-line)
[    1.188353] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    1.188357] ACPI: Power Button [PWRB]
[    1.188413] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    1.188581] ACPI: Lid Switch [LID]
[    1.188614] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    1.188617] ACPI: Power Button [PWRF]
[    1.188730] ACPI: acpi_idle registered with cpuidle
[    1.188785] ACPI: processor limited to max C-state 1
[    1.388610] [Firmware Bug]: Invalid critical threshold (0)
[    1.389190] thermal LNXTHERM:00: registered as thermal_zone0
[    1.389192] ACPI: Thermal Zone [THRM] (37 C)
[    1.389214] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    1.389256] ERST: Table is not found!
[    1.389340] isapnp: Scanning for PnP cards...
[    1.443564] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.591491] ACPI: Battery Slot [BAT0] (battery present)
[    1.772804] isapnp: No Plug & Play device found
[    2.000524] Linux agpgart interface v0.103
[    2.001658] brd: module loaded
[    2.002105] loop: module loaded
[    2.002175] i2c-core: driver [adp5520] using legacy suspend method
[    2.002177] i2c-core: driver [adp5520] using legacy resume method
[    2.002528] Fixed MDIO Bus: probed
[    2.002551] PPP generic driver version 2.4.2
[    2.002578] tun: Universal TUN/TAP device driver, 1.6
[    2.002580] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    2.002648] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.002698] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    2.002709] ehci_hcd 0000:00:12.2: setting latency timer to 64
[    2.002713] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    2.002740] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    2.008139] ehci_hcd 0000:00:12.2: QUIRK: Enable exception for AMD Hudson ASPM
[    2.008145] ehci_hcd 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    2.008171] ehci_hcd 0000:00:12.2: debug port 1
[    2.008194] ehci_hcd 0000:00:12.2: irq 17, io mem 0xf0508600
[    2.020113] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    2.020256] hub 1-0:1.0: USB hub found
[    2.020260] hub 1-0:1.0: 5 ports detected
[    2.020338] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    2.020357] ehci_hcd 0000:00:13.2: setting latency timer to 64
[    2.020361] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    2.020393] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[    2.020457] ehci_hcd 0000:00:13.2: QUIRK: Enable exception for AMD Hudson ASPM
[    2.020462] ehci_hcd 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    2.020489] ehci_hcd 0000:00:13.2: debug port 1
[    2.020504] ehci_hcd 0000:00:13.2: irq 17, io mem 0xf0508500
[    2.032103] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    2.032242] hub 2-0:1.0: USB hub found
[    2.032246] hub 2-0:1.0: 5 ports detected
[    2.032327] ehci_hcd 0000:00:16.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    2.032346] ehci_hcd 0000:00:16.2: setting latency timer to 64
[    2.032349] ehci_hcd 0000:00:16.2: EHCI Host Controller
[    2.032381] ehci_hcd 0000:00:16.2: new USB bus registered, assigned bus number 3
[    2.032444] ehci_hcd 0000:00:16.2: QUIRK: Enable exception for AMD Hudson ASPM
[    2.032450] ehci_hcd 0000:00:16.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    2.032473] ehci_hcd 0000:00:16.2: debug port 1
[    2.032490] ehci_hcd 0000:00:16.2: irq 17, io mem 0xf0508400
[    2.044112] ehci_hcd 0000:00:16.2: USB 2.0 started, EHCI 1.00
[    2.044252] hub 3-0:1.0: USB hub found
[    2.044256] hub 3-0:1.0: 4 ports detected
[    2.044331] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.044352] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.044372] ohci_hcd 0000:00:12.0: setting latency timer to 64
[    2.044375] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    2.044407] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 4
[    2.048161] ohci_hcd 0000:00:12.0: irq 18, io mem 0xf0507000
[    2.072102] Refined TSC clocksource calibration: 2493.755 MHz.
[    2.072107] Switching to clocksource tsc
[    2.108223] hub 4-0:1.0: USB hub found
[    2.108234] hub 4-0:1.0: 5 ports detected
[    2.108308] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.108327] ohci_hcd 0000:00:13.0: setting latency timer to 64
[    2.108330] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    2.108364] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
[    2.108429] ohci_hcd 0000:00:13.0: irq 18, io mem 0xf0506000
[    2.168218] hub 5-0:1.0: USB hub found
[    2.168229] hub 5-0:1.0: 5 ports detected
[    2.168303] ohci_hcd 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.168323] ohci_hcd 0000:00:14.5: setting latency timer to 64
[    2.168327] ohci_hcd 0000:00:14.5: OHCI Host Controller
[    2.168362] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 6
[    2.172137] ohci_hcd 0000:00:14.5: irq 18, io mem 0xf0505000
[    2.232208] hub 6-0:1.0: USB hub found
[    2.232219] hub 6-0:1.0: 2 ports detected
[    2.232286] ohci_hcd 0000:00:16.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.232306] ohci_hcd 0000:00:16.0: setting latency timer to 64
[    2.232309] ohci_hcd 0000:00:16.0: OHCI Host Controller
[    2.232342] ohci_hcd 0000:00:16.0: new USB bus registered, assigned bus number 7
[    2.232410] ohci_hcd 0000:00:16.0: irq 18, io mem 0xf0504000
[    2.292216] hub 7-0:1.0: USB hub found
[    2.292227] hub 7-0:1.0: 4 ports detected
[    2.292298] uhci_hcd: USB Universal Host Controller Interface driver
[    2.292429] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    2.310387] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.310395] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.310516] mousedev: PS/2 mouse device common for all mice
[    2.311063] rtc_cmos 00:05: RTC can wake from S4
[    2.311186] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    2.311217] rtc0: alarms up to one month, 114 bytes nvram, hpet irqs
[    2.311304] device-mapper: uevent: version 1.0.3
[    2.311375] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: dm-devel@redhat.com
[    2.311479] device-mapper: multipath: version 1.2.0 loaded
[    2.311483] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.311585] EISA: Probing bus 0 at eisa.0
[    2.311587] EISA: Cannot allocate resource for mainboard
[    2.311589] Cannot allocate resource for EISA slot 1
[    2.311591] Cannot allocate resource for EISA slot 2
[    2.311592] Cannot allocate resource for EISA slot 3
[    2.311594] Cannot allocate resource for EISA slot 4
[    2.311595] Cannot allocate resource for EISA slot 5
[    2.311597] Cannot allocate resource for EISA slot 6
[    2.311598] Cannot allocate resource for EISA slot 7
[    2.311600] Cannot allocate resource for EISA slot 8
[    2.311601] EISA: Detected 0 cards.
[    2.311687] cpuidle: using governor ladder
[    2.311689] cpuidle: using governor menu
[    2.311915] TCP cubic registered
[    2.312033] NET: Registered protocol family 10
[    2.312514] NET: Registered protocol family 17
[    2.312527] Registering the dns_resolver key type
[    2.312554] powernow-k8: Found 1 AMD Turion(tm) II P560 Dual-Core Processor (2 cpu cores) (version 2.20.00)
[    2.312593] powernow-k8:    0 : pstate 0 (2500 MHz)
[    2.312594] powernow-k8:    1 : pstate 1 (2300 MHz)
[    2.312596] powernow-k8:    2 : pstate 2 (2000 MHz)
[    2.312597] powernow-k8:    3 : pstate 3 (1500 MHz)
[    2.312599] powernow-k8:    4 : pstate 4 (800 MHz)
[    2.312737] Using IPI No-Shortcut mode
[    2.312827] PM: Hibernation image not present or could not be loaded.
[    2.312837] registered taskstats version 1
[    2.313080]   Magic number: 15:849:931
[    2.313170] rtc_cmos 00:05: setting system clock to 2011-06-12 10:55:31 UTC (1307876131)
[    2.313173] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.313174] EDD information not available.
[    2.313293] Freeing unused kernel memory: 720k freed
[    2.313541] Write protecting the kernel text: 5352k
[    2.313594] Write protecting the kernel read-only data: 2188k
[    2.313595] NX-protecting the kernel data: 4888k
[    2.320128] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    2.332124] usb 1-3: new high speed USB device using ehci_hcd and address 2
[    2.335729] <30>udev[63]: starting version 167
[    2.508918] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.508942] r8169 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.508975] r8169 0000:03:00.0: setting latency timer to 64
[    2.508980] r8169 0000:03:00.0: (unregistered net_device): unknown MAC, using family default
[    2.509020] r8169 0000:03:00.0: irq 43 for MSI/MSI-X
[    2.509436] r8169 0000:03:00.0: eth0: RTL8101e at 0xf8436000, 2c:27:d7:c5:0a:c5, XID 00a00000 IRQ 43
[    2.523596] ahci 0000:00:11.0: version 3.0
[    2.523656] ahci 0000:00:11.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    2.523744] ahci 0000:00:11.0: AHCI 0001.0200 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
[    2.523747] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part 
[    2.524250] scsi0 : ahci
[    2.525608] scsi1 : ahci
[    2.525711] ata1: SATA max UDMA/133 irq_stat 0x00400000, PHY RDY changed irq 19
[    2.525715] ata2: SATA max UDMA/133 abar m1024@0xf0508000 port 0xf0508180 irq 19
[    3.020104] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    3.022168] ata2.00: ATAPI: hp       CDDVDW TS-L633R, 0300, max UDMA/100
[    3.026799] ata2.00: configured for UDMA/100
[    3.420113] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.421141] ata1.00: ATA-8: WDC WD3200BEVT-60A23T0, 02.01A02, max UDMA/100
[    3.421145] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    3.422257] ata1.00: configured for UDMA/100
[    3.422469] scsi 0:0:0:0: Direct-Access     ATA      WDC WD3200BEVT-6 02.0 PQ: 0 ANSI: 5
[    3.422651] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    3.422726] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    3.422767] sd 0:0:0:0: [sda] Write Protect is off
[    3.422770] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.422786] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.425275] scsi 1:0:0:0: CD-ROM            hp       CDDVDW TS-L633R  0300 PQ: 0 ANSI: 5
[    3.432990] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    3.432994] cdrom: Uniform CD-ROM driver Revision: 3.20
[    3.433124] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    3.433193] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    3.490755]  sda: sda1 sda2 sda3 < sda5 sda6 >
[    3.491081] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.804689] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[   16.017349] <30>udev[361]: starting version 167
[   16.040375] lp: driver loaded but no devices found
[   16.043426] Adding 1952764k swap on /dev/sda5.  Priority:-1 extents:1 across:1952764k 
[   16.192939] shpchp 0000:00:01.0: HPC vendor_id 1022 device_id 9602 ss_vid 1022 ss_did 9602
[   16.196174] shpchp 0000:00:01.0: Cannot reserve MMIO region
[   16.196211] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   16.265733] type=1400 audit(1307890545.449:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=591 comm="apparmor_parser"
[   16.266050] type=1400 audit(1307890545.449:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=591 comm="apparmor_parser"
[   16.266255] type=1400 audit(1307890545.449:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=591 comm="apparmor_parser"
[   16.310448] ACPI: resource piix4_smbus [io  0x0b00-0x0b07] conflicts with ACPI region SMBI [io 0xb00-0xb0f]
[   16.310452] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   16.317052] rts_pstor: module is from the staging directory, the quality is unknown, you have been warned.
[   16.319076] Initializing Realtek PCIE storage driver...
[   16.319108] rts_pstor 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   16.340496] SP5100 TCO timer: SP5100 TCO WatchDog Timer Driver v0.01
[   16.340670] SP5100 TCO timer: mmio address 0xb8fe00 already in use
[   16.360116] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   16.360121] Disabling lock debugging due to kernel taint
[   16.383196] Resource length: 0x1000
[   16.383215] Original address: 0xf0100000, remapped address: 0xf8454000
[   16.383219] pci->irq = 18
[   16.383222] rtsx_acquire_irq: chip->msi_en = 0, pci->irq = 18
[   16.383235] rts_pstor 0000:04:00.0: setting latency timer to 64
[   16.383239] scsi2 : SCSI emulation for PCI-Express Mass Storage devices
[   16.398890] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
[   16.413221] Linux video capture interface: v2.00
[   16.421493] acpi device:04: registered as cooling_device2
[   16.421731] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/LNXVIDEO:00/input/input4
[   16.421807] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   16.429641] uvcvideo: Found UVC 1.00 device HP Webcam-101 (0461:4dd8)
[   16.429882] ACPI Error: Field [D128] at 1040 exceeds Buffer [NULL] size 160 (bits) (20110112/dsopcode-597)
[   16.429888] ACPI Error: Method parse/execution failed [\_SB_.WMID.HWMC] (Node f74313a8), AE_AML_BUFFER_LIMIT (20110112/psparse-536)
[   16.429899] ACPI Error: Method parse/execution failed [\_SB_.WMID.WMAD] (Node f74314e0), AE_AML_BUFFER_LIMIT (20110112/psparse-536)
[   16.429933] ACPI Error: Field [D128] at 1040 exceeds Buffer [NULL] size 160 (bits) (20110112/dsopcode-597)
[   16.429938] ACPI Error: Method parse/execution failed [\_SB_.WMID.HWMC] (Node f74313a8), AE_AML_BUFFER_LIMIT (20110112/psparse-536)
[   16.429945] ACPI Error: Method parse/execution failed [\_SB_.WMID.WMAD] (Node f74314e0), AE_AML_BUFFER_LIMIT (20110112/psparse-536)
[   16.431963] input: HP WMI hotkeys as /devices/virtual/input/input5
[   16.432997] ACPI Error: Field [D128] at 1040 exceeds Buffer [NULL] size 160 (bits) (20110112/dsopcode-597)
[   16.433005] ACPI Error: Method parse/execution failed [\_SB_.WMID.HWMC] (Node f74313a8), AE_AML_BUFFER_LIMIT (20110112/psparse-536)
[   16.433679] ACPI Error: Method parse/execution failed [\_SB_.WMID.WMAD] (Node f74314e0), AE_AML_BUFFER_LIMIT (20110112/psparse-536)
[   16.433691] hp-wmi: probe of hp-wmi failed with error -22
[   16.447766] input: HP Webcam-101 as /devices/pci0000:00/0000:00:12.2/usb1/1-3/1-3:1.0/input/input6
[   16.447877] usbcore: registered new interface driver uvcvideo
[   16.447880] USB Video Class driver (v1.0.0)
[   16.505418] [fglrx] Maximum main memory to use for locked dma buffers: 3610 MBytes.
[   16.505489] [fglrx]   vendor: 1002 device: 9712 count: 1
[   16.505922] [fglrx] ioport: bar 1, base 0x3000, size: 0x100
[   16.505936] pci 0000:01:05.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   16.505940] pci 0000:01:05.0: setting latency timer to 64
[   16.506342] [fglrx] Kernel PAT support is enabled
[   16.506363] [fglrx] module loaded - fglrx 8.84.60 [Mar 24 2011] with 1 minors
[   16.522263] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   16.522308] HDA Intel 0000:00:14.2: setting latency timer to 64
[   16.576282] input: HDA ATI SB Mic at Ext Front Jack as /devices/pci0000:00/0000:00:14.2/sound/card0/input7
[   16.576438] input: HDA ATI SB HP Out at Ext Front Jack as /devices/pci0000:00/0000:00:14.2/sound/card0/input8
[   16.576664] HDA Intel 0000:01:05.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   16.576701] HDA Intel 0000:01:05.1: setting latency timer to 64
[   16.616242] rts_pstor: waiting for device to settle before scanning
[   16.839309] type=1400 audit(1307890546.021:5): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=799 comm="apparmor_parser"
[   16.846499] type=1400 audit(1307890546.029:6): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=801 comm="apparmor_parser"
[   16.847232] type=1400 audit(1307890546.029:7): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=800 comm="apparmor_parser"
[   16.847561] type=1400 audit(1307890546.029:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=800 comm="apparmor_parser"
[   16.847768] type=1400 audit(1307890546.029:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=800 comm="apparmor_parser"
[   16.850905] type=1400 audit(1307890546.033:10): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=801 comm="apparmor_parser"
[   16.851510] type=1400 audit(1307890546.033:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=803 comm="apparmor_parser"
[   16.864790] r8169 0000:03:00.0: eth0: link down
[   16.864798] r8169 0000:03:00.0: eth0: link down
[   16.865039] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.203508] Synaptics Touchpad, model: 1, fw: 7.5, id: 0x1e0b1, caps: 0xd00073/0x240000/0xa0400
[   17.249578] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9
[   17.616152] rts_pstor: device scan complete
[   17.616246] scsi 2:0:0:0: Direct-Access     Generic- xD/SD/M.S.       1.00 PQ: 0 ANSI: 0 CCS
[   17.616268] Bad LUN (0:1)
[   17.616308] Bad target number (1:0)
[   17.616339] Bad target number (2:0)
[   17.616368] Bad target number (3:0)
[   17.616397] Bad target number (4:0)
[   17.616424] Bad target number (5:0)
[   17.616452] Bad target number (6:0)
[   17.616482] Bad target number (7:0)
[   17.616736] sd 2:0:0:0: Attached scsi generic sg2 type 0
[   17.617231] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[   17.861359] vesafb: framebuffer at 0xe0000000, mapped to 0xf9880000, using 4160k, total 4160k
[   17.861363] vesafb: mode is 1366x768x32, linelength=5504, pages=0
[   17.861366] vesafb: scrolling: redraw
[   17.861369] vesafb: Truecolor: size=0:8:8:8, shift=0:16:8:0
[   17.861525] Console: switching to colour frame buffer device 170x48
[   17.861550] fb0: VESA VGA frame buffer device
[   18.358799] ppdev: user-space parallel port driver
[   18.658322] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=0
[   18.903999] r8169 0000:03:00.0: eth0: link up
[   18.904252] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   19.067524] [fglrx] ATIF platform detected with notification ID: 0x81
[   19.371674] [fglrx] GART Table is not in FRAME_BUFFER range 
[   19.371859] [fglrx] Could not enable MSI; System prevented initialization
[   19.372448] [fglrx] Firegl kernel thread PID: 1191
[   19.372500] [fglrx] Firegl kernel thread PID: 1192
[   19.372593] [fglrx] Firegl kernel thread PID: 1193
[   19.372896] [fglrx] IRQ 18 Enabled
[   19.593909] [fglrx] Gart USWC size:1180 M.
[   19.593913] [fglrx] Gart cacheable size:467 M.
[   19.593918] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   19.593920] [fglrx] Reserved FB block: Unshared offset:fffb000, size:5000 
[   19.602799] [fglrx:__mc_heap_map_virtual_space] *ERROR* Failed to map the virtual space
[   19.602805] [fglrx:mc_heap_map_virtual_space] *ERROR* Can not get virtual address
[   19.602808] [fglrx:MCIL_GetVirtualAddressInDescriptor] *ERROR* Can not get the virtual address
[   22.668454] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[   26.201657] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=0
[   29.472077] eth0: no IPv6 routers present
[  523.623197] exe (2630): /proc/2630/oom_adj is deprecated, please use /proc/2630/oom_score_adj instead.

```

6) sudo lshw -C network

```
*-network UNCLAIMED     
       description: Network controller
       product: BCM4313 802.11b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f0200000-f0203fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 05
       serial: 2c:27:d7:c5:0a:c5
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.6 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:43 ioport:2000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff

``` 

7) iwlist scan

```
:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

```

8) Ubuntu 11.04

9) 2.6.38-8-generic-pae i686

10) /etc/init.d/networking {start|stop}

---

### Post by josephmills on 2011-06-12
could we please see ```
lspci -nn | grep 14e4 
``` then could you go to ubuntu software center then EDIT-->Software Sources then make sure all are ticked see pic then update and upgrade ```
sudo apt-get update && sudo apt-get upgrade 
``` then reboot and post back with the code thanks

---

### Post by bg1256 on 2011-06-12
Software sources are enabled, and I am fully upgraded.

```
02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
```

---

### Post by bg1256 on 2011-06-12
I should also note that I've read everything here: [http://ubuntuforums.org/showthread.php?t=1604868](http://ubuntuforums.org/showthread.php?t=1604868)

And here: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20STA%20drivers](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20STA%20drivers)

Related to these drivers, and I've used this driver in the past. I really haven no idea what the issue is.

---

### Post by bg1256 on 2011-06-12
I have also attempted this workaround: [https://bugs.launchpad.net/ubuntu/+source/b43-fwcutter/+bug/711397/comments/6](https://bugs.launchpad.net/ubuntu/+source/b43-fwcutter/+bug/711397/comments/6)

But I can't seem to uninstall the current version of the package, and hence, I cannot install the older version.

---

### Post by josephmills on 2011-06-12
try this ```
sudo apt-get remove --purge bcmwl-kernel-source 
``` then ```
sudo sudo apt-get install broadcom-sta-common && sudo apt-get install broadcom-sta-source && sudo apt-get install firmware-b43-installer && sudo reboot 

``` after reboot anything? if not now try the launchpad link again

---

### Post by superduperlinuxperson on 2011-06-12
this is how i did it (i know it uses fwcutter but it works)
link: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)
b43-fwcutter is located on the Ubuntu install media under **../pool/main/b/b43-fwcutter/** and patch is located under **../pool/main/p/patch/** **or** both in the official repositories online.  just go online and get it.
Double click on the package to install **or** in a **terminal** (under the desktop menu **Applications > Accessories > Terminal**) navigate to the folder containing the package and issue the following command:  

:/b43-fwcutter/$ sudo dpkg -i b43-fwcutter*
**Step 2.** 
On a computer with Internet access, download the required firmware files from [http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o) and [http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2](http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2) 
**Step 3.**  
Copy  the downloaded files to your home folder and execute the following  commands consecutively in a terminal to extract and install the  firmware: 

~$ tar xfvj broadcom-wl-4.150.10.5.tar.bz2 
~$ sudo b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o 
~$ sudo b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.150.10.5/driver/wl_apsta_mimo.o
btw your card is supported!!!!

---

### Post by bg1256 on 2011-06-12
Thanks for the help.

After attempting a reboot, but before doing any of the two things listed above, it appears my Ubuntu install is bricked. What a pain.

I popped in the Live CD, and the Live CD won't even boot.

I am really hoping my Windows install is okay, so at least the computer still works. 

I'm going to go back to LTS and see if that works. What a pain.

---

### Post by josephmills on 2011-06-12
did you check the md5sum # ? [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by bg1256 on 2011-06-12
Prior to using it, yes. Now the live cd boots to Tue dame black screen as the install from grub does. I al completely lost at this point.

---

### Post by bg1256 on 2011-06-12
Can't even get into the recovery page now, lol. From grub straight to black screen! Can't do a fresh install from the live cd. Is this now completely broken because of trying to install a wireless driver? How can I get this install off my system for a fresh one?

---

### Post by josephmills on 2011-06-12
> **bg1256 said:**
> Prior to using it, yes. Now the live cd boots to Tue dame black screen as the install from grub does. I al completely lost at this point.

so you are just getting black screen nothing else after trying to boot from grub ? Bummer I wonder what could have happened? like you said in a diff post go back to 10.04 or even 10.10. I still dont see how it is just going to a black screen have you tried in the other modes that grub offers?

---

### Post by josephmills on 2011-06-12
> **bg1256 said:**
> Can't even get into the recovery page now, lol. From grub straight to black screen! Can't do a fresh install from the live cd. Is this now completely broken because of trying to install a wireless driver? How can I get this install off my system for a fresh one?

oh my when you put in the live cd and go to disk utility do you still see all partitioned areas ?  You can use gparted to get rid of the 11.04 partitioned are of the hard drive. I dont think that this happened all over a wireless driver. did you have to hardline reset it at all?

---

### Post by bg1256 on 2011-06-12
> **josephmills said:**
> so you are just getting black screen nothing else after trying to boot from grub ? Bummer I wonder what could have happened? like you said in a diff post go back to 10.04 or even 10.10. I still dont see how it is just going to a black screen have you tried in the other modes that grub offers?

Grub launches fine, bit every ubuntu option gives black screen after selection. Live cd begins to boot but then simply goes to a black screen. What a mess!

---

### Post by josephmills on 2011-06-12
> **bg1256 said:**
> Grub launches fine, bit every ubuntu option gives black screen after selection. Live cd begins to boot but then simply goes to a black screen. What a mess!

what a mess is right HOLY COW ! download 10.10 or what ever you like and try to boot with that. was there any info on there that we might have to dig for? also can you get into windoz side of things ?

---

### Post by bg1256 on 2011-06-12
> **josephmills said:**
> oh my when you put in the live cd and go to disk utility do you still see all partitioned areas ?  You can use gparted to get rid of the 11.04 partitioned are of the hard drive. I dont think that this happened all over a wireless driver. did you have to hardline reset it at all?

I cannot get to a CL or GUI. I am trying my LTS cd to see if I can install that.

---

### Post by bg1256 on 2011-06-12
My windows install is okay, thankfully, as I was dual booting. LTS in the drive now, but moving very slow. May be forced to pop in the Windows 7 disc and start over completely... Wth?

---

### Post by josephmills on 2011-06-12
> **bg1256 said:**
> My windows install is okay, thankfully, as I was dual booting. LTS in the drive now, but moving very slow. May be forced to pop in the Windows 7 disc and start over completely... Wth?

no you should be able to wipe the crappy 11,04 and  install 10.04 with no troubles. good to hear about the wondoz side of things

---

### Post by bg1256 on 2011-06-12
10.04 up and running with wireless. How bizarre.

---

### Post by josephmills on 2011-06-12
> **bg1256 said:**
> 10.04 up and running with wireless. How bizarre.

:KS:KS:KS:KS I am so glad to hear that ! :KS:KS:KS:KS

---

### Post by superduperlinuxperson on 2011-06-12
try upgrading then do what we told you earlier

---

### Post by bg1256 on 2011-06-13
I think I am going to stay with LTS. LTS is running fine, and I don't think Unity is mature enough to warrant a switch for me. WiFi just works (after installing the STA driver), and I can get all the software I need just fine.

Unlike when I first started using Ubuntu (as a student), I no longer have the time to use software and an OS that isn't ready for prime time. Don't take that the wrong way, as I love Ubuntu's release cycle. But LTS versions are likely to be the best for me moving forward, as they're supported with the most ***stable ***software -- which is what I need at this point in my life.

---

