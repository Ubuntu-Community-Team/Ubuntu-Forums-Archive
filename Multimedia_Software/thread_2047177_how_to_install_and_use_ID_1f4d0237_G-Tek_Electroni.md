---
title: "how to install and use ID 1f4d:0237 G-Tek Electronics Group usb tv tuner"
date: 2012-08-24
forum: Multimedia Software
---

### Post by thegreateagle on 2012-08-24
hi,

I am totally new to linux hardware installation.
i cant afford windows and currently use linux and windows 8(till its free license expires)

i have the following tv tuner card : ID 1f4d:0237 G-Tek Electronics Group
thats the lsusb output. Its a usb analog tv tuner stick (works perfect in windows 8)

I have spent hours on google and duckduckgo
the maximum i am able to make out is
this page : [http://cateee.net/lkddb/web-lkddb/VIDEO_CX231XX.html](http://cateee.net/lkddb/web-lkddb/VIDEO_CX231XX.html)
has the solution or something about the solution.

I am not able to use or understand the information at all, can someone please guide me?
I need to know what steps to take from here.
is there a utility for doing this automatically.

or is it impossible to use analog tv tuner on linux?


i am really tired of searching and searching and searching.


somebody HELP!

i really dont want to buy a new copy of windows.

---

### Post by sanderj on 2012-08-24
Unplug the usb stick, wait a few seconds, and plug it in again. Then type 'dmesg' and post the last 25 lines here in this forum.

That dmesg output should make clear what the Linux kernel thinks about the device ...

---

### Post by thegreateagle on 2012-08-25
hi,
 thankyou soo much for trying to help.
the last lines from dmesg output :


[ 1076.263382] cx231xx #0: Alternate setting 0, max size= 512
[ 1076.263401] cx231xx #0: Alternate setting 1, max size= 64
[ 1076.263420] cx231xx #0: Alternate setting 2, max size= 128
[ 1076.263438] cx231xx #0: Alternate setting 3, max size= 316
[ 1076.263459] cx231xx #0: Alternate setting 4, max size= 712
[ 1076.263478] cx231xx #0: Alternate setting 5, max size= 1424
[ 1076.263983] usbcore: registered new interface driver cx231xx
[ 1076.276260] cx231xx #0: cx231xxcx231xx: called cx231xx_uninit_vbi_isoc
[ 1076.276291] cx231xx #0: cx231xx_stop_stream():: ep_mask = 10
[ 1076.334467] cx231xx #0: cx231xx_stop_stream():: ep_mask = 8
[ 1076.350117] cx231xx #0: cx231xx-audio.c: probing for cx231xx non standard usbaudio
[ 1076.351051] cx231xx #0: EndPoint Addr 0x83, Alternate settings: 3
[ 1076.351063] cx231xx #0: Alternate setting 0, max size= 512
[ 1076.351070] cx231xx #0: Alternate setting 1, max size= 28
[ 1076.351078] cx231xx #0: Alternate setting 2, max size= 52
[ 1076.351086] cx231xx: Cx231xx Audio Extension initialized
[ 1076.675854] cx231xx #0: cx231xx_start_stream():: ep_mask = 4
[ 1076.676408] cx231xx #0: cx231xx_stop_stream():: ep_mask = 4
[ 1076.678974] cx231xx #0: cx231xx_start_stream():: ep_mask = 4
[ 1076.679522] cx231xx #0: cx231xx_stop_stream():: ep_mask = 4
[ 1076.682478] cx231xx #0: cx231xx_start_stream():: ep_mask = 4
[ 1076.683125] cx231xx #0: cx231xx_stop_stream():: ep_mask = 4
[ 1076.685963] cx231xx #0: cx231xx_start_stream():: ep_mask = 4
[ 1076.687508] cx231xx #0: cx231xx_stop_stream():: ep_mask = 4
[ 1076.691217] cx231xx #0: cx231xx_start_stream():: ep_mask = 4
[ 1076.710323] cx231xx #0: cx231xx_stop_stream():: ep_mask = 4
[ 1076.718564] cx231xx #0: cx231xx_start_stream():: ep_mask = 4
[ 1076.758792] cx231xx #0: cx231xx_init_audio_isoc: Starting ISO AUDIO transfers
[ 1081.760741] cx231xx #0: cx231xx_stop_stream():: ep_mask = 4


i think its detecting something
oh and one more thing, the stick also has fm.
sorry for not mentioning that earlier.

---

### Post by sanderj on 2012-08-25
OK, that indeed looks good, but I think more from dmesg is needed. So can you post more lines? 

And: Have you already tried a TV program? If so: which one? FWIW: I use me-tv, but I don't know if that only works for DVB-T?

---

### Post by thegreateagle on 2012-08-25
dmesg output :
[   24.883342] udevd[346]: starting version 175
[   24.931121] lp: driver loaded but no devices found
[   24.961208] coretemp coretemp.0: Unable to read TjMax from CPU 0
[   24.961255] coretemp coretemp.0: Unable to read TjMax from CPU 2
[   25.112719] lib80211: common routines for IEEE802.11 drivers
[   25.112794] lib80211_crypt: registered algorithm 'NULL'
[   25.118925] wl: module license 'MIXED/Proprietary' taints kernel.
[   25.118937] Disabling lock debugging due to kernel taint
[   25.154208] [drm] Initialized drm 1.1.0 20060810
[   25.183226] wl 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   25.183246] wl 0000:02:00.0: setting latency timer to 64
[   25.199454] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   25.223435] pvrsrvkm 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   25.223454] pvrsrvkm 0000:00:02.0: setting latency timer to 64
[   25.229038] [TTM] Zone  kernel: Available graphics memory: 443152 kiB.
[   25.229049] [TTM] Zone highmem: Available graphics memory: 506812 kiB.
[   25.229056] [TTM] Initializing pool allocator.
[   25.235506] lib80211_crypt: registered algorithm 'TKIP'
[   25.316872] Linux video capture interface: v2.00
[   25.317243] eth1: Broadcom BCM4727 802.11 Hybrid Wireless Controller 5.100.82.38
[   25.321030] uvcvideo: Found UVC 1.00 device USB 2.0 UVC VGA WebCam (13d3:5711)
[   25.349042] input: USB 2.0 UVC VGA WebCam as /devices/pci0000:00/0000:00:1d.7/usb1/1-6/1-6:1.0/input/input6
[   25.349575] usbcore: registered new interface driver uvcvideo
[   25.349584] USB Video Class driver (1.1.1)
[   25.362666] cx231xx v4l2 driver loaded.
[   25.362770] cx231xx #0: New device Geniatech U237 @ 480 Mbps (1f4d:0237) with 6 interfaces
[   25.362779] cx231xx #0: registering interface 1
[   25.367523] pvrsrvkm 0000:00:02.0: irq 44 for MSI/MSI-X
[   25.367542] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   25.367549] [drm] No driver support for vblank timestamp query.
[   25.370054] cx231xx #0: Identified as Iconbit Analog Stick U100 FM (card=13)
[   25.384729] acpi device:3d: registered as cooling_device4
[   25.385625] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input7
[   25.386617] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   25.398241] IR NEC protocol handler initialized
[   25.519965] cx231xx #0: cx231xx_dif_set_standard: setStandard to ffffffff
[   25.522505] IR RC5(x) protocol handler initialized
[   25.533467] IR RC6 protocol handler initialized
[   25.558095] Overlay GTT address is 7c0000
[   25.583450] psmouse serio1: hgpk: ID: 10 00 64
[   25.599649] IR JVC protocol handler initialized
[   25.614738] cx25840 0-0044: cx23102 A/V decoder found @ 0x88 (cx231xx #0)
[   25.691259] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[   25.696467] cx25840 0-0044:  Firmware download size changed to 16 bytes max length
[   25.747781] psmouse serio1: elantech: assuming hardware version 2 (with firmware version 0x140100)
[   25.756937] IR Sony protocol handler initialized
[   25.799224] asus_wmi: ASUS WMI generic driver loaded
[   25.810965] asus_wmi: Initialization: 0x0
[   25.811104] asus_wmi: BIOS WMI version: 0.9
[   25.812852] psmouse serio1: elantech: Synaptics capabilities query result 0x68, 0x15, 0x0a.
[   25.815262] asus_wmi: SFUN value: 0x0
[   25.824638] input: Eee PC WMI hotkeys as /devices/platform/eeepc-wmi/input/input8
[   26.002904] IR MCE Keyboard/mouse protocol handler initialized
[   26.052078] asus_wmi: Backlight controlled by ACPI video driver
[   26.086496] fbcon: psbfb (fb0) is primary device
[   26.121455] psmouse serio1: elantech: retrying ps2 command 0xe6 (2).
[   26.135052] lirc_dev: IR Remote Control driver registered, major 250 
[   26.137113] IR LIRC bridge handler initialized
[   26.418643] Console: switching to colour frame buffer device 128x37
[   26.427523] fb0: psbfb frame buffer device
[   26.427529] drm: registered panic notifier
[   26.427694] Cedartrail: apply sample cache workaround
[   26.428053] Device ID: 2
[   26.428079] [drm] Initialized pvrsrvkm 8.1.0 2009-03-10 for 0000:00:02.0 on minor 0
[   26.428377] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   26.428532] snd_hda_intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[   26.428618] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[   26.482085] init: failsafe main process (642) killed by TERM signal
[   26.492477] HDMI status: Codec=1 Pin=3 Presence_Detect=0 ELD_Valid=0
[   26.492789] input: HDA Intel HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   26.493208] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   26.635071] psmouse serio1: elantech: retrying ps2 command 0xf8 (2).
[   27.087841] ppdev: user-space parallel port driver
[   27.336564] psmouse serio1: elantech: retrying ps2 command 0xf8 (1).
[   27.349758] Bluetooth: Core ver 2.16
[   27.349870] NET: Registered protocol family 31
[   27.349878] Bluetooth: HCI device and connection manager initialized
[   27.349887] Bluetooth: HCI socket layer initialized
[   27.349894] Bluetooth: L2CAP socket layer initialized
[   27.350778] Bluetooth: SCO socket layer initialized
[   27.361305] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   27.361315] Bluetooth: BNEP filters: protocol multicast
[   27.371530] Bluetooth: RFCOMM TTY layer initialized
[   27.371546] Bluetooth: RFCOMM socket layer initialized
[   27.371554] Bluetooth: RFCOMM ver 1.11
[   27.630651] atl1c 0000:03:00.0: irq 46 for MSI/MSI-X
[   27.713774] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   27.720580] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   27.965056] input: ETPS/2 Elantech Touchpad as /devices/platform/i8042/serio1/input/input11
[   28.144406] cx25840 0-0044: loaded v4l-cx231xx-avcore-01.fw firmware (16382 bytes)
[   28.179840] cx231xx #0: cx231xx #0: v4l2 driver version 0.0.2
[   28.255319] cx231xx #0: cx231xx_dif_set_standard: setStandard to ffffffff
[   28.303284] cx231xx #0: video_mux : 0
[   28.303292] cx231xx #0: do_mode_ctrl_overrides : 0x0
[   28.304124] cx231xx #0: do_mode_ctrl_overrides PAL
[   28.311527] cx231xx #0: cx231xx #0/0: registered device video1 [v4l2]
[   28.311842] cx231xx #0: cx231xx #0/0: registered device vbi0
[   28.311851] cx231xx #0: V4L2 device registered as video1 and vbi0
[   28.311862] cx231xx #0: EndPoint Addr 0x84, Alternate settings: 5
[   28.311870] cx231xx #0: Alternate setting 0, max size= 512
[   28.311878] cx231xx #0: Alternate setting 1, max size= 184
[   28.311885] cx231xx #0: Alternate setting 2, max size= 728
[   28.311892] cx231xx #0: Alternate setting 3, max size= 2892
[   28.311900] cx231xx #0: Alternate setting 4, max size= 1800
[   28.311908] cx231xx #0: EndPoint Addr 0x85, Alternate settings: 2
[   28.311916] cx231xx #0: Alternate setting 0, max size= 512
[   28.311923] cx231xx #0: Alternate setting 1, max size= 512
[   28.311937] cx231xx #0: EndPoint Addr 0x86, Alternate settings: 2
[   28.311954] cx231xx #0: Alternate setting 0, max size= 512
[   28.311968] cx231xx #0: Alternate setting 1, max size= 576
[   28.311981] cx231xx #0: EndPoint Addr 0x81, Alternate settings: 6
[   28.311994] cx231xx #0: Alternate setting 0, max size= 512
[   28.312007] cx231xx #0: Alternate setting 1, max size= 64
[   28.312019] cx231xx #0: Alternate setting 2, max size= 128
[   28.312031] cx231xx #0: Alternate setting 3, max size= 316
[   28.312043] cx231xx #0: Alternate setting 4, max size= 712
[   28.312054] cx231xx #0: Alternate setting 5, max size= 1424
[   28.312212] usbcore: registered new interface driver cx231xx
[   28.317078] cx231xx #0: cx231xxcx231xx: called cx231xx_uninit_vbi_isoc
[   28.317091] cx231xx #0: cx231xx_stop_stream():: ep_mask = 10
[   28.330604] cx231xx #0: cx231xx-audio.c: probing for cx231xx non standard usbaudio
[   28.331153] cx231xx #0: EndPoint Addr 0x83, Alternate settings: 3
[   28.331163] cx231xx #0: Alternate setting 0, max size= 512
[   28.331170] cx231xx #0: Alternate setting 1, max size= 28
[   28.331177] cx231xx #0: Alternate setting 2, max size= 52
[   28.331184] cx231xx: Cx231xx Audio Extension initialized
[   28.372801] cx231xx #0: cx231xx_stop_stream():: ep_mask = 8
[   29.082076] init: kdm main process (1060) killed by TERM signal
[   30.081546] Adding 9765884k swap on /dev/mapper/cryptswap1.  Priority:-1 extents:1 across:9765884k 
[   39.995702] eth1: no IPv6 routers present
[   65.180969] cx231xx #0: cx231xx_start_stream():: ep_mask = 4
[   65.181546] cx231xx #0: cx231xx_stop_stream():: ep_mask = 4
[   65.183963] cx231xx #0: cx231xx_start_stream():: ep_mask = 4
[   65.184473] cx231xx #0: cx231xx_stop_stream():: ep_mask = 4
[   65.186967] cx231xx #0: cx231xx_start_stream():: ep_mask = 4
[   65.187566] cx231xx #0: cx231xx_stop_stream():: ep_mask = 4
[   65.189970] cx231xx #0: cx231xx_start_stream():: ep_mask = 4
[   65.191192] cx231xx #0: cx231xx_stop_stream():: ep_mask = 4
[   65.194217] cx231xx #0: cx231xx_start_stream():: ep_mask = 4
[   65.206207] cx231xx #0: cx231xx_stop_stream():: ep_mask = 4
[   65.213219] cx231xx #0: cx231xx_start_stream():: ep_mask = 4
[   65.235775] cx231xx #0: cx231xx_init_audio_isoc: Starting ISO AUDIO transfers
[   70.592775] cx231xx #0: cx231xx_stop_stream():: ep_mask = 4
[  335.416424] eth1: no IPv6 routers present
[  591.529352] eth1: no IPv6 routers present
[ 1306.711701] usb 1-3: USB disconnect, device number 3
[ 1431.385428] usb 1-2: new high-speed USB device number 5 using ehci_hcd
[ 1431.523585] cx231xx #1: New device Geniatech U237 @ 480 Mbps (1f4d:0237) with 6 interfaces
[ 1431.523613] cx231xx #1: registering interface 1
[ 1431.523790] cx231xx #1: Identified as Iconbit Analog Stick U100 FM (card=13)
[ 1431.661562] cx231xx #1: cx231xx_dif_set_standard: setStandard to ffffffff
[ 1431.891420] cx25840 8-0044: cx23102 A/V decoder found @ 0x88 (cx231xx #1)
[ 1431.912565] cx25840 8-0044:  Firmware download size changed to 16 bytes max length
[ 1434.242534] cx25840 8-0044: loaded v4l-cx231xx-avcore-01.fw firmware (16382 bytes)
[ 1434.280967] cx231xx #1: cx231xx #1: v4l2 driver version 0.0.2
[ 1434.354050] cx231xx #1: cx231xx_dif_set_standard: setStandard to ffffffff
[ 1434.399887] cx231xx #1: video_mux : 0
[ 1434.399903] cx231xx #1: do_mode_ctrl_overrides : 0x0
[ 1434.400754] cx231xx #1: do_mode_ctrl_overrides PAL
[ 1434.407825] cx231xx #1: cx231xx #1/0: registered device video2 [v4l2]
[ 1434.408015] cx231xx #1: cx231xx #1/0: registered device vbi1
[ 1434.408026] cx231xx #1: V4L2 device registered as video2 and vbi1
[ 1434.408037] cx231xx #1: cx231xx-audio.c: probing for cx231xx non standard usbaudio
[ 1434.408807] cx231xx #1: EndPoint Addr 0x83, Alternate settings: 3
[ 1434.408818] cx231xx #1: Alternate setting 0, max size= 512
[ 1434.408827] cx231xx #1: Alternate setting 1, max size= 28
[ 1434.408836] cx231xx #1: Alternate setting 2, max size= 52
[ 1434.408847] cx231xx #1: EndPoint Addr 0x84, Alternate settings: 5
[ 1434.408857] cx231xx #1: Alternate setting 0, max size= 512
[ 1434.408865] cx231xx #1: Alternate setting 1, max size= 184
[ 1434.408993] cx231xx #1: Alternate setting 2, max size= 728
[ 1434.409002] cx231xx #1: Alternate setting 3, max size= 2892
[ 1434.409011] cx231xx #1: Alternate setting 4, max size= 1800
[ 1434.409021] cx231xx #1: EndPoint Addr 0x85, Alternate settings: 2
[ 1434.409096] cx231xx #1: Alternate setting 0, max size= 512
[ 1434.409105] cx231xx #1: Alternate setting 1, max size= 512
[ 1434.409114] cx231xx #1: EndPoint Addr 0x86, Alternate settings: 2
[ 1434.409123] cx231xx #1: Alternate setting 0, max size= 512
[ 1434.409131] cx231xx #1: Alternate setting 1, max size= 576
[ 1434.409140] cx231xx #1: EndPoint Addr 0x81, Alternate settings: 6
[ 1434.409149] cx231xx #1: Alternate setting 0, max size= 512
[ 1434.409157] cx231xx #1: Alternate setting 1, max size= 64
[ 1434.409166] cx231xx #1: Alternate setting 2, max size= 128
[ 1434.409174] cx231xx #1: Alternate setting 3, max size= 316
[ 1434.409182] cx231xx #1: Alternate setting 4, max size= 712
[ 1434.409190] cx231xx #1: Alternate setting 5, max size= 1424
[ 1434.670559] cx231xx #1: cx231xxcx231xx: called cx231xx_uninit_vbi_isoc
[ 1434.670571] cx231xx #1: cx231xx_stop_stream():: ep_mask = 10
[ 1434.671103] cx231xx #1: cx231xx_stop_stream():: ep_mask = 8
[ 1435.730285] cx231xx #1: cx231xx_start_stream():: ep_mask = 4
[ 1435.731070] cx231xx #1: cx231xx_stop_stream():: ep_mask = 4
[ 1435.734231] cx231xx #1: cx231xx_start_stream():: ep_mask = 4
[ 1435.734711] cx231xx #1: cx231xx_stop_stream():: ep_mask = 4
[ 1435.737428] cx231xx #1: cx231xx_start_stream():: ep_mask = 4
[ 1435.738099] cx231xx #1: cx231xx_stop_stream():: ep_mask = 4
[ 1435.740811] cx231xx #1: cx231xx_start_stream():: ep_mask = 4
[ 1435.742228] cx231xx #1: cx231xx_stop_stream():: ep_mask = 4
[ 1435.745449] cx231xx #1: cx231xx_start_stream():: ep_mask = 4
[ 1435.808778] cx231xx #1: cx231xx_stop_stream():: ep_mask = 4
[ 1435.865715] cx231xx #1: cx231xx_start_stream():: ep_mask = 4
[ 1435.929382] cx231xx #1: cx231xx_init_audio_isoc: Starting ISO AUDIO transfers
[ 1440.941737] cx231xx #1: cx231xx_stop_stream():: ep_mask = 4


i tried me-tv it says no dvb devices available.

can you recommend any software, i feel that it should work with vlc player, it has all sorts of options for capture devices and there is dvb option with frequency etc fields.
still not working though.

---

### Post by sanderj on 2012-08-25
As far as I can tell, your dmesg looks good.

So just find a program that can show Analog TV video. I only have experience with Digital TV (DVB-T) and me-tv

So: go to the software center, type "TV", and have a look at the different TV programs.

Yes, VLC can watch TV, but I don't know how to do the tuning with VLC.

---

