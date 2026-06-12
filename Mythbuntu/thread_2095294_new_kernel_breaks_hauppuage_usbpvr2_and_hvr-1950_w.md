---
title: "new kernel breaks hauppuage usbpvr2 and hvr-1950 with mythtv"
date: 2012-12-16
forum: Mythbuntu
---

### Post by dan5207 on 2012-12-16
I can't seem to get a 3.x linux kernel to work with the hauppauge pvrusb2 or hvr-1950. There's a lot of posts that these two capture devices work with linux and mythtv, but I can't find a combo that works. I can get tv-viewer to work, but I want a complete dvr. Do I have to go back to a 2.x kernel? Can anyone tell me the exact versions of ubuntu, mythtv, and the usbpvr2.ko that work together?

Thanks so much.

---

### Post by nickrout on 2012-12-16
What does dmesg tell you?

---

### Post by dan5207 on 2012-12-16
after
sudo chmod 0777 /dev/video0
restart backend
restart frontend

ubuntu 12.04 hvr-1950 
backend reports us-cable 2 LOCKED during channel scan.
frontend only flickers screen after clicking watch tv

ubuntu 10.10 usbpvr2
backend scans for channels correctly
frontend error: mythtv is using all inputs after clicking watch tv

HVR-1950 ubuntu 12.04 
```

[   18.088455] pvrusb2: Hardware description: WinTV HVR-1950 Model 751xx
[   18.097155] Adding 7336956k swap on /dev/sde5.  Priority:-1 extents:1 across:7336956k 
[   18.097445] usbcore: registered new interface driver pvrusb2
[   18.097449] pvrusb2: V4L in-tree version:Hauppauge WinTV-PVR-USB2 MPEG2 Encoder/Tuner
[   18.097452] pvrusb2: Debug mask is 31 (0x1f)
[   18.150951] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 22
[   18.150960] snd_hda_intel 0000:00:05.0: PCI INT B -> Link[AAZA] -> GSI 22 (level, low) -> IRQ 22
[   18.150964] hda_intel: Disabling MSI
[   18.150992] snd_hda_intel 0000:00:05.0: setting latency timer to 64
[   18.234605] usb 1-10: reset high-speed USB device number 6 using ehci_hcd
[   18.274946] cfg80211: World regulatory domain updated:
[   18.274950] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   18.274955] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.274958] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   18.274962] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   18.274965] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.274968] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.396803] EXT4-fs (sde1): re-mounted. Opts: errors=remount-ro
[   18.529407] init: failsafe main process (824) killed by TERM signal
[   18.653037] Bluetooth: Core ver 2.16
[   18.653071] NET: Registered protocol family 31
[   18.653074] Bluetooth: HCI device and connection manager initialized
[   18.653078] Bluetooth: HCI socket layer initialized
[   18.653080] Bluetooth: L2CAP socket layer initialized
[   18.653086] Bluetooth: SCO socket layer initialized
[   18.659839] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   18.659844] Bluetooth: BNEP filters: protocol multicast
[   18.665231] Bluetooth: RFCOMM TTY layer initialized
[   18.665239] Bluetooth: RFCOMM socket layer initialized
[   18.665242] Bluetooth: RFCOMM ver 1.11
[   18.701871] type=1400 audit(1355686997.188:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=920 comm="apparmor_parser"
[   18.702180] type=1400 audit(1355686997.188:7): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=921 comm="apparmor_parser"
[   18.703869] type=1400 audit(1355686997.188:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=921 comm="apparmor_parser"
[   18.704260] type=1400 audit(1355686997.192:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=921 comm="apparmor_parser"
[   18.707617] type=1400 audit(1355686997.192:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=924 comm="apparmor_parser"
[   18.708590] type=1400 audit(1355686997.196:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=929 comm="apparmor_parser"
[   18.708962] ppdev: user-space parallel port driver
[   18.721572] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   18.721579] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.721583] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   18.721587] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.721590] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   18.721593] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.721596] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   18.721599] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.721601] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   18.721605] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.721607] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   18.721611] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.721613] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   18.721616] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.721619] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   18.721625] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.721627] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   18.721631] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.721634] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   18.721637] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.721639] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   18.721643] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.721645] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   18.721648] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   18.721651] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   18.721654] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   18.721657] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   18.721660] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   18.725625] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   18.726357] Registered led device: rt73usb-phy0::radio
[   18.726383] Registered led device: rt73usb-phy0::assoc
[   18.726406] Registered led device: rt73usb-phy0::quality
[   18.727048] usbcore: registered new interface driver rt73usb
[   18.784052] hda_codec: ALC1200: BIOS auto-probing.
[   18.784057] hda_codec: ALC1200: SKU not ready 0x411111f0
[   18.860801] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   18.861204] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   18.864523] forcedeth 0000:00:07.0: irq 43 for MSI/MSI-X
[   18.901999] lirc_dev: IR Remote Control driver registered, major 249 
[   18.904824] usbcore: registered new interface driver mceusb
[   18.906365] IR NEC protocol handler initialized
[   18.910259] IR RC5(x) protocol handler initialized
[   18.912177] IR RC6 protocol handler initialized
[   18.915904] IR JVC protocol handler initialized
[   18.917825] init: alsa-restore main process (1011) terminated with status 19
[   18.931199] IR Sony protocol handler initialized
[   18.934236] IR MCE Keyboard/mouse protocol handler initialized
[   18.944834] IR LIRC bridge handler initialized
[   19.218748] pvrusb2: Device microcontroller firmware (re)loaded; it should now reset and reconnect.
[   19.250646] usb 1-4: USB disconnect, device number 4
[   19.250757] pvrusb2: Device being rendered inoperable
[   19.984123] input: HDA NVidia Line as /devices/pci0000:00/0000:00:05.0/sound/card0/input5
[   19.984243] input: HDA NVidia Front Mic as /devices/pci0000:00/0000:00:05.0/sound/card0/input6
[   19.984342] input: HDA NVidia Rear Mic as /devices/pci0000:00/0000:00:05.0/sound/card0/input7
[   19.984432] input: HDA NVidia Front Headphone as /devices/pci0000:00/0000:00:05.0/sound/card0/input8
[   19.984527] input: HDA NVidia Line-Out Side as /devices/pci0000:00/0000:00:05.0/sound/card0/input9
[   19.984615] input: HDA NVidia Line-Out CLFE as /devices/pci0000:00/0000:00:05.0/sound/card0/input10
[   19.984706] input: HDA NVidia Line-Out Surround as /devices/pci0000:00/0000:00:05.0/sound/card0/input11
[   19.984798] input: HDA NVidia Line-Out Front as /devices/pci0000:00/0000:00:05.0/sound/card0/input12
[   19.985354] ACPI: PCI Interrupt Link [APC5] enabled at IRQ 16
[   19.985375] snd_hda_intel 0000:02:00.1: PCI INT B -> Link[APC5] -> GSI 16 (level, low) -> IRQ 16
[   19.985430] snd_hda_intel 0000:02:00.1: irq 44 for MSI/MSI-X
[   19.985455] snd_hda_intel 0000:02:00.1: setting latency timer to 64
[   20.002715] HDMI status: Codec=0 Pin=3 Presence_Detect=0 ELD_Valid=0
[   20.002834] input: HD-Audio Generic HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:09.0/0000:02:00.1/sound/card1/input13
[   20.598048] vesafb: mode is 1152x864x32, linelength=4608, pages=0
[   20.598053] vesafb: scrolling: redraw
[   20.598057] vesafb: Truecolor: size=0:8:8:8, shift=0:16:8:0
[   20.601325] vesafb: framebuffer at 0xe0000000, mapped to 0xf8d80000, using 3904k, total 3904k
[   20.601457] fbcon: VESA VGA (fb0) is primary device
[   20.601605] Console: switching to colour frame buffer device 144x54
[   20.601645] fb0: VESA VGA frame buffer device
[   20.620545] init: plymouth-splash main process (1404) terminated with status 1
[   21.008038] usb 1-4: new high-speed USB device number 7 using ehci_hcd
[   21.150625] pvrusb2: Hardware description: WinTV HVR-1950 Model 751xx
[   21.182257] pvrusb2: Binding ir_rx_z8f0811_haup to i2c address 0x71.
[   21.182290] pvrusb2: Binding ir_tx_z8f0811_haup to i2c address 0x70.
[   21.186069] cx25840 2-0044: cx25843-24 found @ 0x88 (pvrusb2_a)
[   21.196071] pvrusb2: Attached sub-driver cx25840
[   21.197749] i2c-core: driver [tuner] using legacy suspend method
[   21.197754] i2c-core: driver [tuner] using legacy resume method
[   21.202317] tuner 2-0042: Tuner -1 found with type(s) Radio TV.
[   21.202326] pvrusb2: Attached sub-driver tuner
[   23.359507] cx25840 2-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[   23.455631] tveeprom 2-00a2: Hauppauge model 75111, rev E1F5, serial# 8434647
[   23.455637] tveeprom 2-00a2: MAC address is 00:0d:fe:80:b3:d7
[   23.455640] tveeprom 2-00a2: tuner model is NXP 18271C2 (idx 155, type 54)
[   23.455644] tveeprom 2-00a2: TV standards NTSC(M) ATSC/DVB Digital (eeprom 0x88)
[   23.455647] tveeprom 2-00a2: audio processor is CX25843 (idx 37)
[   23.455650] tveeprom 2-00a2: decoder processor is CX25843 (idx 30)
[   23.455653] tveeprom 2-00a2: has radio, has IR receiver, has IR transmitter
[   23.455661] pvrusb2: Supported video standard(s) reported available in hardware: PAL-M/N/Nc;NTSC-M/Mj/Mk;ATSC-8VSB/16VSB
[   23.455668] pvrusb2: Mapping standards mask=0x300b700 (PAL-M/N/Nc;NTSC-M/Mj/Mk;ATSC-8VSB/16VSB)
[   23.455671] pvrusb2: Setting up 6 unique standard(s)
[   23.455675] pvrusb2: Set up standard idx=0 name=PAL-M
[   23.455678] pvrusb2: Set up standard idx=1 name=PAL-N
[   23.455681] pvrusb2: Set up standard idx=2 name=PAL-Nc
[   23.455684] pvrusb2: Set up standard idx=3 name=NTSC-M
[   23.455686] pvrusb2: Set up standard idx=4 name=NTSC-Mj
[   23.455689] pvrusb2: Set up standard idx=5 name=NTSC-Mk
[   23.455692] pvrusb2: Initial video standard (determined by device type): NTSC-M
[   23.455703] pvrusb2: Device initialization completed successfully.
[   23.455793] pvrusb2: registered device video0 [mpeg]
[   23.455799] DVB: registering new adapter (pvrusb2-dvb)
[   25.658194] cx25840 2-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[   25.772576] tda829x 2-0042: setting tuner address to 60
[   25.798463] tda18271 2-0060: creating new instance
[   25.832563] TDA18271HD/C2 detected @ 2-0060
[   27.900507] tda18271: performing RF tracking filter calibration
[   28.928008] eth0: no IPv6 routers present
[   49.424549] tda18271: RF tracking filter calibration complete
[   49.472548] tda829x 2-0042: type set to tda8295+18271
[   54.568546] cx25840 2-0044: 0x0000 is not a valid video input!
[   54.659283] DVB: registering adapter 0 frontend 0 (Samsung S5H1411 QAM/8VSB Frontend)...
[   54.660660] tda829x 2-0042: type set to tda8295
[   54.696167] tda18271 2-0060: attaching existing instance
[  141.770061] init: mythtv-backend main process (2281) killed by TERM signal
[  150.556202] cx25840 2-0044: loaded v4l-cx25840.fw firmware (16382 bytes)

```

pvrusb2 ubuntu 10.10
```

[    4.543706] pvrusb2: Hardware description: WinTV PVR USB2 Model 24xxx
[    4.544582] usbcore: registered new interface driver pvrusb2
[    4.544584] pvrusb2: V4L in-tree version:Hauppauge WinTV-PVR-USB2 MPEG2 Encoder/Tuner
[    4.544586] pvrusb2: Debug mask is 31 (0x1f)
[    4.559401] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.559404] i915 0000:00:02.0: setting latency timer to 64
[    4.573495] mtrr: type mismatch for e0000000,10000000 old: write-back new: write-combining
[    4.573499] [drm] MTRR allocation failed.  Graphics performance may suffer.
[    4.573503] [drm] detected 63M stolen memory, trimming to 32M
[    4.573547]   alloc irq_desc for 45 on node -1
[    4.573549]   alloc kstat_irqs on node -1
[    4.573557] i915 0000:00:02.0: irq 45 for MSI/MSI-X
[    4.573565] [drm] set up 32M of stolen space
[    4.582305] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    4.605294] type=1400 audit(1355686990.413:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=784 comm="apparmor_parser"
[    4.605642] type=1400 audit(1355686990.413:7): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=785 comm="apparmor_parser"
[    4.605776] type=1400 audit(1355686990.413:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=784 comm="apparmor_parser"
[    4.606001] type=1400 audit(1355686990.413:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=784 comm="apparmor_parser"
[    4.607142] type=1400 audit(1355686990.413:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=787 comm="apparmor_parser"
[    4.716800] r8169 0000:03:00.0: eth0: link up
[    4.716807] r8169 0000:03:00.0: eth0: link up
[    4.765021] lirc_dev: IR Remote Control driver registered, major 250 
[    4.766049] lirc_i2c: module is from the staging directory, the quality is unknown, you have been warned.
[    4.898008] Console: switching to colour frame buffer device 210x65
[    4.902059] fb0: inteldrmfb frame buffer device
[    4.902060] drm: registered panic notifier
[    4.902063] Slow work thread pool: Starting up
[    4.902102] Slow work thread pool: Ready
[    4.902169] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    4.902242]   alloc irq_desc for 22 on node -1
[    4.902244]   alloc kstat_irqs on node -1
[    4.902251] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    4.902286]   alloc irq_desc for 46 on node -1
[    4.902287]   alloc kstat_irqs on node -1
[    4.902295] HDA Intel 0000:00:1b.0: irq 46 for MSI/MSI-X
[    4.902316] HDA Intel 0000:00:1b.0: setting latency timer to 64
[    4.995260] ppdev: user-space parallel port driver
[    5.554792] pvrusb2: Device microcontroller firmware (re)loaded; it should now reset and reconnect.
[    5.575382] usb 1-5: USB disconnect, address 2
[    5.575425] pvrusb2: Device being rendered inoperable
[    5.718435] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[    6.272132] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[    7.324540] usb 1-5: new high speed USB device using ehci_hcd and address 3
[    7.458168] pvrusb2: Hardware description: WinTV PVR USB2 Model 24xxx
[    7.487673] pvrusb2: Binding ir_video to i2c address 0x18.
[    7.487720] lirc_i2c: chip 0x0 found @ 0x18 (Hauppauge IR)
[    7.489156] i2c ir driver 7-0018: lirc_dev: driver lirc_i2c registered at minor = 0
[    7.513297] cx25840 7-0044: cx25843-24 found @ 0x88 (pvrusb2_a)
[    7.514038] pvrusb2: Attached sub-driver cx25840
[    7.528595] tuner 7-0061: chip found @ 0xc2 (pvrusb2_a)
[    7.528600] pvrusb2: Attached sub-driver tuner
[    7.539844] wm8775 7-001b: chip found @ 0x36 (pvrusb2_a)
[    7.543123] pvrusb2: Attached sub-driver wm8775
[    7.568148] tuner 7-0043: chip found @ 0x86 (pvrusb2_a)
[    7.570255] tda9887 7-0043: creating new instance
[    7.570258] tda9887 7-0043: tda988[5/6/7] found
[    7.570663] pvrusb2: Attached sub-driver tuner
[    8.455501] cx25840 7-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[    8.509584] tveeprom 7-00a2: Hauppauge model 24012, rev E1A3, serial# 10129719
[    8.509588] tveeprom 7-00a2: tuner model is TCL MFNM05-4 (idx 103, type 43)
[    8.509590] tveeprom 7-00a2: TV standards NTSC(M) (eeprom 0x08)
[    8.509593] tveeprom 7-00a2: audio processor is CX25843 (idx 37)
[    8.509595] tveeprom 7-00a2: decoder processor is CX25843 (idx 30)
[    8.509597] tveeprom 7-00a2: has radio, has IR receiver, has no IR transmitter
[    8.509603] pvrusb2: Supported video standard(s) reported available in hardware: PAL-M/N/Nc;NTSC-M/Mj/Mk
[    8.509607] pvrusb2: Mapping standards mask=0xb700 (PAL-M/N/Nc;NTSC-M/Mj/Mk)
[    8.509609] pvrusb2: Setting up 6 unique standard(s)
[    8.509612] pvrusb2: Set up standard idx=0 name=PAL-M
[    8.509614] pvrusb2: Set up standard idx=1 name=PAL-N
[    8.509616] pvrusb2: Set up standard idx=2 name=PAL-Nc
[    8.509618] pvrusb2: Set up standard idx=3 name=NTSC-M
[    8.509620] pvrusb2: Set up standard idx=4 name=NTSC-Mj
[    8.509622] pvrusb2: Set up standard idx=5 name=NTSC-Mk
[    8.509625] pvrusb2: Initial video standard guessed as NTSC-M
[    8.509636] pvrusb2: Device initialization completed successfully.
[    8.509706] pvrusb2: registered device video0 [mpeg]
[    8.509732] pvrusb2: registered device radio0 [mpeg]
[    8.793590] tuner-simple 7-0061: creating new instance
[    8.793593] tuner-simple 7-0061: type set to 43 (Philips NTSC MK3 (FM1236MK3 or FM1236/F))
[   15.639123] eth0: no IPv6 routers present

```

---

### Post by dan5207 on 2012-12-16
Progress!!! I can get the pvrusb2 to work with mythtv on mythbuntu 10.04.

Problems!!! I can't get the hvr1950 to work with mythtv on mythbuntu 10.04. It's stuck on analog cable channel 3. I've tried to use ivtv-tune to change the channel, but mplayer shows it stuck on channel 3. I've used both 16k and 8k fx2 firmware with no luck. When the backend scans the channels it finds every possible channel, so it's not doing a real channel scan. I want to try mythbuntu 10.10 and 11.04 but the iso images are gone from the ubuntu server. Anyone know where I can get them?

---

### Post by nickrout on 2012-12-16
> **dan5207 said:**
> Progress!!! I can get the pvrusb2 to work with mythtv on mythbuntu 10.04.

Problems!!! I can't get the hvr1950 to work with mythtv on mythbuntu 10.04. It's stuck on analog cable channel 3. I've tried to use ivtv-tune to change the channel, but mplayer shows it stuck on channel 3. I've used both 16k and 8k fx2 firmware with no luck. When the backend scans the channels it finds every possible channel, so it's not doing a real channel scan. I want to try mythbuntu 10.10 and 11.04 but the iso images are gone from the ubuntu server. Anyone know where I can get them?Does the hvr need a firmware file? Try installing the package linux-firmware-nonfree.

---

### Post by dan5207 on 2012-12-16
hvr requires firmware. after installing linux-firmware-nonfree, tv just shows noise.

---

### Post by dan5207 on 2012-12-17
someone claims they got the hvr-1950 working with fedora 14. i'll give that a try.

---

### Post by dan5207 on 2012-12-18
couldn't install mythtv on fedora 14 b/c all the mythtv repositories were empty.

i'm going to try to fix the problems w/ mythbuntu 10.04 kernel 2.6.32
firmware seems to load correctly for both 16k and 8k versions.
usb device appears correctly in backend, but during channel scan, can't find any us-cable channels.
any suggestions on what's broken?
any suggestions on what i need to update or recompile?

---

### Post by nickrout on 2012-12-18
> **dan5207 said:**
> couldn't install mythtv on fedora 14 b/c all the mythtv repositories were empty.

i'm going to try to fix the problems w/ mythbuntu 10.04 kernel 2.6.32
firmware seems to load correctly for both 16k and 8k versions.
usb device appears correctly in backend, but during channel scan, can't find any us-cable channels.
any suggestions on what's broken?
any suggestions on what i need to update or recompile?I thought analogue was dead in the USA? Perhaps that's why you don't get any channels.

Also I thought the way to get your channel info in the US was Schedules Direct?

---

### Post by dan5207 on 2012-12-18
I have cable with analog channels 2-70 and digital channels for my local channels. I'm not using a listings grabber yet.

I recompiled the pvrusb2 driver and installed it correctly, but still have the same problem.
I tried to recompile v4l-dvb, but it wouldn't install to the kernel directory, so the kernel kept using the old drivers. It kept installing to 2.6.32.60+drm33.26 instead of 2.6.32-45-generic-pae. Does anyone know how to get v4l to install correctly or how to manually install it?

---

### Post by dan5207 on 2012-12-19
Since I'm not getting much feedback here, I'm moving this discussion over to the pvrusb2 mailing list at
[http://www.isely.net/cgi-bin/mailman/listinfo/pvrusb2](http://www.isely.net/cgi-bin/mailman/listinfo/pvrusb2)

Archives at
[http://www.isely.net/pipermail/pvrusb2/](http://www.isely.net/pipermail/pvrusb2/)

---

### Post by JanCeuleers on 2012-12-20
Are you perhaps starting mythbackend too soon in the boot process? Looking at your dmesg I see that mythtv has already exited while the tuners are still initialising.

Please have a look at this page:

[http://www.mythtv.org/wiki/Upstart_mythbackend_Configuration](http://www.mythtv.org/wiki/Upstart_mythbackend_Configuration)

Specifically the section called "Delay starting the backend until all tuners have initialised" (wot I wrote).

---

