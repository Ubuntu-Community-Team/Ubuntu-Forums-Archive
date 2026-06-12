---
title: "Ubuntu 9.10 sound playing through subwoofer, not speakers"
date: 2010-01-18
forum: Multimedia Software
---

### Post by opethfan89 on 2010-01-18
Hi all,

I recently switched to Ubuntu 9.10 from Fedora 12 because it was giving me problems, but now I've run into some problems with Ubuntu. I really only use my computer for internet and music, and I'm not really able to listen to my music.

My computer is an HP Pavillion dv7-3060US laptop, AMD 64bit processor, 4gb ram, ATI Mobility Radeon HD 4530 graphics chip and an ATI chipset (not sure which).

I have an altec lansing speaker configuration, with a built in subwoofer on the bottom. My problem comes that the sound is coming out of the subwoofer, not the actual speakers themself. When I try plugging in an external set of speakers, nothing happens, the sound still plays. Switching the device from "Interal audio analog stereo" to the other choices in my list does nothing (system>preferences>sound is the list im talking about)

I'm able to hear music through my subwoofer when using totem music player, but neither rhythmbox nor amarok play any music. amarok doesn't play at all, and rhythm box shows the music is loaded but no sound comes out and it looks like its playing it at 2x speed.

I've attempted to follow the comprehensive audio problems guide [here]("http://ubuntuforums.org/showthread.php?t=205449") but I get to step 3 and the website isnt the same, so I can't continue.

These are the outputs from the first few steps:

```
aplay -l

root@kadar-laptop:/home/kadar# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
``````

lspci -v

root@kadar-laptop:/home/kadar# lspci -v
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate
    Subsystem: Hewlett-Packard Company Device 3639
    Flags: bus master, 66MHz, medium devsel, latency 0
    Capabilities: [c4] HyperTransport: Slave or Primary Interface
    Capabilities: [54] HyperTransport: UnitID Clumping
    Capabilities: [40] HyperTransport: Retry Mode
    Capabilities: [9c] HyperTransport: #1a
    Capabilities: [f8] HyperTransport: #1c

00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00007000-00007fff
    Memory behind bridge: f2300000-f23fffff
    Prefetchable memory behind bridge: 00000000e0000000-00000000efffffff
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Port (Slot+), MSI 00
    Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
    Capabilities: [b0] Subsystem: Hewlett-Packard Company Device 3639
    Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [100] Vendor Specific Information <?>
    Capabilities: [110] Virtual Channel <?>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=07, sec-latency=0
    I/O behind bridge: 00003000-00006fff
    Memory behind bridge: f1300000-f22fffff
    Prefetchable memory behind bridge: 00000000f0000000-00000000f0ffffff
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Port (Slot+), MSI 00
    Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
    Capabilities: [b0] Subsystem: Hewlett-Packard Company Device 3639
    Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [100] Vendor Specific Information <?>
    Capabilities: [110] Virtual Channel <?>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
    Memory behind bridge: f1200000-f12fffff
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Port (Slot+), MSI 00
    Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
    Capabilities: [b0] Subsystem: Hewlett-Packard Company Device 3639
    Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [100] Vendor Specific Information <?>
    Capabilities: [110] Virtual Channel <?>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=09, subordinate=09, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: f2500000-f25fffff
    Prefetchable memory behind bridge: 00000000f1000000-00000000f10fffff
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Port (Slot+), MSI 00
    Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
    Capabilities: [b0] Subsystem: Hewlett-Packard Company Device 3639
    Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [100] Vendor Specific Information <?>
    Capabilities: [110] Virtual Channel <?>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 5)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=0a, subordinate=0a, sec-latency=0
    Memory behind bridge: f1100000-f11fffff
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Port (Slot+), MSI 00
    Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
    Capabilities: [b0] Subsystem: Hewlett-Packard Company Device 3639
    Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [100] Vendor Specific Information <?>
    Capabilities: [110] Virtual Channel <?>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode] (prog-if 01)
    Subsystem: Hewlett-Packard Company Device 3639
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 22
    I/O ports at 8038 [size=8]
    I/O ports at 804c [size=4]
    I/O ports at 8030 [size=8]
    I/O ports at 8048 [size=4]
    I/O ports at 8010 [size=16]
    Memory at f2408000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [60] Power Management version 2
    Capabilities: [70] SATA HBA <?>
    Kernel driver in use: ahci

00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10)
    Subsystem: Hewlett-Packard Company Device 3639
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
    Memory at f2407000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller (prog-if 10)
    Subsystem: Hewlett-Packard Company Device 3639
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
    Memory at f2406000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20)
    Subsystem: Hewlett-Packard Company Device 3639
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
    Memory at f2408500 (32-bit, non-prefetchable) [size=256]
    Capabilities: [c0] Power Management version 2
    Capabilities: [e4] Debug port: BAR=1 offset=00e0
    Kernel driver in use: ehci_hcd

00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10)
    Subsystem: Hewlett-Packard Company Device 3639
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at f2405000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller (prog-if 10)
    Subsystem: Hewlett-Packard Company Device 3639
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at f2404000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20)
    Subsystem: Hewlett-Packard Company Device 3639
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
    Memory at f2408400 (32-bit, non-prefetchable) [size=256]
    Capabilities: [c0] Power Management version 2
    Capabilities: [e4] Debug port: BAR=1 offset=00e0
    Kernel driver in use: ehci_hcd

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
    Subsystem: Hewlett-Packard Company Device 3639
    Flags: 66MHz, medium devsel
    Capabilities: [b0] HyperTransport: MSI Mapping Enable- Fixed+
    Kernel modules: i2c-piix4

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
    Subsystem: Hewlett-Packard Company Device 3639
    Flags: bus master, slow devsel, latency 64, IRQ 16
    Memory at f2400000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
    Subsystem: Hewlett-Packard Company Device 3639
    Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (prog-if 01)
    Flags: bus master, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=0b, subordinate=0b, sec-latency=64

00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
    Flags: fast devsel
    Capabilities: [80] HyperTransport: Host or Secondary Interface

00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
    Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
    Flags: fast devsel
    Kernel modules: amd64_edac_mod

00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
    Flags: fast devsel
    Capabilities: [f0] Secure device <?>

00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
    Flags: fast devsel

01:00.0 VGA compatible controller: ATI Technologies Inc M92 [Mobility Radeon HD 4500 Series]
    Subsystem: Hewlett-Packard Company Device 3639
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at e0000000 (32-bit, prefetchable) [size=256M]
    I/O ports at 7000 [size=256]
    Memory at f2300000 (32-bit, non-prefetchable) [size=64K]
    Expansion ROM at f2320000 [disabled] [size=128K]
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Legacy Endpoint, MSI 00
    Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
    Capabilities: [100] Vendor Specific Information <?>
    Kernel modules: radeon

01:00.1 Audio device: ATI Technologies Inc R700 Audio Device [Radeon HD 4000 Series]
    Subsystem: Hewlett-Packard Company Device 3639
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at f2310000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Legacy Endpoint, MSI 00
    Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
    Capabilities: [100] Vendor Specific Information <?>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

08:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
    Subsystem: Hewlett-Packard Company Device 3041
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at f1200000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: [40] Power Management version 2
    Capabilities: [50] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
    Capabilities: [60] Express Legacy Endpoint, MSI 00
    Capabilities: [90] MSI-X: Enable- Mask- TabSize=1
    Capabilities: [100] Advanced Error Reporting <?>
    Capabilities: [140] Virtual Channel <?>
    Capabilities: [160] Device Serial Number 00-00-00-00-00-00-00-00
    Kernel driver in use: ath9k
    Kernel modules: ath9k

09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
    Subsystem: Hewlett-Packard Company Device 3639
    Flags: bus master, fast devsel, latency 0, IRQ 30
    I/O ports at 2000 [size=256]
    Memory at f1004000 (64-bit, prefetchable) [size=4K]
    Memory at f1000000 (64-bit, prefetchable) [size=16K]
    Expansion ROM at f1010000 [disabled] [size=64K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
    Capabilities: [70] Express Endpoint, MSI 01
    Capabilities: [ac] MSI-X: Enable- Mask- TabSize=4
    Capabilities: [cc] Vital Product Data <?>
    Capabilities: [100] Advanced Error Reporting <?>
    Capabilities: [140] Virtual Channel <?>
    Capabilities: [160] Device Serial Number 00-00-00-00-00-00-00-00
    Kernel driver in use: r8169
    Kernel modules: r8169

```And then I try to do the next step but the website doesn't work.

Any advice is greatly appreciated, as I'm eager to switch over to Ubuntu full time, but I NEED my music to be able to do that.

Thanks in advance for any advice

Opethfan89

---

### Post by opethfan89 on 2010-01-23
*BUMP* Still waiting for a reply! I want to get this problem fixed so I can really start using Ubuntu full time, any help is appreciated!

---

### Post by ReedAndrew on 2010-02-19
I have been having the same problem I have an HP Pavilion dv6 laptop.  I have sound working but not in Rythmbox and the movie player same issue with it playing at 2x speed.  I downloaded VLC and the audio plays fine through there.  I would much rather use rythmbox to listen to my music as it is cleaner.  I will keep looking for a way to fix this and I'll post up what I find here for you. Here is a link to the form that I made

[http://ubuntuforums.org/showthread.php?p=8849433#post8849433](http://ubuntuforums.org/showthread.php?p=8849433#post8849433)

I solved the issue with mine try unistalling pulseaudio that did the trick for me 
sudo apt-get remove pulseaudio

---

### Post by Sudo Su on 2010-04-05
I too have the same issue, with dv7 series laptop on 9.10 and also the 10.04 beta, also  when shutting down get strange sound noises, also bad gfx glitches when logging off or suspending.

Oh and hey all I'm new here Finally giving Ubuntu a proper go :guitar:

---

### Post by duke.tim on 2010-04-06
[https://help.ubuntu.com/community/SoundTroubleshooting#Having%20sound%20issues%20with%20HP%20dvx%20laptop](https://help.ubuntu.com/community/SoundTroubleshooting#Having%20sound%20issues%20with%20HP%20dvx%20laptop)

This should help I have a dv6 and this has solved a problem similar to this. you also might want to check the alsamixer settings
```
alsamixer
```
to exit press "ctrl c"

---

### Post by lidex on 2010-04-06
Try this. Open a terminal ("Applications>Accessories>Terminal") and input this command:
```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```
Add these lines at the bottom:
```
options snd-hda-intel enable_msi=1
options snd-hda-intel model=hp-dv5

```
Save. Close. Reboot. Check mixer levels (terminal):
```
alsamixer
```

---

### Post by lidex on 2010-04-06
For Amarok, in a terminal:
```
sudo apt-get install phonon-backend-xine libxine1-ffmpeg
```

Sounds like you may have a gstreamer issue. Have a look here:
[http://ubuntuforums.org/showthread.php?t=766683]("http://ubuntuforums.org/showthread.php?t=766683")

---

### Post by opethfan89 on 2010-04-27
I didn't even notice that I had new replies on this thread, thank you everyone.

I want to state that I _did_ eventually fix the issue, by following instructions [here]("http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1381413"), and I made a text file with a few addendum instructions for my own clarification.

Thank you to everyone who posted,
Opethfan89

---

