---
title: "NEED sound on Feisty Fawn ATI -- specific chipset, alsamixer data posted"
date: 2007-06-21
forum: Multimedia &amp; Video
---

### Post by johntkucz on 2007-06-21
Okay, I've been trying to get sound to work on my mx3701 laptop, but need help figuring out exactly what my sound card, manufacturer and chipset are, and some terminology defined before I can decipher out what the problem is and how to fix it for my system.

I followed:
e [http://ubuntuguide.org/wiki/Ubuntu:Feisty#Sound](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Sound)

to the key and plugged in "ref" (instead of 3stack) which was listed under the alsa-driver configuration text under the STAC9200 model, was that right?  When I 

 tail -2 /proc/asound/oss/sndstat
Mixers:
0: SigmaTel STAC9200

 cat /proc/interrupts
           CPU0       CPU1       
  0:     260534          0   IO-APIC-edge      timer
  1:       1038          0   IO-APIC-edge      i8042
  8:          3          0   IO-APIC-edge      rtc
 12:     317254          0   IO-APIC-edge      i8042
 14:      17696          0   IO-APIC-edge      ide0
 16:      22927      31170   IO-APIC-fasteoi   ohci_hcd:usb1, ehci_hcd:usb2, ohci_hcd:usb3
 17:      13495          0   IO-APIC-fasteoi   eth0, HDA Intel
 21:       1407          0   IO-APIC-fasteoi   acpi
NMI:          0          0 
LOC:     260271     260270 
ERR:          0
MIS:          0



dmesg  (the solution could be in here)
17
[   22.420000] si3054: cannot initialize. EXT MID = 0000
[   22.504000] NET: Registered protocol family 17
[   22.788000] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control rx
[   27.480000] sd 2:0:0:0: Attached scsi removable disk sdd
[   27.484000] SCSI device sde: 160836480 512-byte hdwr sectors (82348 MB)
[   27.484000] sde: Write Protect is off
[   27.484000] sde: Mode Sense: 2a 00 00 00
[   27.484000] sde: assuming drive cache: write through
[   27.484000] SCSI device sde: 160836480 512-byte hdwr sectors (82348 MB)
[   27.484000] sde: Write Protect is off
[   27.484000] sde: Mode Sense: 2a 00 00 00
[   27.484000] sde: assuming drive cache: write through
[   27.484000]  sde: sde1
[   27.500000] sd 1:0:0:0: Attached scsi disk sde
[   27.500000] SCSI device sdf: 1994751 512-byte hdwr sectors (1021 MB)
[   27.500000] sdf: Write Protect is off
[   27.500000] sdf: Mode Sense: 45 00 00 08
[   27.500000] sdf: assuming drive cache: write through
[   27.500000] SCSI device sdf: 1994751 512-byte hdwr sectors (1021 MB)
[   27.500000] sdf: Write Protect is off
[   27.500000] sdf: Mode Sense: 45 00 00 08
[   27.500000] sdf: assuming drive cache: write through
[   27.500000]  sdf: sdf1
[   27.504000] sd 5:0:0:0: Attached scsi removable disk sdf
[   27.996000] fuse init (API version 7.8)
[   28.084000] lp: driver loaded but no devices found
[   28.132000] Adding 1951856k swap on /dev/disk/by-uuid/2f2bc714-21c9-49ec-a278-72a74c8f8474.  Priority:-1 extents:1 across:1951856k
[   28.312000] EXT3 FS on hda2, internal journal
[   28.516000] NET: Registered protocol family 10
[   28.516000] lo: Disabled Privacy Extensions
[   38.672000] eth0: no IPv6 routers present
[   47.580000] kjournald starting.  Commit interval 5 seconds
[   47.580000] EXT3 FS on hda3, internal journal
[   47.580000] EXT3-fs: mounted filesystem with ordered data mode.
[   54.188000] input: Power Button (FF) as /class/input/input5
[   54.188000] ACPI: Power Button (FF) [PWRF]
[   54.188000] input: Power Button (CM) as /class/input/input6
[   54.188000] ACPI: Power Button (CM) [PWRB]
[   54.188000] input: Lid Switch as /class/input/input7
[   54.188000] ACPI: Lid Switch [LID0]
[   54.188000] input: Sleep Button (CM) as /class/input/input8
[   54.192000] ACPI: Sleep Button (CM) [SLPB]
[   54.372000] ACPI: Battery Slot [BAT0] (battery present)
[   54.420000] Using specific hotkey driver
[   54.528000] ibm_acpi: ec object not found
[   54.588000] No dock devices found.
[   54.688000] ACPI: AC Adapter [AC] (on-line)
[   54.836000] pcc_acpi: loading...
[   70.064000] ppdev: user-space parallel port driver
[   70.716000] apm: BIOS not found.
[   70.964000] ACPI: PCI interrupt for device 0000:00:14.2 disabled
[   70.996000] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 17
[   71.972000] si3054: cannot initialize. EXT MID = 0000
[   72.172000] Bluetooth: Core ver 2.11
[   72.172000] NET: Registered protocol family 31
[   72.172000] Bluetooth: HCI device and connection manager initialized
[   72.172000] Bluetooth: HCI socket layer initialized
[   72.212000] Bluetooth: L2CAP ver 2.8
[   72.212000] Bluetooth: L2CAP socket layer initialized
[   72.308000] Bluetooth: RFCOMM socket layer initialized
[   72.308000] Bluetooth: RFCOMM TTY layer initialized
[   72.308000] Bluetooth: RFCOMM ver 1.8
[   75.076000] hda-intel: Invalid position buffer, using LPIB read method instea

amixer
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [0.00dB] [on]
  Front Right: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 0 [0%] [0.00dB] [off]
  Front Right: Capture 0 [0%] [0.00dB] [off]
Simple mixer control 'Capture Mux',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 4
  Front Left: 0 [0%] [0.00dB]
  Front Right: 0 [0%] [0.00dB]
Simple mixer control 'Caller ID',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Input Source',0
  Capabilities: enum
  Items: 'Front Mic'
  Item0: 'Front Mic'
Simple mixer control 'Off-hook',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]

asoundconf list
Names of available sound cards:
SB

kooz@kooz-laptop:~$ cat /etc/asound.conf~/.asoundrc*
cat: /etc/asound.conf~/.asoundrc*: No such file or directory



aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

So I assumed stac9200 was right.  

lspci -v
00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)
        Subsystem: Gateway 2000 Unknown device 0318
        Flags: bus master, 66MHz, medium devsel, latency 64

00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        I/O behind bridge: 00009000-00009fff
        Memory behind bridge: d0000000-d00fffff
        Prefetchable memory behind bridge: d8000000-dfffffff
        Capabilities: <access denied>

00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=04, sec-latency=0
        I/O behind bridge: 0000a000-0000afff
        Memory behind bridge: d0100000-d01fffff
        Capabilities: <access denied>

00:05.0 PCI bridge: ATI Technologies Inc Unknown device 5a37 (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=07, sec-latency=0
        Capabilities: <access denied>

00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10 [OHCI])
        Subsystem: Gateway 2000 Unknown device 0318
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
        Memory at d0504000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10 [OHCI])
        Subsystem: Gateway 2000 Unknown device 0318
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
        Memory at d0505000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80) (prog-if 20 [EHCI])
        Subsystem: Gateway 2000 Unknown device 0318
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
        Memory at d0506000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
        Subsystem: Gateway 2000 Unknown device 0318
        Flags: 66MHz, medium devsel
        I/O ports at 8400 [size=16]
        Memory at d0507000 (32-bit, non-prefetchable) [size=1K]

00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80) (prog-if 8a [Master SecP PriP])
        Subsystem: Gateway 2000 Unknown device 0318
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 17
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 8410 [size=16]
        Capabilities: <access denied>

00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
        Subsystem: Gateway 2000 Unknown device 0318
        Flags: bus master, slow devsel, latency 64, IRQ 17
        Memory at d0500000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
        Subsystem: Gateway 2000 Unknown device 0318
        Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80) (prog-if 01 [Subtractive decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=08, subordinate=0a, sec-latency=64
        I/O behind bridge: 0000b000-0000bfff
        Memory behind bridge: f0200000-f02fffff
        Prefetchable memory behind bridge: f0300000-f03fffff

01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M] (prog-if 00 [VGA])
        Subsystem: Gateway 2000 Unknown device 0318
        Flags: bus master, 66MHz, medium devsel, latency 66, IRQ 10
        Memory at d8000000 (32-bit, prefetchable) [size=128M]
        I/O ports at 9000 [size=256]
        Memory at d0000000 (32-bit, non-prefetchable) [size=64K]
        [virtual] Expansion ROM at d0020000 [disabled] [size=128K]
        Capabilities: <access denied>

02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
        Subsystem: Gateway 2000 Unknown device 0318
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at d0100000 (64-bit, non-prefetchable) [size=16K]
        I/O ports at a000 [size=256]
        Capabilities: <access denied>

08:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)
        Subsystem: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
        Flags: bus master, medium devsel, latency 64, IRQ 11
        I/O ports at b000 [size=256]
        Memory at d0200000 (32-bit, non-prefetchable) [size=512]
        Capabilities: <access denied>

In alsamixer I see 10 columns: Master, PCM, LFE (recently turned on after following e [http://ubuntuguide.org/wiki/Ubuntu:Feisty#Sound](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Sound)), IEC958, Three Capture columns, Caller I, Input So, Off-hook.

Call I and Off-hook are muted, I have to manually unmute Master and LFE after every reboot.  
 
Could some of those sound channels be clashing?  Should I leave IEC958 off?  What IS IEC958, PCM, and LFE?

At the top it says: 
HDA ATI SB
SigmaTel STAC9200 for all those 10 channels. What does THAT mean?  Do I have an ATI manufacturer or an snd-hda-intel manufactuer?  What's the different between those two? Also, is SigmaTel the model (is that synonymous with chipset?) of the ATI soundcard?

Please help! Answering some of these questions will be a step in solving this problem for sure!

You can't mend the "ear"  (sound) if you don't know how to identify the ossicles, and whatnot (okay, obscure anatomical reference, but the point is you need to know the parts to fix the whole in this case).

Also, what is up with sound pref. panel?  The Default Mixer Tracks have options HDA ATI SB (Alsa mixer) and SigmaTel STAC9200 (OSS Mixer), then for sound events, Music and movies, and audio conferencing, it's set at ALSA, but have tried autodetect, and has STAC92xx Analog and digital as options, what should those be set at? 

-- John

---

### Post by fredj on 2007-06-22
Open a console then do
sudo gedit /etc/modprobe.d/alsa-base
Then enter this line at the bottom of the file
options snd-hda-intel model=STAC9200
Save file and reboot. 
Double click on the volume control to open the mixer and use preferences on the Edit menu to add all
the controls and switches you need and set them all to suitable values and unmute.

---

### Post by amarrero on 2007-09-02
Hi, it seems that we have the same sound cards and, of course, the same problems. I would like to know if you or somebody else have resolved the problem. I have tried the solution offered but it didn't work for me. Did it works for you?

Thanks.

---

