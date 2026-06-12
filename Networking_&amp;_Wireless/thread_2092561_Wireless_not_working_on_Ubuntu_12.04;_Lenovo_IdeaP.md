---
title: "Wireless not working on Ubuntu 12.04; Lenovo IdeaPad z580"
date: 2012-12-08
forum: Networking &amp; Wireless
---

### Post by lukapez on 2012-12-08
Hi folks.
I need help with my wireless on Ubuntu 12.04 (64 bit). I cant even find my wireless network on my Ubuntu, but when I am using windows 7 (another laptop) or my android, everything works fine.
Here are the things required:

Lenovo Ideapad z580

lspci
00:00.0 Host bridge: Intel Corporation Ivy Bridge DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Ivy Bridge PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Ivy Bridge Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation Panther Point USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation Panther Point MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation Panther Point High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 2 (rev c4)
00:1c.2 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 3 (rev c4)
00:1d.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Panther Point LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation Panther Point 6 port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation Panther Point SMBus Controller (rev 04)
01:00.0 VGA compatible controller: NVIDIA Corporation Device 0de3 (rev a1)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
04:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)

lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 04f2:b2e1 Chicony Electronics Co., Ltd 
Bus 003 Device 003: ID 0489:e032 Foxconn / Hon Hai 
Bus 001 Device 003: ID 0bda:0139 Realtek Semiconductor Corp. 

ifconfig 
eth0      Link encap:Ethernet  HWaddr 08:9e:01:33:10:a1  
          inet addr:192.168.1.24  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::a9e:1ff:fe33:10a1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20755 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16960 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:22890026 (22.8 MB)  TX bytes:2155155 (2.1 MB)
          Interrupt:43 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1850 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1850 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:305183 (305.1 KB)  TX bytes:305183 (305.1 KB)

wlan0     Link encap:Ethernet  HWaddr c0:14:3d:d2:65:9b  
          inet6 addr: fe80::c214:3dff:fed2:659b/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:135 (135.0 B)  TX bytes:155 (155.0 B)





iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.




lsmod

Module                  Size  Used by
wl                   2568210  0 
lib80211               14381  1 wl
rfcomm                 47604  12 
bnep                   18281  2 
parport_pc             32866  0 
ppdev                  17113  0 
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   17585  1 
fat                    61512  1 vfat
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_realtek   224173  1 
snd_hda_intel          33773  3 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
uvcvideo               72627  0 
bcma                   26696  0 
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
arc4                   12529  2 
snd_seq_midi           13324  0 
rts5139               351143  0 
videodev               98259  1 uvcvideo
btusb                  18332  2 
bluetooth             180104  23 rfcomm,bnep,btusb
snd_rawmidi            30748  1 snd_seq_midi
v4l2_compat_ioctl32    17128  1 videodev
snd_seq_midi_event     14899  1 snd_seq_midi
joydev                 17693  0 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    78855  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
brcmsmac              570874  0 
mac80211              506816  1 brcmsmac
nouveau               774641  0 
ttm                    76949  1 nouveau
brcmutil               15139  1 brcmsmac
cfg80211              205544  2 brcmsmac,mac80211
i915                  477438  3 
drm_kms_helper         46978  2 nouveau,i915
drm                   241921  6 nouveau,ttm,i915,drm_kms_helper
mei                    41616  0 
psmouse                97443  0 
soundcore              15091  1 snd
mac_hid                13253  0 
crc8                   12893  1 brcmsmac
cordic                 12535  1 brcmsmac
mxm_wmi                12979  1 nouveau
i2c_algo_bit           13423  2 nouveau,i915
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
ideapad_laptop         18234  0 
wmi                    19256  1 mxm_wmi
sparse_keymap          13890  1 ideapad_laptop
serio_raw              13211  0 
video                  19596  2 nouveau,i915
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
r8169                  62099  0 


dmesg
[   10.015906] mei 0000:00:16.0: setting latency timer to 64
[   10.015961] mei 0000:00:16.0: irq 44 for MSI/MSI-X
[   10.049269] [drm] Initialized drm 1.1.0 20060810
[   10.171606] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   10.171610] i915 0000:00:02.0: setting latency timer to 64
[   10.229820] mtrr: type mismatch for d0000000,10000000 old: write-back new: write-combining
[   10.229823] [drm] MTRR allocation failed.  Graphics performance may suffer.
[   10.230070] i915 0000:00:02.0: irq 45 for MSI/MSI-X
[   10.230074] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   10.230075] [drm] Driver supports precise vblank timestamp query.
[   10.230196] [drm:intel_dsm_platform_mux_info] *ERROR* MUX INFO call failed
[   10.230585] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   10.230587] vgaarb: transferring owner from PCI:0000:00:02.0 to PCI:0000:01:00.0
[   10.289954] cfg80211: Calling CRDA to update world regulatory domain
[   10.545914] VGA switcheroo: detected Optimus DSM method \_SB_.PCI0.PEG0.PEGP handle
[   10.545943] nouveau 0000:01:00.0: power state changed by ACPI to D0
[   10.545947] nouveau 0000:01:00.0: power state changed by ACPI to D0
[   10.545951] nouveau 0000:01:00.0: enabling device (0006 -> 0007)
[   10.545956] nouveau 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   10.545960] nouveau 0000:01:00.0: setting latency timer to 64
[   10.839578] fbcon: inteldrmfb (fb0) is primary device
[   10.862730] brcmsmac 0000:04:00.0: bus 4 slot 0 func 0 irq 255
[   10.862774] brcmsmac 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   10.862781] brcmsmac 0000:04:00.0: setting latency timer to 64
[   10.912262] psmouse serio4: synaptics: Touchpad model: 1, fw: 8.1, id: 0x1e2b1, caps: 0xd00123/0x840300/0x123c00
[   10.951912] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input6
[   11.015400] Console: switching to colour frame buffer device 170x48
[   11.017839] fb0: inteldrmfb frame buffer device
[   11.017840] drm: registered panic notifier
[   11.018289] [Firmware Bug]: ACPI(PEGP) defines _DOD but not _DOS
[   11.034958] acpi device:44: registered as cooling_device4
[   11.035167] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:42/LNXVIDEO:00/input/input7
[   11.035258] ACPI: Video Device [PEGP] (multi-head: yes  rom: yes  post: no)
[   11.039412] acpi device:51: registered as cooling_device5
[   11.039599] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input8
[   11.039641] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   11.039684] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   11.042433] [drm] nouveau 0000:01:00.0: Detected an NVc0 generation card (0x0c1180a1)
[   11.050003] vga_switcheroo: enabled
[   11.050016] [drm] nouveau 0000:01:00.0: Attempting to load BIOS image from PRAMIN
[   11.059724] [drm] nouveau 0000:01:00.0: ... BIOS signature not found
[   11.059727] [drm] nouveau 0000:01:00.0: Attempting to load BIOS image from PROM
[   11.059735] [drm] nouveau 0000:01:00.0: ... BIOS signature not found
[   11.059736] [drm] nouveau 0000:01:00.0: Attempting to load BIOS image from PCIROM
[   11.069560] nouveau 0000:01:00.0: Invalid ROM contents
[   11.069646] [drm] nouveau 0000:01:00.0: ... BIOS signature not found
[   11.069648] [drm] nouveau 0000:01:00.0: Attempting to load BIOS image from ACPI
[   11.578190] [drm] nouveau 0000:01:00.0: ... appears to be valid
[   11.578196] [drm] nouveau 0000:01:00.0: BIT BIOS found
[   11.578200] [drm] nouveau 0000:01:00.0: Bios version 70.08.a8.00
[   11.578203] [drm] nouveau 0000:01:00.0: TMDS table version 2.0
[   11.578206] [drm] nouveau 0000:01:00.0: Found Display Configuration Block version 4.0
[   11.578209] [drm] nouveau 0000:01:00.0: Raw DCB entry 0: 02001300 00000000
[   11.578212] [drm] nouveau 0000:01:00.0: Raw DCB entry 1: 0000000e 00000000
[   11.578215] [drm] nouveau 0000:01:00.0: DCB connector table: VHER 0x40 5 16 4
[   11.578218] [drm] nouveau 0000:01:00.0:   1: 0x00000100: type 0x00 idx 1 tag 0xff
[   11.578233] [drm] nouveau 0000:01:00.0: Adaptor not initialised, running VBIOS init tables.
[   11.578236] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 0 at offset 0x7954
[   11.638480] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 1 at offset 0x7FB0
[   11.665289] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 2 at offset 0x9245
[   11.665294] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 3 at offset 0x9249
[   11.665348] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 4 at offset 0x9350
[   11.665350] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table at offset 0x93B5
[   11.685194] [drm] nouveau 0000:01:00.0: voltage table 0x50 unknown
[   11.685203] [drm] nouveau 0000:01:00.0: unknown i2c port 51
[   11.685241] [drm] nouveau 0000:01:00.0: 2 available performance level(s)
[   11.685245] [drm] nouveau 0000:01:00.0: 1: core 270MHz shader 540MHz memory 405MHz timing 5
[   11.685250] [drm] nouveau 0000:01:00.0: 3: core 475MHz shader 950MHz memory 900MHz timing 6 voltage 10mV
[   11.685318] [drm] nouveau 0000:01:00.0: c: core 270MHz shader 540MHz memory 405MHz
[   11.687908] [TTM] Zone  kernel: Available graphics memory: 1954850 kiB.
[   11.687910] [TTM] Initializing pool allocator.
[   11.687919] [drm] nouveau 0000:01:00.0: Detected 1024MiB VRAM
[   11.687926] mtrr: no more MTRRs available
[   11.687934] [drm] nouveau 0000:01:00.0: 512 MiB GART (aperture)
[   11.691980] Bluetooth: Core ver 2.16
[   11.692002] NET: Registered protocol family 31
[   11.692004] Bluetooth: HCI device and connection manager initialized
[   11.692006] Bluetooth: HCI socket layer initialized
[   11.692008] Bluetooth: L2CAP socket layer initialized
[   11.692014] Bluetooth: SCO socket layer initialized
[   11.693181] [drm] nouveau 0000:01:00.0: ACPI backlight interface available, not registering our own
[   11.721512] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   11.721514] [drm] No driver support for vblank timestamp query.
[   11.721520] [drm] nouveau 0000:01:00.0: unknown i2c port 48
[   11.730011] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   11.730473] usbcore: registered new interface driver btusb
[   11.757890] Linux video capture interface: v2.00
[   11.767138] [drm] nouveau 0000:01:00.0: allocated 1024x768 fb: 0x1a0000, bo ffff880125472000
[   11.767203] fb1: nouveaufb frame buffer device
[   11.767209] [drm] Initialized nouveau 0.0.16 20090420 for 0000:01:00.0 on minor 1
[   11.819336] rts5139: module is from the staging directory, the quality is unknown, you have been warned.
[   11.819881] Initializing rts5139 USB card reader driver...
[   11.823357] scsi6 : SCSI emulation for RTS5139 USB card reader
[   11.823466] usbcore: registered new interface driver rts5139
[   11.823468] Realtek rts5139 USB card reader support registered.
[   11.823540] scsi 6:0:0:0: Direct-Access     Generic- xD/SD/M.S.       1.00 PQ: 0 ANSI: 0 CCS
[   11.824475] sd 6:0:0:0: Attached scsi generic sg2 type 0
[   11.826602] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[   11.835887] Bluetooth: can't load firmware, may not work correctly
[   12.125294] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   12.125298] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   12.125301] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   12.125304] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   12.125307] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   12.125310] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   12.125312] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   12.125315] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   12.125317] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   12.125319] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   12.125321] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   12.125323] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   12.125325] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   12.125327] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   12.125328] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   12.125330] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   12.125332] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   12.125334] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   12.125335] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   12.125337] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   12.125339] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   12.125341] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   12.125343] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   12.125345] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (600 mBi, 2000 mBm)
[   12.125346] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   12.125348] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (600 mBi, 2000 mBm)
[   12.125350] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   12.125352] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (600 mBi, 2000 mBm)
[   12.189924] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   12.190479] cfg80211: Pending regulatory request, waiting for it to be processed...
[   12.576679] uvcvideo: Found UVC 1.00 device Lenovo EasyCamera (04f2:b2e1)
[   12.577418] input: Lenovo EasyCamera as /devices/pci0000:00/0000:00:14.0/usb3/3-3/3-3:1.0/input/input9
[   12.577485] usbcore: registered new interface driver uvcvideo
[   12.577486] USB Video Class driver (1.1.1)
[   12.801209] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   12.801286] snd_hda_intel 0000:00:1b.0: irq 46 for MSI/MSI-X
[   12.801311] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[   12.909140] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   12.909143] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.909146] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   12.909148] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.909149] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   12.909151] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.909153] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   12.909155] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.909156] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   12.909158] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.909160] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   12.909162] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.909164] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   12.909166] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.909167] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   12.909169] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.909171] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   12.909173] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.909175] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   12.909178] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.909180] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   12.909183] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.909185] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   12.909189] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   12.909191] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   12.909193] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   12.909195] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   12.909197] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   12.909199] cfg80211: World regulatory domain updated:
[   12.909201] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   12.909203] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.909204] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   12.909206] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   12.909208] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.909210] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.909219] cfg80211: Calling CRDA for country: US
[   12.912069] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   12.912072] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   12.912074] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   12.912077] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   12.912078] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   12.912080] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   12.912082] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   12.912084] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   12.912085] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   12.912087] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   12.912089] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   12.912091] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   12.912093] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   12.912095] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   12.912096] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   12.912098] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   12.912100] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   12.912102] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   12.912104] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   12.912106] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   12.912107] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   12.912109] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   12.912111] cfg80211: Disabling freq 2467 MHz
[   12.912112] cfg80211: Disabling freq 2472 MHz
[   12.912113] cfg80211: Disabling freq 2484 MHz
[   12.912115] cfg80211: Regulatory domain changed to country: US
[   12.912116] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   12.912118] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   12.912120] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[   12.912122] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.912124] cfg80211:     (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.912125] cfg80211:     (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.912127] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[   13.545969] HDMI status: Codec=3 Pin=5 Presence_Detect=0 ELD_Valid=0
[   13.546044] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   13.546137] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   13.546211] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   13.633016] type=1400 audit(1355005139.757:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=614 comm="apparmor_parser"
[   13.633039] type=1400 audit(1355005139.757:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=650 comm="apparmor_parser"
[   13.633047] type=1400 audit(1355005139.757:4): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=728 comm="apparmor_parser"
[   13.633339] type=1400 audit(1355005139.757:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=614 comm="apparmor_parser"
[   13.633444] type=1400 audit(1355005139.757:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=650 comm="apparmor_parser"
[   13.633451] type=1400 audit(1355005139.757:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=728 comm="apparmor_parser"
[   13.633522] type=1400 audit(1355005139.757:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=614 comm="apparmor_parser"
[   13.633676] type=1400 audit(1355005139.757:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=650 comm="apparmor_parser"
[   13.633685] type=1400 audit(1355005139.757:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=728 comm="apparmor_parser"
[   15.944027] xhci_hcd 0000:00:14.0: WARN Event TRB for slot 1 ep 0 with no TDs queued?
[   16.089624] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro
[   16.620937] init: failsafe main process (855) killed by TERM signal
[   17.621912] type=1400 audit(1355005143.753:11): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=928 comm="apparmor_parser"
[   17.960085] ppdev: user-space parallel port driver
[   18.545233] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   18.545237] Bluetooth: BNEP filters: protocol multicast
[   18.590020] Bluetooth: RFCOMM TTY layer initialized
[   18.590026] Bluetooth: RFCOMM socket layer initialized
[   18.590028] Bluetooth: RFCOMM ver 1.11
[   23.312033] r8169 0000:03:00.0: eth0: link down
[   23.312325] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   23.312596] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   23.365889] ieee80211 phy0: brcms_ops_config: change monitor mode: false (implement)
[   23.365893] ieee80211 phy0: brcms_ops_config: change power-save mode: false (implement)
[   23.366991] ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[   23.367271] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   23.367714] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   25.380175] init: plymouth-stop pre-start process (1247) terminated with status 1
[   30.838074] [drm] nouveau 0000:01:00.0: unknown i2c port 48
[   39.888401] xhci_hcd 0000:00:14.0: WARN Event TRB for slot 1 ep 2 with no TDs queued?
[   39.888407] xhci_hcd 0000:00:14.0: WARN Event TRB for slot 1 ep 0 with no TDs queued?
[  115.665544] r8169 0000:03:00.0: eth0: link up
[  115.666095] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  126.199768] eth0: no IPv6 routers present
[  714.193467] lib80211: common routines for IEEE802.11 drivers
[  714.193470] lib80211_crypt: registered algorithm 'NULL'
[  714.195844] wl: module license 'MIXED/Proprietary' taints kernel.
[  714.195849] Disabling lock debugging due to kernel taint
[  775.865772] r8169 0000:03:00.0: eth0: link down
[  780.291467] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  893.365157] r8169 0000:03:00.0: eth0: link up
[  893.365704] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  894.873243] wlan0: authenticate with 00:24:17:42:be:96 (try 1)
[  894.875380] wlan0: authenticated
[  894.906873] wlan0: associate with 00:24:17:42:be:96 (try 1)
[  894.917991] wlan0: RX AssocResp from 00:24:17:42:be:96 (capab=0x411 status=0 aid=1)
[  894.917998] wlan0: associated
[  894.919084] ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[  894.919092] ieee80211 phy0: brcmsmac: brcms_ops_bss_info_changed: associated
[  894.919098] ieee80211 phy0: changing basic rates failed: -22
[  894.919102] ieee80211 phy0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 0 (implement)
[  894.919646] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  899.266822] ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[  899.266829] ieee80211 phy0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[  899.266834] ieee80211 phy0: brcms_ops_bss_info_changed: arp filtering: enabled false, count 0 (implement)
[  899.266838] wlan0: deauthenticating from 00:24:17:42:be:96 by local choice (reason=3)
[  899.296459] cfg80211: All devices are disconnected, going to restore regulatory settings
[  899.296465] cfg80211: Restoring regulatory settings
[  899.296473] cfg80211: Calling CRDA to update world regulatory domain
[  899.299820] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[  899.299824] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[  899.299826] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[  899.299828] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[  899.299830] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[  899.299832] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[  899.299833] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[  899.299835] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[  899.299837] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[  899.299839] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[  899.299841] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[  899.299843] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[  899.299844] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[  899.299846] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[  899.299848] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[  899.299850] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[  899.299851] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[  899.299853] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[  899.299855] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[  899.299857] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[  899.299859] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[  899.299861] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[  899.299862] cfg80211: Disabling freq 2467 MHz
[  899.299864] cfg80211: Disabling freq 2472 MHz
[  899.299865] cfg80211: Disabling freq 2484 MHz
[  899.299867] cfg80211: World regulatory domain updated:
[  899.299868] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  899.299870] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  899.299872] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  899.299874] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  899.299875] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  899.299877] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  903.514025] eth0: no IPv6 routers present
[ 2138.844135] r8169 0000:03:00.0: eth0: link down
[ 2143.244610] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 2164.465177] ideapad_laptop: Unknown event: 1
[ 2184.416447] ideapad_laptop: Unknown event: 1
[ 2195.502957] r8169 0000:03:00.0: eth0: link up
[ 2195.503509] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 2205.918195] eth0: no IPv6 routers present
[ 2222.149999] eth0: no IPv6 routers present
[ 2234.078513] wlan0: authenticate with 00:24:17:42:be:96 (try 1)
[ 2234.148636] wlan0: authenticated
[ 2234.148942] wlan0: associate with 00:24:17:42:be:96 (try 1)
[ 2234.347894] wlan0: associate with 00:24:17:42:be:96 (try 2)
[ 2234.547610] wlan0: associate with 00:24:17:42:be:96 (try 3)
[ 2234.747294] wlan0: association with 00:24:17:42:be:96 timed out
[ 2240.397141] wlan0: authenticate with 00:24:17:42:be:96 (try 1)
[ 2240.594586] wlan0: authenticate with 00:24:17:42:be:96 (try 2)
[ 2240.624408] wlan0: authenticated
[ 2240.678530] wlan0: associate with 00:24:17:42:be:96 (try 1)
[ 2240.878112] wlan0: associate with 00:24:17:42:be:96 (try 2)
[ 2241.077868] wlan0: associate with 00:24:17:42:be:96 (try 3)
[ 2241.118222] wlan0: deauthenticated from 00:24:17:42:be:96 (Reason: 6)
[ 2249.646194] r8169 0000:03:00.0: eth0: link down
[ 2253.024123] r8169 0000:03:00.0: eth0: link up
[ 2270.797553] eth0: no IPv6 routers present

sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 05
       serial: 08:9e:01:33:10:a1
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8105e-1.fw ip=192.168.1.24 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:43 ioport:2000(size=256) memory:f3804000-f3804fff memory:f3800000-f3803fff
  *-network
       description: Wireless interface
       product: BCM4313 802.11b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 01
       serial: c0:14:3d:d2:65:9b
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=brcmsmac driverversion=3.2.0-34-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:18 memory:f3900000-f3903fff


iwlist scan

lo        Interface doesn't support scanning.

wlan0     No scan results

eth0      Interface doesn't support scanning.



lsb_release -d

Description:    Ubuntu 12.04.1 LTS




 uname -mr
3.2.0-34-generic x86_64


sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                   [ OK ] 



so, this is it. sorry if it is too much, i dont know how to use grep command.
i would greatly appreciate any kind of help.
thanks a lot :)

---

### Post by mörgæs on 2012-12-08
Hi, welcome to the fora.

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by chili555 on 2012-12-08
Please run the terminal command:```
lspci -nn | grep 0280
```Is your Broadcom the famous 14e4:4727? If so, please do:```
sudo apt-get install --reinstall bcmwl-kernel-source
```Detach the ethernet, reboot and let us have your report.

If that is not your device, post it and we'll be glad to help.

---

### Post by lukapez on 2012-12-08
yes, thats exactly my device!
its working now, after running the above command, which i found in mörgæs's link. 
however, the speed is bad, but i think its due to my router.

thanks!

---

### Post by mörgæs on 2012-12-08
Good. If it solves your problem, please mark the thread so.

---

