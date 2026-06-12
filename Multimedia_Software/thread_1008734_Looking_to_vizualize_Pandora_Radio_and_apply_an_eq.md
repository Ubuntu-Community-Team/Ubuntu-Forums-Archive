---
title: "Looking to vizualize Pandora Radio and apply an equalizer"
date: 2008-12-11
forum: Multimedia Software
---

### Post by gbear14275 on 2008-12-11
Hello,

This is my first post on the ubuntu forums and so I apologize ahead of time for mistakes, cultural or otherwise.

Problem:  I have been unable to find a simple equalizer which will adjust my Pandora internet radio output to my headphones. I would prefer if this eq could also do real-time visualization so that I can see the effects of eq adjustments, but this is not necessary.

Some limited configuration info... ask for more and I will be happy to provide... granted you provide a pointer or instructions on gathering it.  Much of this I hand copied off drop down menu's (not fun).

lspci:
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:19.0 Ethernet controller: Intel Corporation 82566MM Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HBM (ICH8M-E) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation Quadro NVS 140M (rev a1)
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
15:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
15:00.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)
15:00.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)
15:00.3 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev ff)
15:00.4 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 11)
15:00.5 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 11)

@:/proc/asound# cat devices
  2:        : timer
  3:        : sequencer
  4: [ 0- 1]: digital audio playback
  5: [ 0- 0]: digital audio playback
  6: [ 0- 0]: digital audio capture
  7: [ 0]   : control
@:/proc/asound# cat version
Advanced Linux Sound Architecture Driver Version 1.0.17.
@:/proc/asound# cat modules
 0 snd_hda_intel
@:/proc/asound# cat cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfe220000 irq 17
@:/proc/asound# cat pcm
00-01: AD198x Digital : AD198x Digital : playback 1
00-00: AD198x Analog : AD198x Analog : playback 1 : capture 2
@:/proc/asound# cat timers
G0: system timer : 4000.000us (10000000 ticks)
P0-0-0: PCM playback 0-0-0 : SLAVE
P0-0-1: PCM capture 0-0-1 : SLAVE
P0-0-3: PCM capture 0-0-3 : SLAVE
P0-1-0: PCM playback 0-1-0 : SLAVE

/proc/asound/oss# cat sndstat
Sound Driver:3.8.1a-980706 (ALSA v1.0.17 emulation code)
Kernel: Linux Mustache 2.6.27-9-generic #1 SMP Thu Nov 20 22:15:32 UTC 2008 x86_64
Config options: 0

Installed drivers: 
Type 10: ALSA emulation

Card config: 
HDA Intel at 0xfe220000 irq 17

Audio devices:
0: AD198x Analog (DUPLEX)

Synth devices: NOT ENABLED IN CONFIG

Midi devices: NOT ENABLED IN CONFIG

Timers:
31: system timer

Mixers:
0: Analog Devices AD1984


and there are huge outputs from the codec#0... but... i'll let someone ask before I post them.

Any help in the form of package recommendations or anything would be great.  I've tried playing around with JAMin and jack control but both seem to keep pandora from playing correctly or cause firefox to freeze.

Thank you for your time.

---

### Post by loboc on 2008-12-11
google pulse audio equalizer

---

