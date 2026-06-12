---
title: "[SOLVED] Sound out of ATI 2400HD hdmi, kind of"
date: 2008-08-06
forum: Multimedia Software
---

### Post by mythms on 2008-08-06
I am trying to get MythTv working with audio over HDMI.

I have an ATI Radeon HD 2400.  When connected to a Visio HD tv via the hdmi port I am getting SD video out of my Hauppage 350PVR, but no sound.  By issuing the following command I can make white-noise on the tv:

```
$>speaker-test -D plughw:0,3

speaker-test 1.0.15

Playback device is plughw:0,3
Stream parameters are 48000Hz, S16_LE, 1 channels
Using 16 octaves of pink noise
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 64 to 16384
Period size range from 32 to 8192
Using max buffer size 16384
Periods = 4
was set period_size = 4096
was set buffer_size = 16384
 0 - Front Left

```

This indicates to me that I have some level of support for audio over hdmi.  

Anyone have any pointers on the next step required set up device files and configure in mythtv?

Output from lspci, aplay -L, and aplay -l are given below.

```
> $lspci -v

00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
        Subsystem: Hewlett-Packard Company Unknown device 2a26
        Flags: bus master, 66MHz, medium devsel, latency 64

00:02.0 PCI bridge: ATI Technologies Inc RS480 PCI-X Root Port (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 0000e000-0000efff
        Memory behind bridge: fdd00000-fddfffff
        Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
        Capabilities: [50] Power Management version 3
        Capabilities: [58] Express Root Port (Slot-) IRQ 0
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [b0] Subsystem: Hewlett-Packard Company Unknown device 2a26
        Capabilities: [b8] HyperTransport: MSI Mapping

00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: Hewlett-Packard Company Unknown device 2a26
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 11
        I/O ports at ff00 [size=8]
        I/O ports at fe00 [size=4]
        I/O ports at fd00 [size=8]
        I/O ports at fc00 [size=4]
        I/O ports at fb00 [size=16]
        Memory at fe02f000 (32-bit, non-prefetchable) [size=512]
        [virtual] Expansion ROM at 40000000 [disabled] [size=512K]
        Capabilities: [60] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-

00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (prog-if 10 [OHCI])
        Subsystem: Hewlett-Packard Company Unknown device 2a26
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 4
        Memory at fe02e000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-

00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (prog-if 10 [OHCI])
        Subsystem: Hewlett-Packard Company Unknown device 2a26
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 4
        Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-

00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (prog-if 20 [EHCI])
        Subsystem: Hewlett-Packard Company Unknown device 2a26
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 4
        Memory at fe02c000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [dc] Power Management version 2
        Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-

00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
        Subsystem: Hewlett-Packard Company Unknown device 2a26
        Flags: 66MHz, medium devsel
        I/O ports at 0b00 [size=16]
        Memory at fe02b000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [b0] HyperTransport: MSI Mapping

00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (prog-if 8a [Master SecP PriP])
        Subsystem: Hewlett-Packard Company Unknown device 2a26
        Flags: bus master, 66MHz, medium devsel, latency 64
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at f900 [size=16]
        Capabilities: [70] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-

00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
        Subsystem: Hewlett-Packard Company Unknown device 2a26
        Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (prog-if 01 [Subtractive decode])
        Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=64
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: fde00000-fdefffff
        Prefetchable memory behind bridge: f8000000-fbffffff

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
        Flags: fast devsel
        Capabilities: [80] HyperTransport: Host or Secondary Interface

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
        Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
        Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
        Flags: fast devsel

01:00.0 VGA compatible controller: ATI Technologies Inc RV610 video device [Radeon HD 2400 PRO] (prog-if 00 [VGA controller])
        Subsystem: Micro-Star International Co., Ltd. Unknown device 1100
        Flags: bus master, fast devsel, latency 0, IRQ 5
        Memory at d0000000 (64-bit, prefetchable) [size=256M]
        Memory at fdde0000 (64-bit, non-prefetchable) [size=64K]
        I/O ports at ee00 [size=256]
        [virtual] Expansion ROM at fdd00000 [disabled] [size=128K]
        Capabilities: [50] Power Management version 3
        Capabilities: [58] Express Legacy Endpoint IRQ 0
        Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-

01:00.1 Audio device: ATI Technologies Inc RV610 audio device [Radeon HD 2400 PRO]
        Subsystem: Micro-Star International Co., Ltd. Unknown device aa10
        Flags: bus master, fast devsel, latency 0, IRQ 4
        Memory at fddfc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 3
        Capabilities: [58] Express Legacy Endpoint IRQ 0
        Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-

02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Hewlett-Packard Company Unknown device 2a26
        Flags: bus master, medium devsel, latency 64, IRQ 10
        I/O ports at de00 [size=256]
        Memory at fdeff000 (32-bit, non-prefetchable) [size=256]
        Capabilities: [50] Power Management version 2

02:09.0 Multimedia video controller: Internext Compression Inc iTVC15 MPEG-2 Encoder (rev 01)
        Subsystem: Hauppauge computer works Inc. WinTV PVR-350
        Flags: bus master, medium devsel, latency 64, IRQ 3
        Memory at f8000000 (32-bit, prefetchable) [size=64M]
        Capabilities: [44] Power Management version 2

$>aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

$>aplay -L
front:CARD=HDMI
    HDA ATI HDMI
    Front speakers
surround40:CARD=HDMI
    HDA ATI HDMI
    4.0 Surround output to Front and Rear speakers
surround41:CARD=HDMI
    HDA ATI HDMI
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=HDMI
    HDA ATI HDMI
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=HDMI
    HDA ATI HDMI
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=HDMI
    HDA ATI HDMI
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
null
    Discard all samples (playback) or generate zero samples (capture)


```

I am kind of a noob around the Linux Multi-media but have been installing using Linux since mid '90's.

---

### Post by mythms on 2008-08-06
Now passing audio over hdmi.  Found the answer here in the 'Use Your Device' section. [_[COLOR="Blue"]http://alsa.opensrc.org/index.php/DigitalOut[/COLOR]_]("http://alsa.opensrc.org/index.php/DigitalOut")

MythTV->Utilities/Setup->Setup->General, on the third page, by typing 'ALSA:plughw:0,3' into Audio output device.  Here are my settings for all of the parameters on the Audio page:

Audio output device: ALSA:plughw:0,3
Passthrough output device: ALSA:plughw:0,3
Max Audio Channels: Stereo
Upmix: Passive
[x] Enable AC3 to SPDIF passthrough
[x] Enable DTS to SPDIF passthrough
[ ] Agressive Sound card Buffering
[x] Use internal volume controls
Mixer Device: /dev/mixer
Mixer Controls: PCM
Master Mixer Volume: 70
PCM Mixer Volume: 52
[ ] Independent Muting of Left and Right Audio Channels

Next:
* Determining if possible to control the volume with the myth controls
* Figure out how to get Podcast audio to play over hdmi

---

