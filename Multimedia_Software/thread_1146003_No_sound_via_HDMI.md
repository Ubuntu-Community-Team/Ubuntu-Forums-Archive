---
title: "No sound via HDMI"
date: 2009-05-02
forum: Multimedia Software
---

### Post by j0hnsmith on 2009-05-02
My motherboard is an Asus M2A-VM HDMI, it has HDMI via a PCI express card but this uses the onboard video/sound provided by the 690G chipset. I have the computer connected to my TV using a HDMI cable but there's no sound, I don't have a normal monitor connected. In Win XP everything works fine.

Lack of sound via HDMI seems to be a common problem on many different motherboards and Linux distros.

I started with a clean install of Ubuntu 8.10, the only changes I've made have been my attempts to make the sound work.

I've upgraded the ALSA driver to the latest version (1.0.19) using the instructions [here]("http://xbmc.org/wiki/?title=HOW-TO_install_XBMC_for_Linux_on_Ubuntu_8.04_%28Hardy%29_and_8.10_%28Intrepid%29_step-by-step#Upgrading_ALSA_.28sound_driver.29_to_the_latest_version").

When I unmuted the IEC958 channels in alsamixer there were only 2, the guide says there should be 3.

I've tried many tests for all the different options in the Sounds preferences and enabled IEC958 in the volume control dialogue box.

I don't know what else I can do. Any help would be massively appreciated.


Here's the aplay -l output

```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0 

```and here's the output of sudo lspci -v

```
$ sudo lspci -v
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
    Subsystem: ASUSTeK Computer Inc. Device 826d
    Flags: bus master, 66MHz, medium devsel, latency 64
    Kernel modules: ati-agp

00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
    Flags: bus master, 66MHz, medium devsel, latency 99
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=68
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: fda00000-fdbfffff
    Prefetchable memory behind bridge: 00000000f0000000-00000000f7ffffff
    Capabilities: [44] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [b0] Subsystem: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
    Kernel modules: shpchp

00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: fdf00000-fdffffff
    Prefetchable memory behind bridge: 00000000fdc00000-00000000fdcfffff
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Port (Slot-), MSI 00
    Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
    Capabilities: [b0] Subsystem: ASUSTeK Computer Inc. Device 826d
    Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [100] Virtual Channel <?>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA (prog-if 01)
    Subsystem: ASUSTeK Computer Inc. Device 81ef
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 22
    I/O ports at ff00 [size=8]
    I/O ports at fe00 [size=4]
    I/O ports at fd00 [size=8]
    I/O ports at fc00 [size=4]
    I/O ports at fb00 [size=16]
    Memory at fe02f000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [60] Power Management version 2
    Kernel driver in use: ahci
    Kernel modules: ahci

00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0) (prog-if 10)
    Subsystem: ASUSTeK Computer Inc. Device 81ef
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
    Memory at fe02e000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd
    Kernel modules: ohci-hcd

00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1) (prog-if 10)
    Subsystem: ASUSTeK Computer Inc. Device 81ef
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
    Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd
    Kernel modules: ohci-hcd

00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2) (prog-if 10)
    Subsystem: ASUSTeK Computer Inc. Device 81ef
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at fe02c000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd
    Kernel modules: ohci-hcd

00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3) (prog-if 10)
    Subsystem: ASUSTeK Computer Inc. Device 81ef
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
    Memory at fe02b000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd
    Kernel modules: ohci-hcd

00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4) (prog-if 10)
    Subsystem: ASUSTeK Computer Inc. Device 81ef
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at fe02a000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd
    Kernel modules: ohci-hcd

00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI) (prog-if 20)
    Subsystem: ASUSTeK Computer Inc. Device 81ef
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
    Memory at fe029000 (32-bit, non-prefetchable) [size=256]
    Capabilities: [c0] Power Management version 2
    Capabilities: [e4] Debug port: BAR=1 offset=00e0
    Kernel driver in use: ehci_hcd
    Kernel modules: ehci-hcd

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
    Subsystem: ASUSTeK Computer Inc. Device 81ef
    Flags: 66MHz, medium devsel
    I/O ports at 0b00 [size=16]
    Capabilities: [b0] HyperTransport: MSI Mapping Enable- Fixed+
    Kernel driver in use: piix4_smbus
    Kernel modules: i2c-piix4

00:14.1 IDE interface: ATI Technologies Inc SB600 IDE (prog-if 8a [Master SecP PriP])
    Subsystem: ASUSTeK Computer Inc. Device 81ef
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at f900 [size=16]
    Kernel driver in use: pata_atiixp
    Kernel modules: pata_atiixp

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
    Subsystem: ASUSTeK Computer Inc. Device 8249
    Flags: bus master, slow devsel, latency 64, IRQ 16
    Memory at fe020000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
    Subsystem: ASUSTeK Computer Inc. Device 81ef
    Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (prog-if 01)
    Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=64
    I/O behind bridge: 0000c000-0000cfff
    Memory behind bridge: fde00000-fdefffff
    Prefetchable memory behind bridge: fdd00000-fddfffff

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
    Flags: fast devsel
    Capabilities: [80] HyperTransport: Host or Secondary Interface

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
    Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
    Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
    Flags: fast devsel
    Capabilities: [f0] Secure device <?>
    Kernel driver in use: k8temp
    Kernel modules: k8temp

01:05.0 VGA compatible controller: ATI Technologies Inc RS690 [Radeon X1200 Series]
    Subsystem: ASUSTeK Computer Inc. Device 826d
    Flags: bus master, fast devsel, latency 64, IRQ 18
    Memory at f0000000 (64-bit, prefetchable) [size=128M]
    Memory at fdbe0000 (64-bit, non-prefetchable) [size=64K]
    I/O ports at de00 [size=256]
    Memory at fda00000 (32-bit, non-prefetchable) [size=1M]
    Capabilities: [50] Power Management version 2
    Capabilities: [80] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-

01:05.2 Audio device: ATI Technologies Inc Radeon X1200 Series Audio Controller
    Subsystem: ATI Technologies Inc Radeon X1200 Series Audio Controller
    Flags: bus master, fast devsel, latency 64, IRQ 19
    Memory at fdbfc000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
    Subsystem: ASUSTeK Computer Inc. Device 81aa
    Flags: bus master, fast devsel, latency 0, IRQ 222
    I/O ports at ee00 [size=256]
    Memory at fdfff000 (64-bit, non-prefetchable) [size=4K]
    [virtual] Expansion ROM at fdc00000 [disabled] [size=128K]
    Capabilities: [40] Power Management version 2
    Capabilities: [48] Vital Product Data <?>
    Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
    Capabilities: [60] Express Endpoint, MSI 00
    Capabilities: [84] Vendor Specific Information <?>
    Capabilities: [100] Advanced Error Reporting <?>
    Capabilities: [12c] Virtual Channel <?>
    Capabilities: [148] Device Serial Number 68-81-ec-10-00-00-00-1a
    Capabilities: [154] Power Budgeting <?>
    Kernel driver in use: r8169
    Kernel modules: r8169

03:07.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev c0) (prog-if 10)
    Subsystem: ASUSTeK Computer Inc. Device 81fe
    Flags: bus master, medium devsel, latency 64, IRQ 22
    Memory at fdeff000 (32-bit, non-prefetchable) [size=2K]
    I/O ports at cf00 [size=128]
    Capabilities: [50] Power Management version 2
    Kernel driver in use: ohci1394
    Kernel modules: ohci1394

```

---

### Post by hakamade on 2009-05-16
I don't have sound via HDMI either. I originally installed 8.10, but upgraded to 9.04. This is anything but a clean install due to a ton of hardware issues and a million failed attempts at fixing them.

I've installed ALSA 1.0.20 (I think). The sound settings screen shows "HDA ATI HDMI ATI HDMI (ALSA)", in all of sound events, music and movies, and sound negotiation. Testing the setting gives no sound, but the "detect automatically" setting gives a sound from the laptop speakers.

Here's aplay -l (it's in Finnish but I suppose the words can be guessed from context :)):

```

**** Luettelo PLAYBACK laitteista ****
kortti 0: SB [HDA ATI SB], laite 0: ALC262 Analog [ALC262 Analog]
  Alalaitteet: 1/1
  Alalaite #0: subdevice #0
kortti 1: HDMI [HDA ATI HDMI], laite 3: ATI HDMI [ATI HDMI]
  Alalaitteet: 1/1
  Alalaite #0: subdevice #0

```And lspci -v (there seem to be two audio cards):

```

00:00.0 Host bridge: ATI Technologies Inc Radeon Xpress 7930 Host Bridge
    Subsystem: LG Electronics, Inc. Device 011b
    Flags: bus master, 66MHz, medium devsel, latency 64

00:01.0 PCI bridge: ATI Technologies Inc RS7932 PCI Bridge
    Flags: bus master, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
    I/O behind bridge: 00009000-00009fff
    Memory behind bridge: dfe00000-dfefffff
    Prefetchable memory behind bridge: 00000000e0000000-00000000efffffff
    Capabilities: <access denied>
    Kernel modules: shpchp

00:04.0 PCI bridge: ATI Technologies Inc Device 7934
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=04, sec-latency=0
    I/O behind bridge: 0000a000-0000afff
    Memory behind bridge: f4400000-f44fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:06.0 PCI bridge: ATI Technologies Inc RS7936 PCI Bridge
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=07, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:07.0 PCI bridge: ATI Technologies Inc Device 7937
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=08, subordinate=0a, sec-latency=0
    Memory behind bridge: f4300000-f43fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA (prog-if 01)
    Subsystem: LG Electronics, Inc. Device 011b
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 22
    I/O ports at 8438 [size=8]
    I/O ports at 8444 [size=4]
    I/O ports at 8430 [size=8]
    I/O ports at 8440 [size=4]
    I/O ports at 8400 [size=16]
    Memory at f4209000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ahci

00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0) (prog-if 10)
    Subsystem: LG Electronics, Inc. Device 011b
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
    Memory at f4004000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1) (prog-if 10)
    Subsystem: LG Electronics, Inc. Device 011b
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
    Memory at f4005000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2) (prog-if 10)
    Subsystem: LG Electronics, Inc. Device 011b
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at f4006000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3) (prog-if 10)
    Subsystem: LG Electronics, Inc. Device 011b
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
    Memory at f4007000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4) (prog-if 10)
    Subsystem: LG Electronics, Inc. Device 011b
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at f4008000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI) (prog-if 20)
    Subsystem: LG Electronics, Inc. Device 011b
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
    Memory at f4209400 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
    Subsystem: LG Electronics, Inc. Device 011b
    Flags: 66MHz, medium devsel
    I/O ports at 8410 [size=16]
    Kernel driver in use: piix4_smbus
    Kernel modules: i2c-piix4

00:14.1 IDE interface: ATI Technologies Inc SB600 IDE (prog-if 8a [Master SecP PriP])
    Subsystem: LG Electronics, Inc. Device 011b
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at 8420 [size=16]
    Kernel driver in use: pata_atiixp

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
    Subsystem: LG Electronics, Inc. Device 011b
    Flags: bus master, slow devsel, latency 64, IRQ 16
    Memory at f4000000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel

00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
    Subsystem: LG Electronics, Inc. Device 011b
    Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (prog-if 01)
    Flags: bus master, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=0b, subordinate=0d, sec-latency=64

01:05.0 VGA compatible controller: ATI Technologies Inc Radeon Xpress 1250
    Subsystem: LG Electronics, Inc. Device 011b
    Flags: bus master, fast devsel, latency 64, IRQ 18
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    Memory at dfef0000 (64-bit, non-prefetchable) [size=64K]
    I/O ports at 9000 [size=256]
    Capabilities: <access denied>

01:05.2 Audio device: ATI Technologies Inc RS600 audio device [Radeon Xpress 12xx Series]
    Subsystem: LG Electronics, Inc. Device 011b
    Flags: bus master, fast devsel, latency 64, IRQ 19
    Memory at dfeec000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel

02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller (rev 15)
    Subsystem: LG Electronics, Inc. Device 011b
    Flags: bus master, fast devsel, latency 0, IRQ 2300
    Memory at f4400000 (64-bit, non-prefetchable) [size=16K]
    I/O ports at a000 [size=256]
    Capabilities: <access denied>
    Kernel driver in use: sky2
    Kernel modules: sky2

08:00.0 Network controller: RaLink RT2860
    Subsystem: RaLink Device 2790
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at f4300000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: rt2860
    Kernel modules: rt2860sta

```Hopefully someone knows how to solve this. I'm going back to XP for now. Maybe that'll work where neither ubuntu nor visva did.

---

### Post by mspaul on 2009-07-15
Same video card and issues here.  No hdmi sound yet I have sound through laptop speakers.

I am a noob and this is the only thing holding me back from using Ubuntu fulltime.

---

### Post by luken8r on 2009-07-15
I have nothing of substance to add other than I am having the same problem. Im on a HP DV5 laptop with the HDMI port on the side. Worked like a champ in Vista, but no dice yet on Ubuntu. If anyone has any suggestions for those of use w/o audio over HDMI Im all ears

---

### Post by igorzwx on 2009-07-15
ask markbuntu

---

### Post by mspaul on 2009-07-17
> **igorzwx said:**
> ask markbuntu

Will do, thanks.

---

### Post by zodiac09 on 2009-07-18
I had the same problem today with my HDMI port. it was my first time using it.  I found a solution for my ATI card in my laptop. I am not sure if this will help u guys. like don't go installing the wrong driver or anything. U may even just have to edit xorg.conf . I suggest reading through it. then decide what to do first

[http://www.mediaboxblog.co.uk/blog1.php/2008/10/03/howto-compiling-and-running-radeonhd](http://www.mediaboxblog.co.uk/blog1.php/2008/10/03/howto-compiling-and-running-radeonhd)

also. when i ran the command 

git-clone git://anongit.freedesktop.org/git/xorg/driver/xf86-video-radeonhd

i didin't need the hyphen "-" between git-clone. Just used git clone
u may have to as well

---

### Post by mspaul on 2009-07-18
Thanks for the reply

couldn't get it to work... I tried my best but in the end I'm a noob.  

I'm not sure what to put after Identifier (my card is a xpress 1250 but I don't know exactly what goes there):

Section "Device"
  Identifier  "Radeon HD3200 Driver"
  Driver  "radeonhd"
  Option  "Audio"  "on"
  Option  "HDMI"  "all"
EndSection

Bricked my wubi. 

back to the starting block for me.

Hopefully this will get panned out by the next U release.

---

### Post by rick_ca on 2010-12-08
4 years later...

...just wondering if this problem ("No Sound via HDMI") was ever resolved.

I'm having the same problem: ATI Radeon Xpress 1200 series (RS600), but in Ubuntu 10.10.

Laptop audio works, and Ubuntu sees the device, but audio won't work over HDMI.

---

