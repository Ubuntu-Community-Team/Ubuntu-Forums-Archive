---
title: "Mic doesn't work on Thinkpad x121e"
date: 2015-02-18
forum: Multimedia Software
---

### Post by grafviktor on 2015-02-18
Hello all. My microphone isn't working. The system "sees" the microphone, but when I try to record sound with the help of arecord, the recording starts, but the indicator always shows 0, and the recorded file is empty if check it with aplay. Pavucontrol doesn't help either. Here is some details about my system
```
Advanced Linux Sound Architecture Driver Version k3.13.0-37-generic.
 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xf0340000 irq 16
 1 [Generic        ]: HDA-Intel - HD-Audio Generic
                      HD-Audio Generic at 0xf0344000 irq 45
29 [ThinkPadEC     ]: ThinkPad EC - ThinkPad Console Audio Control
                      ThinkPad Console Audio Control at EC reg 0x30, fw unknown
  1:        : sequencer
  2: [29]   : control
  3: [ 1- 3]: digital audio playback
  4: [ 1- 0]: hardware dependent
  5: [ 1]   : control
  6: [ 0- 0]: digital audio playback
  7: [ 0- 0]: digital audio capture
  8: [ 0- 0]: hardware dependent
  9: [ 0]   : control
 33:        : timer
01-00: HDA Codec 0
00-00: HDA Codec 0
00-00: CX20590 Analog : CX20590 Analog : playback 1 : capture 1
01-03: HDMI 0 : HDMI 0 : playback 1
Client info
  cur  clients : 2
  peak clients : 2
  max  clients : 192

Client   0 : "System" [Kernel]
  Port   0 : "Timer" (Rwe-)
  Port   1 : "Announce" (R-e-)
Client  14 : "Midi Through" [Kernel]
  Port   0 : "Midi Through Port-0" (RWe-)
rm: cannot remove '/etc/asound.conf': No such file or directory
rm: cannot remove '/home/roman/.pulse': No such file or directory
rm: cannot remove '/home/roman/.asound*': No such file or directory
rm: cannot remove '/home/roman/.pulse-cookie': No such file or directory
H/W path      Device     Class       Description
================================================
                         system      3053AC1 ()
/0                       bus         3053AC1
/0/0                     memory      128KiB BIOS
/0/2f                    processor   AMD E-450 APU with Radeon(tm) HD Graphics
/0/2f/30                 memory      128KiB L1 cache
/0/2f/31                 memory      1MiB L2 cache
/0/32                    memory      4GiB System Memory
/0/32/0                  memory      4GiB SODIMM DDR3 Synchronous 1333 MHz (0.8 ns)
/0/100                   bridge      Family 14h Processor Root Complex
/0/100/1                 display     Wrestler [Radeon HD 6320]
/0/100/1.1               multimedia  Wrestler HDMI Audio
/0/100/5                 bridge      Family 14h Processor Root Port
/0/100/5/0    wlan0      network     RTL8188CE 802.11b/g/n WiFi Adapter
/0/100/6                 bridge      Family 14h Processor Root Port
/0/100/6/0    eth0       network     AR8151 v2.0 Gigabit Ethernet
/0/100/7                 bridge      Family 14h Processor Root Port
/0/100/7/0               generic     RTS5209 PCI Express Card Reader
/0/100/11                storage     SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
/0/100/12                bus         SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
/0/100/12.2              bus         SB7x0/SB8x0/SB9x0 USB EHCI Controller
/0/100/13                bus         SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
/0/100/13.2              bus         SB7x0/SB8x0/SB9x0 USB EHCI Controller
/0/100/14                bus         SBx00 SMBus Controller
/0/100/14.2              multimedia  SBx00 Azalia (Intel HDA)
/0/100/14.3              bridge      SB7x0/SB8x0/SB9x0 LPC host controller
/0/100/14.4              bridge      SBx00 PCI to PCI Bridge
/0/101                   bridge      Family 12h/14h Processor Function 0
/0/102                   bridge      Family 12h/14h Processor Function 1
/0/103                   bridge      Family 12h/14h Processor Function 2
/0/104                   bridge      Family 12h/14h Processor Function 3
/0/105                   bridge      Family 12h/14h Processor Function 4
/0/106                   bridge      Family 12h/14h Processor Function 6
/0/107                   bridge      Family 12h/14h Processor Function 5
/0/108                   bridge      Family 12h/14h Processor Function 7
/0/1          scsi0      storage    
/0/1/0.0.0    /dev/sda   disk        320GB ST320LT007-9ZV14
/0/1/0.0.0/1  /dev/sda1  volume      499MiB Windows NTFS volume
/0/1/0.0.0/2  /dev/sda2  volume      43GiB Windows NTFS volume
/0/1/0.0.0/3  /dev/sda3  volume      249GiB EXT4 volume
/0/1/0.0.0/4  /dev/sda4  volume      4GiB Linux swap volume
total 0
crw-rw----+  1 root audio 116, 33 Feb 18 15:02 timer
crw-rw----+  1 root audio 116,  4 Feb 18 15:02 hwC1D0
crw-rw----+  1 root audio 116,  2 Feb 18 15:02 controlC29
crw-rw----+  1 root audio 116,  5 Feb 18 15:02 controlC1
drwxr-xr-x   3 root root      260 Feb 18 15:02 .
crw-rw----+  1 root audio 116,  8 Feb 18 15:02 hwC0D0
crw-rw----+  1 root audio 116,  9 Feb 18 15:02 controlC0
drwxr-xr-x   2 root root      100 Feb 18 15:02 by-path
crw-rw----+  1 root audio 116,  3 Feb 18 15:08 pcmC1D3p
crw-rw----+  1 root audio 116,  6 Feb 18 15:08 pcmC0D0p
crw-rw----+  1 root audio 116,  7 Feb 18 15:08 pcmC0D0c
crw-rw----+  1 root audio 116,  1 Feb 18 15:15 seq
drwxr-xr-x  16 root root     4160 Feb 18 15:16 ..
cat: /dev/sndstat: No such file or directory
00:00.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 14h Processor Root Complex [1022:1510]
00:01.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Wrestler [Radeon HD 6320] [1002:9806]
00:01.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] Wrestler HDMI Audio [1002:1314]
00:05.0 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] Family 14h Processor Root Port [1022:1513]
00:06.0 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] Family 14h Processor Root Port [1022:1514]
00:07.0 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] Family 14h Processor Root Port [1022:1515]
00:11.0 SATA controller [0106]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] [1002:4391]
00:12.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
00:12.2 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
00:13.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
00:13.2 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
00:14.0 SMBus [0c05]: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller [1002:4385] (rev 42)
00:14.2 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA) [1002:4383] (rev 40)
00:14.3 ISA bridge [0601]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 LPC host controller [1002:439d] (rev 40)
00:14.4 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 PCI to PCI Bridge [1002:4384] (rev 40)
00:18.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 0 [1022:1700] (rev 43)
00:18.1 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 1 [1022:1701]
00:18.2 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 2 [1022:1702]
00:18.3 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 3 [1022:1703]
00:18.4 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 4 [1022:1704]
00:18.5 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 6 [1022:1718]
00:18.6 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 5 [1022:1716]
00:18.7 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 7 [1022:1719]
01:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
02:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8151 v2.0 Gigabit Ethernet [1969:1083] (rev c0)
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5209 PCI Express Card Reader [10ec:5209] (rev 01)
Bus 002 Device 002: ID 5986:01a6 Acer, Inc Lenovo Integrated Webcam
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 003: ID 045e:0083 Microsoft Corp. Basic Optical Mouse
Bus 003 Device 002: ID 0518:0001 EzKEY Corp. USB to PS2 Adaptor v1.09
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
/usr/sbin/alsactl
Specified filename /dev/dsp does not exist.
                     USER        PID ACCESS COMMAND
/dev/snd/controlC0:  roman      1725 F.... pulseaudio
/dev/snd/controlC1:  roman      1725 F.... pulseaudio
dpkg-query: no path found matching pattern *bin/slmodemd*
[    0.000000] No AGP bridge found
[    0.000000] No NUMA configuration found
[    0.000000] No AGP bridge found
[    0.564116] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.575261] ACPI: No dock devices found.
[    0.576138] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.576165] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.587437] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.587498] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.594332] acpi PNP0A08:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-1f] only partially covers this bridge
[    0.628329] Found 1 acpi root devices
[    0.647411] pnp: PnP ACPI: found 9 devices
[    1.710536] audit: initializing netlink socket (disabled)
[    1.710557] type=2000 audit(1424271750.276:1): initialized
[    1.905396] libphy: Fixed MDIO Bus: probed
[    1.906361] ehci-pci 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.918681] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.919105] hub 1-0:1.0: USB hub found
[    1.919831] ehci-pci 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.930680] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    1.931185] hub 2-0:1.0: USB hub found
[    1.990732] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    1.991284] hub 3-0:1.0: USB hub found
[    2.050726] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    2.051247] hub 4-0:1.0: USB hub found
[    2.077679] IMA: No TPM chip found, activating TPM-bypass!
[    2.078902] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.253158] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    2.508897] [drm] Enabling audio 0 support
[    2.615820] [drm] Found smc ucode version: 0x00010601
[    2.754861] usb 2-5: New USB device found, idVendor=5986, idProduct=01a6
[    3.063916] usb 3-2: New USB device found, idVendor=0518, idProduct=0001
[    3.374212] usb 3-3: New USB device found, idVendor=045e, idProduct=0083
[    7.917668] psmouse serio5: trackpoint: IBM TrackPoint firmware: 0x0e, buttons: 3/3
[    9.621932] lp: driver loaded but no devices found
[   11.850978] thinkpad_acpi: radio switch found; radios are enabled
[   11.850993] thinkpad_acpi: possible tablet mode switch found; ThinkPad in laptop mode
[   11.856874] thinkpad_acpi: Console audio control enabled, mode: monitor (read only)
[   11.967434] snd_hda_intel 0000:00:01.1: irq 45 for MSI/MSI-X
[   11.995203] input: HD-Audio Generic HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.1/sound/card1/input19
[   12.123588] input: HDA ATI SB Headphone as /devices/pci0000:00/0000:00:14.2/sound/card0/input21
[   12.127794] input: HDA ATI SB Mic as /devices/pci0000:00/0000:00:14.2/sound/card0/input20
[   12.205810] rtl8192ce: Using firmware rtlwifi/rtl8192cfw.bin
[   13.426878] uvcvideo: Found UVC 1.00 device Integrated Camera (5986:01a6)
sudo: /etc/init.d/sl-modem-daemon: command not found
/etc/modprobe.d/alsa-base.conf:# options snd-hda-intel model=lenovo index=0 position_fix=1 enable=yes
    Release Date: 10/24/2012
        Serial services are supported (int 14h)
    Manufacturer: LENOVO
    Product Name: 3053AC1
    Serial Number: LRZ78GB
    Manufacturer: LENOVO
    Product Name: 3053AC1
    Serial Number: 1ZKA528G1MV
    Manufacturer: LENOVO
    Serial Number: LRZ78GB
    Manufacturer: AMD
    Serial Number: Not Specified
    Manufacturer: 0198
    Serial Number: 121C040D
snd_seq_dummy          12798  0
snd_seq_midi           13324  0
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  1 snd_seq_midi
snd_seq                61560  3 snd_seq_midi_event,snd_seq_dummy,snd_seq_midi
snd_seq_device         14497  4 snd_seq,snd_rawmidi,snd_seq_dummy,snd_seq_midi
snd_hda_codec_conexant    57441  1
snd_hda_codec_hdmi     46368  1
snd_hda_intel          56451  5
snd_hda_codec         192906  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_timer              29482  2 snd_pcm,snd_seq
snd                    69322  23 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,thinkpad_acpi,snd_seq_device,snd_seq_dummy,snd_seq_midi
soundcore              12680  1 snd
usbhid                 52659  0
hid                   106148  2 hid_generic,usbhid
Welcome to PulseAudio! Use "help" for usage information.
>>> 2 sink(s) available.
    index: 0
    name: <alsa_output.pci-0000_00_01.1.hdmi-stereo>
    driver: <module-alsa-card.c>
    flags: HARDWARE DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
    state: SUSPENDED
    suspend cause: IDLE
    priority: 9950
    volume: 0: 100% 1: 100%
            0: 0,00 dB 1: 0,00 dB
            balance 0,00
    base volume: 100%
                 0,00 dB
    volume steps: 65537
    muted: no
    current latency: 0,00 ms
    max request: 0 KiB
    max rewind: 0 KiB
    monitor source: 0
    sample spec: s16le 2ch 96000&#1043;&#1094;
    channel map: front-left,front-right
                 &#1057;&#1090;&#1077;&#1088;&#1077;&#1086;
    used by: 0
    linked by: 0
    configured latency: 0,00 ms; range is 0,50 .. 170,67 ms
    card: 0 <alsa_card.pci-0000_00_01.1>
    module: 4
    properties:
        alsa.resolution_bits = "16"
        device.api = "alsa"
        device.class = "sound"
        alsa.class = "generic"
        alsa.subclass = "generic-mix"
        alsa.name = "HDMI 0"
        alsa.id = "HDMI 0"
        alsa.subdevice = "0"
        alsa.subdevice_name = "subdevice #0"
        alsa.device = "3"
        alsa.card = "1"
        alsa.card_name = "HD-Audio Generic"
        alsa.long_card_name = "HD-Audio Generic at 0xf0344000 irq 45"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:00:01.1"
        sysfs.path = "/devices/pci0000:00/0000:00:01.1/sound/card1"
        device.bus = "pci"
        device.vendor.id = "1002"
        device.vendor.name = "Advanced Micro Devices, Inc. [AMD/ATI]"
        device.product.id = "1314"
        device.product.name = "Wrestler HDMI Audio [Radeon HD 6250/6310]"
        device.form_factor = "internal"
        device.string = "hdmi:1"
        device.buffering.buffer_size = "65536"
        device.buffering.fragment_size = "32768"
        device.access_mode = "mmap+timer"
        device.profile.name = "hdmi-stereo"
        device.profile.description = "&#1062;&#1080;&#1092;&#1088;&#1086;&#1074;&#1086;&#1077; &#1089;&#1090;&#1077;&#1088;&#1077;&#1086; (HDMI)"
        device.description = "&#1042;&#1089;&#1090;&#1088;&#1086;&#1077;&#1085;&#1085;&#1086;&#1077; &#1072;&#1091;&#1076;&#1080;&#1086; &#1062;&#1080;&#1092;&#1088;&#1086;&#1074;&#1086;&#1077; &#1089;&#1090;&#1077;&#1088;&#1077;&#1086; (HDMI)"
        alsa.mixer_name = "ATI R6xx HDMI"
        alsa.components = "HDA:1002aa01,00aa0100,00100200"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    ports:
        hdmi-output-0: HDMI / DisplayPort (priority 5900, latency offset 0 usec, available: yes)
            properties:
                device.icon_name = "video-display"
    active port: <hdmi-output-0>
  * index: 1
    name: <alsa_output.pci-0000_00_14.2.analog-stereo>
    driver: <module-alsa-card.c>
    flags: HARDWARE HW_MUTE_CTRL HW_VOLUME_CTRL DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
    state: SUSPENDED
    suspend cause: IDLE
    priority: 9959
    volume: 0: 100% 1: 100%
            0: 0,12 dB 1: 0,12 dB
            balance 0,00
    base volume: 100%
                 0,00 dB
    volume steps: 65537
    muted: no
    current latency: 0,00 ms
    max request: 0 KiB
    max rewind: 0 KiB
    monitor source: 1
    sample spec: s16le 2ch 96000&#1043;&#1094;
    channel map: front-left,front-right
                 &#1057;&#1090;&#1077;&#1088;&#1077;&#1086;
    used by: 0
    linked by: 0
    configured latency: 0,00 ms; range is 0,50 .. 170,67 ms
    card: 1 <alsa_card.pci-0000_00_14.2>
    module: 5
    properties:
        alsa.resolution_bits = "16"
        device.api = "alsa"
        device.class = "sound"
        alsa.class = "generic"
        alsa.subclass = "generic-mix"
        alsa.name = "CX20590 Analog"
        alsa.id = "CX20590 Analog"
        alsa.subdevice = "0"
        alsa.subdevice_name = "subdevice #0"
        alsa.device = "0"
        alsa.card = "0"
        alsa.card_name = "HDA ATI SB"
        alsa.long_card_name = "HDA ATI SB at 0xf0340000 irq 16"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:00:14.2"
        sysfs.path = "/devices/pci0000:00/0000:00:14.2/sound/card0"
        device.bus = "pci"
        device.vendor.id = "1002"
        device.vendor.name = "Advanced Micro Devices, Inc. [AMD/ATI]"
        device.product.id = "4383"
        device.product.name = "SBx00 Azalia (Intel HDA)"
        device.form_factor = "internal"
        device.string = "front:0"
        device.buffering.buffer_size = "65536"
        device.buffering.fragment_size = "32768"
        device.access_mode = "mmap+timer"
        device.profile.name = "analog-stereo"
        device.profile.description = "&#1040;&#1085;&#1072;&#1083;&#1086;&#1075;&#1086;&#1074;&#1086;&#1077; &#1089;&#1090;&#1077;&#1088;&#1077;&#1086;"
        device.description = "&#1042;&#1089;&#1090;&#1088;&#1086;&#1077;&#1085;&#1085;&#1086;&#1077; &#1072;&#1091;&#1076;&#1080;&#1086; &#1040;&#1085;&#1072;&#1083;&#1086;&#1075;&#1086;&#1074;&#1086;&#1077; &#1089;&#1090;&#1077;&#1088;&#1077;&#1086;"
        alsa.mixer_name = "Conexant CX20590"
        alsa.components = "HDA:14f1506e,17aa21ec,00100003"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    ports:
        analog-output-speaker: &#1043;&#1088;&#1086;&#1084;&#1082;&#1086;&#1075;&#1086;&#1074;&#1086;&#1088;&#1080;&#1090;&#1077;&#1083;&#1080; (priority 10000, latency offset 0 usec, available: unknown)
            properties:
                device.icon_name = "audio-speakers"
        analog-output-headphones: &#1040;&#1085;&#1072;&#1083;&#1086;&#1075;&#1086;&#1074;&#1099;&#1077; &#1085;&#1072;&#1091;&#1096;&#1085;&#1080;&#1082;&#1080; (priority 9000, latency offset 0 usec, available: no)
            properties:
                device.icon_name = "audio-headphones"
    active port: <analog-output-speaker>
>>> **** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: CX20590 Analog [CX20590 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
Unloading ALSA sound driver modules: snd-seq-dummy snd-seq-midi snd-seq-midi-event snd-rawmidi snd-seq snd-seq-device snd-hda-codec-conexant snd-hda-codec-hdmi snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-page-alloc snd-timer (failed: modules still loaded: snd-hda-codec-conexant snd-hda-codec-hdmi snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-page-alloc snd-timer).
Loading ALSA sound driver modules: snd-seq-dummy snd-seq-midi snd-seq-midi-event snd-rawmidi snd-seq snd-seq-device snd-hda-codec-conexant snd-hda-codec-hdmi snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-page-alloc snd-timer.
Traceback (most recent call last):
  File "/usr/bin/ubuntu-support-status", line 133, in <module>
    pkg.name, support_tag)
  File "/usr/bin/ubuntu-support-status", line 49, in get_maintenance_status
    raise Exception("No date tag found")
Exception: No date tag found
  *-multimedia:0          
       description: Audio device
       product: Wrestler HDMI Audio
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 1.1
       bus info: pci@0000:00:01.1
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list
       configuration: driver=snd_hda_intel latency=0
       resources: irq:45 memory:f0344000-f0347fff
  *-multimedia:1
       description: Audio device
       product: SBx00 Azalia (Intel HDA)
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 14.2
       bus info: pci@0000:00:14.2
       version: 40
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=snd_hda_intel latency=64
       resources: irq:16 memory:f0340000-f0343fff
```

And here is the output of alsa-info.sh script [http://www.alsa-project.org/db/?f=fa7291bff45964702734c04d86b007349b21a298](http://www.alsa-project.org/db/?f=fa7291bff45964702734c04d86b007349b21a298)

Please help me to resolve the issue, I spent 2 days with google playing around with different settings, but still at the same point. Thank you.

---

### Post by tgalati4 on 2015-02-18
Your microphone could be broken.  

Open a terminal:

```
alsamixer
```

Hit F4 to bring up the "Capture" dialog.  Describe what you see.

Use the arrows and spacebar to move and select settings.  Make sure mic boost is on, capture is on, and mic level is up to 70% or so.

---

### Post by grafviktor on 2015-02-19
tgalati4, thanks for your reply,  here is what I see when launch alsamixer. 

```
&#9474; Card: HDA ATI SB                                     F1:  Help               &#9474;
&#9474; Chip: Conexant CX20590                               F2:  System information &#9474;
&#9474; View: F3: Playback  F4:[Capture] F5: All             F6:  Select sound card  &#9474;
&#9474; Item: Mic Boost [dB gain: 40.00, 40.00]              Esc: Exit               &#9474;
&#9474;                                                                              &#9474;
&#9474;                  &#9484;&#9472;&#9472;&#9488;               &#9484;&#9472;&#9472;&#9488;               &#9484;&#9472;&#9472;&#9488;                  &#9474;
&#9474;                  &#9474;&#9618;&#9618;&#9474;               &#9474;&#9618;&#9618;&#9474;               &#9474;&#9618;&#9618;&#9474;                  &#9474;
&#9474;                  &#9474;&#9618;&#9618;&#9474;               &#9474;&#9618;&#9618;&#9474;               &#9474;&#9618;&#9618;&#9474;                  &#9474;
&#9474;                  &#9474;&#9618;&#9618;&#9474;               &#9474;&#9618;&#9618;&#9474;               &#9474;&#9618;&#9618;&#9474;                  &#9474;
&#9474;                  &#9474;&#9618;&#9618;&#9474;               &#9474;&#9618;&#9618;&#9474;               &#9474;&#9618;&#9618;&#9474;                  &#9474;
&#9474;                  &#9474;&#9618;&#9618;&#9474;               &#9474;&#9618;&#9618;&#9474;               &#9474;&#9618;&#9618;&#9474;                  &#9474;
&#9474;                  &#9474;&#9618;&#9618;&#9474;               &#9474;&#9618;&#9618;&#9474;               &#9474;&#9618;&#9618;&#9474;                  &#9474;
&#9474;                  &#9474;&#9618;&#9618;&#9474;               &#9474;&#9618;&#9618;&#9474;               &#9474;&#9618;&#9618;&#9474;                  &#9474;
&#9474;                  &#9474;&#9618;&#9618;&#9474;               &#9474;&#9618;&#9618;&#9474;               &#9474;&#9618;&#9618;&#9474;                  &#9474;
&#9474;                  &#9474;&#9618;&#9618;&#9474;               &#9474;&#9618;&#9618;&#9474;               &#9474;&#9618;&#9618;&#9474;                  &#9474;
&#9474;                  &#9474;&#9618;&#9618;&#9474;               &#9474;&#9618;&#9618;&#9474;               &#9474;&#9618;&#9618;&#9474;                  &#9474;
&#9474;                  &#9474;&#9618;&#9618;&#9474;               &#9474;&#9618;&#9618;&#9474;               &#9474;&#9618;&#9618;&#9474;                  &#9474;
&#9474;                  &#9492;&#9472;&#9472;&#9496;              L&#9492;&#9472;&#9472;&#9496;R              &#9492;&#9472;&#9472;&#9496;                  &#9474;
&#9474;                                   CAPTURE                                    &#9474;
&#9474;                100<>100           100<>100           100<>100                &#9474;
&#9474;          <    Mic Boost     >     Capture       Internal Mic Boost           &#9474;
```

> Your microphone could be broken.  I've also already thought that it could be such a luck.

---

### Post by tgalati4 on 2015-02-19
Is the microphone on the screen bezel?  If so, the ribbon cable could be loose or broken.

If the microphone is near the keyboard, was there any liquid spilled on the keyboard?

Was the computer dropped?

Is this a dual-boot system?  If so, does it work in Windows?

Use a USB headset microphone or if you have a microphone port, use a standard headset microphone and see if that works.

---

