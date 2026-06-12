---
title: "no DTS 5.1 over HDMI with via vt1705b"
date: 2011-10-06
forum: Multimedia Software
---

### Post by mbah.pande on 2011-10-06
Hi

I've got problem with my audio
I'm using AMD E350 board with via vt 1705b audio codec on board running with ubuntu 11.04 64bit kernel update to 2.6.38-11 generic and got linux-alsa-driver-modules from ppa:ubuntu-audio-dev/ppa

my trouble is so difficult to understand for me because it's so weired i play movie with dts-5.1 and dts-7.1 with analog speaker everything it's OK but when i switch to HDMI only dts-5.1 audio wont work, dts7.1 and the other work fine

any idea about this?


PS: Using XBMC to play movie

Thanks

---

### Post by nhtrader on 2011-10-07
I don't have a solution, but it might help if you post more details and discover what your system has.

Post your system's output to these commands which will show what you have.

I use these in user mode rather than root...
amixer
iecset -x
arecord -L 
arecord -l
lshw
lspci -v
cat /proc/asound/card0/codec*
ls /dev/snd

Then after you learn what devices your system has, you should check out these webpages for some insights as to how to proceed.

[http://www.mythtv.org/wiki/Digital_Audio_Tutorial](http://www.mythtv.org/wiki/Digital_Audio_Tutorial)
[http://alsa.opensrc.org/.asoundrc](http://alsa.opensrc.org/.asoundrc)
[http://www.sabi.co.uk/Notes/linuxSoundALSA.html#tasks](http://www.sabi.co.uk/Notes/linuxSoundALSA.html#tasks)

then when you try new settings, use these commands to test it.
speaker-test -twav -c2 (stereo)
speaker-test -twav -c6 -Dplug:surround51 (5.1)


Hope this helps you to get started.

---

### Post by mbah.pande on 2011-10-07
Thanks a lot for suggestion. but I'm still confuse, would you please teach me how?

here is result off command that you explain

amixer 

> Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
iecset -x

> AES0=0x04,AES1=0x00,AES2=0x00,AES3=0x00
arecord -L

> default
    Playback/recording through the PulseAudio sound server
pulse
    Playback/recording through the PulseAudio sound server
front:CARD=SB,DEV=0
    HDA ATI SB, VT1705 Analog
    Front speakers
surround40:CARD=SB,DEV=0
    HDA ATI SB, VT1705 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=SB,DEV=0
    HDA ATI SB, VT1705 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=SB,DEV=0
    HDA ATI SB, VT1705 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=SB,DEV=0
    HDA ATI SB, VT1705 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=SB,DEV=0
    HDA ATI SB, VT1705 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
dmix:CARD=SB,DEV=0
    HDA ATI SB, VT1705 Analog
    Direct sample mixing device
dsnoop:CARD=SB,DEV=0
    HDA ATI SB, VT1705 Analog
    Direct sample snooping device
hw:CARD=SB,DEV=0
    HDA ATI SB, VT1705 Analog
    Direct hardware device without any conversions
plughw:CARD=SB,DEV=0
    HDA ATI SB, VT1705 Analog
    Hardware device with all software conversionsarecord -l 

> **** List of CAPTURE Hardware Devices ****
card 1: SB [HDA ATI SB], device 0: VT1705 Analog [VT1705 Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1

lshw 

>  00:00.0 Host bridge: Advanced Micro Devices [AMD] Pavilion DM1Z-3000 Host bridge
    Subsystem: Elitegroup Computer Systems Device 3137
    Flags: bus master, 66MHz, medium devsel, latency 32

00:01.0 VGA compatible controller: ATI Technologies Inc Device 9802 (prog-if 00 [VGA controller])
    Subsystem: Elitegroup Computer Systems Device 3137
    Flags: bus master, fast devsel, latency 0, IRQ 42
    Memory at d0000000 (32-bit, prefetchable) [size=256M]
    I/O ports at f000 [size=256]
    Memory at feb00000 (32-bit, non-prefetchable) [size=256K]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: fglrx_pci
    Kernel modules: fglrx, radeon

00:01.1 Audio device: ATI Technologies Inc Device 1314
    Subsystem: Elitegroup Computer Systems Device 3137
    Flags: bus master, fast devsel, latency 0, IRQ 41
    Memory at feb44000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

00:04.0 PCI bridge: Advanced Micro Devices [AMD] Device 1512 (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00001000-00001fff
    Memory behind bridge: 7f000000-7f1fffff
    Prefetchable memory behind bridge: 000000007f200000-000000007f3fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:11.0 SATA controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode] (rev 40) (prog-if 01 [AHCI 1.0])
    Subsystem: Elitegroup Computer Systems Device 4390
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 19
    I/O ports at f190 [size=8]
    I/O ports at f180 [size=4]
    I/O ports at f170 [size=8]
    I/O ports at f160 [size=4]
    I/O ports at f150 [size=16]
    Memory at feb4f000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci

00:12.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller (prog-if 10 [OHCI])
    Subsystem: Elitegroup Computer Systems Device 3137
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
    Memory at feb4e000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:12.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller (prog-if 20 [EHCI])
    Subsystem: Elitegroup Computer Systems Device 3137
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
    Memory at feb4d000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:13.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller (prog-if 10 [OHCI])
    Subsystem: Elitegroup Computer Systems Device 3137
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
    Memory at feb4c000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller (prog-if 20 [EHCI])
    Subsystem: Elitegroup Computer Systems Device 3137
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
    Memory at feb4b000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 42)
    Subsystem: Elitegroup Computer Systems Device 3137
    Flags: 66MHz, medium devsel
    Kernel driver in use: piix4_smbus
    Kernel modules: sp5100_tco, i2c-piix4

00:14.1 IDE interface: ATI Technologies Inc SB7x0/SB8x0/SB9x0 IDE Controller (rev 40) (prog-if 8a [Master SecP PriP])
    Subsystem: Elitegroup Computer Systems Device 3137
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at f100 [size=16]
    Kernel driver in use: pata_atiixp
    Kernel modules: pata_atiixp

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
    Subsystem: Elitegroup Computer Systems Device 3137
    Flags: bus master, slow devsel, latency 32, IRQ 16
    Memory at feb40000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

00:14.3 ISA bridge: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
    Subsystem: Elitegroup Computer Systems Device 3137
    Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40) (prog-if 01 [Subtractive decode])
    Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=64

00:14.5 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI2 Controller (prog-if 10 [OHCI])
    Subsystem: Elitegroup Computer Systems Device 3137
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
    Memory at feb4a000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:15.0 PCI bridge: ATI Technologies Inc Device 43a0 (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:15.2 PCI bridge: ATI Technologies Inc Device 43a2 (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: fea00000-feafffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:16.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller (prog-if 10 [OHCI])
    Subsystem: Elitegroup Computer Systems Device 3137
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
    Memory at feb49000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:16.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller (prog-if 20 [EHCI])
    Subsystem: Elitegroup Computer Systems Device 3137
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
    Memory at feb48000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 0 (rev 43)
    Flags: fast devsel

00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 1
    Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 2
    Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 3
    Flags: fast devsel
    Capabilities: <access denied>
    Kernel driver in use: k10temp
    Kernel modules: k10temp

00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 4
    Flags: fast devsel

00:18.5 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 6
    Flags: fast devsel

00:18.6 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 5
    Flags: fast devsel

00:18.7 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 7
    Flags: fast devsel

04:00.0 Ethernet controller: Atheros Communications Device 1083 (rev c0)
    Subsystem: Elitegroup Computer Systems Device 8151
    Flags: bus master, fast devsel, latency 0, IRQ 40
    Memory at fea00000 (64-bit, non-prefetchable) [size=256K]
    I/O ports at e000 [size=128]
    Capabilities: <access denied>
    Kernel driver in use: atl1c
    Kernel modules: atl1clspci -v

>  00:00.0 Host bridge: Advanced Micro Devices [AMD] Pavilion DM1Z-3000 Host bridge
    Subsystem: Elitegroup Computer Systems Device 3137
    Flags: bus master, 66MHz, medium devsel, latency 32

00:01.0 VGA compatible controller: ATI Technologies Inc Device 9802 (prog-if 00 [VGA controller])
    Subsystem: Elitegroup Computer Systems Device 3137
    Flags: bus master, fast devsel, latency 0, IRQ 42
    Memory at d0000000 (32-bit, prefetchable) [size=256M]
    I/O ports at f000 [size=256]
    Memory at feb00000 (32-bit, non-prefetchable) [size=256K]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: fglrx_pci
    Kernel modules: fglrx, radeon

00:01.1 Audio device: ATI Technologies Inc Device 1314
    Subsystem: Elitegroup Computer Systems Device 3137
    Flags: bus master, fast devsel, latency 0, IRQ 41
    Memory at feb44000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

00:04.0 PCI bridge: Advanced Micro Devices [AMD] Device 1512 (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00001000-00001fff
    Memory behind bridge: 7f000000-7f1fffff
    Prefetchable memory behind bridge: 000000007f200000-000000007f3fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:11.0 SATA controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode] (rev 40) (prog-if 01 [AHCI 1.0])
    Subsystem: Elitegroup Computer Systems Device 4390
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 19
    I/O ports at f190 [size=8]
    I/O ports at f180 [size=4]
    I/O ports at f170 [size=8]
    I/O ports at f160 [size=4]
    I/O ports at f150 [size=16]
    Memory at feb4f000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci

00:12.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller (prog-if 10 [OHCI])
    Subsystem: Elitegroup Computer Systems Device 3137
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
    Memory at feb4e000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:12.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller (prog-if 20 [EHCI])
    Subsystem: Elitegroup Computer Systems Device 3137
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
    Memory at feb4d000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:13.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller (prog-if 10 [OHCI])
    Subsystem: Elitegroup Computer Systems Device 3137
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
    Memory at feb4c000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller (prog-if 20 [EHCI])
    Subsystem: Elitegroup Computer Systems Device 3137
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
    Memory at feb4b000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 42)
    Subsystem: Elitegroup Computer Systems Device 3137
    Flags: 66MHz, medium devsel
    Kernel driver in use: piix4_smbus
    Kernel modules: sp5100_tco, i2c-piix4

00:14.1 IDE interface: ATI Technologies Inc SB7x0/SB8x0/SB9x0 IDE Controller (rev 40) (prog-if 8a [Master SecP PriP])
    Subsystem: Elitegroup Computer Systems Device 3137
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at f100 [size=16]
    Kernel driver in use: pata_atiixp
    Kernel modules: pata_atiixp

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
    Subsystem: Elitegroup Computer Systems Device 3137
    Flags: bus master, slow devsel, latency 32, IRQ 16
    Memory at feb40000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

00:14.3 ISA bridge: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
    Subsystem: Elitegroup Computer Systems Device 3137
    Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40) (prog-if 01 [Subtractive decode])
    Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=64

00:14.5 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI2 Controller (prog-if 10 [OHCI])
    Subsystem: Elitegroup Computer Systems Device 3137
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
    Memory at feb4a000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:15.0 PCI bridge: ATI Technologies Inc Device 43a0 (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:15.2 PCI bridge: ATI Technologies Inc Device 43a2 (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: fea00000-feafffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:16.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller (prog-if 10 [OHCI])
    Subsystem: Elitegroup Computer Systems Device 3137
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
    Memory at feb49000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:16.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller (prog-if 20 [EHCI])
    Subsystem: Elitegroup Computer Systems Device 3137
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
    Memory at feb48000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 0 (rev 43)
    Flags: fast devsel

00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 1
    Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 2
    Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 3
    Flags: fast devsel
    Capabilities: <access denied>
    Kernel driver in use: k10temp
    Kernel modules: k10temp

00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 4
    Flags: fast devsel

00:18.5 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 6
    Flags: fast devsel

00:18.6 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 5
    Flags: fast devsel

00:18.7 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 7
    Flags: fast devsel

04:00.0 Ethernet controller: Atheros Communications Device 1083 (rev c0)
    Subsystem: Elitegroup Computer Systems Device 8151
    Flags: bus master, fast devsel, latency 0, IRQ 40
    Memory at fea00000 (64-bit, non-prefetchable) [size=256K]
    I/O ports at e000 [size=128]
    Capabilities: <access denied>
    Kernel driver in use: atl1c
    Kernel modules: atl1ccat /proc/asound/card0/codec*

>  Codec: ATI R6xx HDMI
Address: 0
AFG Function Id: 0x1 (unsol 0)
Vendor Id: 0x1002aa01
Subsystem Id: 0x00aa0100
Revision Id: 0x100200
No Modem Function Group found
Default PCM:
    rates [0x70]: 32000 44100 48000
    bits [0x2]: 16
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x02 [Audio Output] wcaps 0x201: Stereo Digital
  Converter: stream=1, channel=0
  Digital: Enabled GenLevel
  Digital category: 0x2
Node 0x03 [Pin Complex] wcaps 0x400381: Stereo Digital
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Pincap 0x00000094: OUT Detect HDMI
  Pin Default 0x18560010: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x00:
  Unsolicited: tag=03, enabled=1
  Connection: 1
     0x02ls /dev/snd

> by-path
controlC0
controlC1
hwC0D0
hwC1D0
pcmC0D3p
pcmC1D0c
pcmC1D0p
pcmC1D1p
pcmC1D2p
seq
timer

thats what I have. refers to link that you mentioned still difficult to me to understand

FYI : HDMI useng converter from DVI to HDMI

---

### Post by nhtrader on 2011-10-08
As mentioned earlier, I don't have a solution for you.

1. However, I am confused b/c I'm unfamiliar with DVI. I thought DVI was strictly video only. I didn't think that it transports audio. Whereas HDMI was designed to transmit both audio and video. So, converting the DVI to HDMI would imply that you don't have any audio. But, yet you state that 7.1 audio works. This baffles me. Please describe in detail how you connect your computer to your TV/Receiver. How many wires do you use? Which wires do you use?

2. I see that PulseAudio is your sound server. I use ALSA and in fact the link from the UK states that ALSA is reprefered over PulseAudio. But I wouldn't make the switch just yet.

3. I see that you are using an ATI chipset. You may wish to install AMD/ATI proprietary drivers which are not installed by default. This may resolve the problem since open source drivers maybe insufficient with your hardware config.

4. I see that you have 2 audio devices but neither of them indicate digital audio devices, both report analog. Also, both of "arecord"s output don't indicate any digital devices which is odd, but this maybe the way PulseAudio handles devices. With ALSA, you'd see all analog and digital devices.

---

### Post by mbah.pande on 2011-10-08
even you don't give the solution directly but following your step it's really help me, thank's alot for it 

OK

1. I only using DVI to HDMI converter like this

[IMG]http://img191.imageshack.us/img191/8831/image003teq.jpg[/IMG]
 so only use one hdmi cable and with this cable dts-7.1 work OK but it's after upgrade linux-alsa-driver-modules from ppa:ubuntu-audio-dev/ppa and before won't work either dts-5.1 and dts-7.1 and refers to this [http://www.tomshardware.com/forum/257301-33-hdmi-adapter-audio-conundrum](http://www.tomshardware.com/forum/257301-33-hdmi-adapter-audio-conundrum) DVI can carry audio signal somehow

2. It's because i upgrade ALSA from linux-alsa-driver-modules from ppa:ubuntu-audio-dev/ppa, as I mention before upgrade dts-5.1 and dts-7.1 wont work either ove analog and HDMI

3. Yes I don't install ATI proprietary by default but get deb by running this code
> cd ~; mkdir catalyst11.9; cd catalyst11.9
wget [http://www2.ati.com/drivers/linux/ati-driver-installer-11-9-x86.x86_64.run](http://www2.ati.com/drivers/linux/ati-driver-installer-11-9-x86.x86_64.run)
chmod +x ati-driver-installer-11-9-x86.x86_64.run
sudo sh ./ati-driver-installer-11-9-x86.x86_64.run --extract ati
cd ati
sudo ./ati-installer.sh 8.892 --buildpkg Ubuntu/natty
cd ..
sudo rm -rf ati
sudo dpkg -i fglrx*.deb
if this is wrong i will installed by default

4. when i running arecord i use analog audio not use HDMI should i run that command in when use HDMI?

---

### Post by nhtrader on 2011-10-08
Ipresume that you've checked your audio mixer. It should be set to use HDMI, or in your case does it say DVI? I use command "alsamixer" or in graphical mode I select from Menu|Multimedia|Mmixer to enable/disable audio inputs/outputs.

---

