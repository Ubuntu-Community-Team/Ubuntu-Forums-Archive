---
title: "Lirc USB hama Irda"
date: 2010-07-15
forum: Multimedia Software
---

### Post by redman5087 on 2010-07-15
Hello,

It's the first time I'm going to use a remote, I just installed XBMC Live on a htpc.
I bought a HAMA usb irda device an I have Philips sru 5150 universal remote control device.

dmesg gives the following result:

[    8.650460] irda_init()
[    8.650490] NET: Registered protocol family 23
[    8.712391] ACPI: PCI Interrupt Link [LPMU] enabled at IRQ 20
[    8.712404] nvidia 0000:00:03.5: PCI INT B -> Link[LPMU] -> GSI 20 (level, low) -> IRQ 20
[    8.713351] ACPI: PCI Interrupt Link [SGRU] enabled at IRQ 23
[    8.713364] nvidia 0000:03:00.0: PCI INT A -> Link[SGRU] -> GSI 23 (level, low) -> IRQ 23
[    8.713381] nvidia 0000:03:00.0: setting latency timer to 64
[    8.714266] NVRM: loading NVIDIA UNIX x86 Kernel Module  190.53  Tue Dec  8 18:51:41 PST 2009
[    8.736678] lp: driver loaded but no devices found
[    8.772133] cfg80211: Calling CRDA to update world regulatory domain
[    8.914714] SigmaTel STIr4200 IRDA/USB found at address 2, Vendor: 66f, Product: 4200
[    8.916392] stir4200 4-2:1.0: IrDA: Registered SigmaTel device irda0
[    8.916485] usbcore: registered new interface driver stir4200
[    9.934094] ACPI: PCI Interrupt Link [LN3A] enabled at IRQ 19
[    9.934107]   alloc irq_desc for 19 on node -1
[    9.934113]   alloc kstat_irqs on node -1
[    9.934128] ath9k 0000:04:00.0: PCI INT A -> Link[LN3A] -> GSI 19 (level, low) -> IRQ 19
[    9.934144] ath9k 0000:04:00.0: setting latency timer to 64
[    9.983389] ath: EEPROM regdomain: 0x60
[    9.983398] ath: EEPROM indicates we should expect a direct regpair map
[    9.983409] ath: Country alpha2 being used: 00
[    9.983415] ath: Regpair used: 0x60
[   10.243572] HDA Intel 0000:00:08.0: power state changed by ACPI to D0
[   10.244704] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 22
[   10.244718] HDA Intel 0000:00:08.0: PCI INT A -> Link[LAZA] -> GSI 22 (level, low) -> IRQ 22
[   10.244787] HDA Intel 0000:00:08.0: setting latency timer to 64
[   10.301571] phy0: Selected rate control algorithm 'ath9k_rate_control'
[   10.303280] Registered led device: ath9k-phy0::radio
[   10.303319] Registered led device: ath9k-phy0::assoc
[   10.303357] Registered led device: ath9k-phy0::tx
[   10.303394] Registered led device: ath9k-phy0::rx
[   10.303437] phy0: Atheros AR9285 MAC/BB Rev:2 AR5133 RF Rev:e0: mem=0xf9a20000, irq=19
[   10.868028] hda_codec: Unknown model for ALC662 rev1, trying auto-probe from BIOS...
[   11.100184] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:08.0/input/input5
[   13.515727] lirc_dev: IR Remote Control driver registered, major 61 
[   13.575118] lirc_mceusb: Windows Media Center Edition USB IR Transceiver driver for LIRC 1.90
[   13.575127] lirc_mceusb: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>, Dan Conti <dconti@acm.wwu.edu>
[   13.575188] usbcore: registered new interface driver lirc_mceusb


So, I presume that the driver is loaded now.

But I don't know how to get further!

This is my hardware.conf:

# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Windows Media Center Remotes (new version Philips et al.)"
REMOTE_MODULES="lirc_dev lirc_mceusb2"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_LIRCD_CONF="mceusb/lircd.conf.mceusb"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="Hama"
TRANSMITTER_MODULES="lirc_dev lirc_mceusb"
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE="/dev/lirc1"
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD="true"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"

#Try to load appropriate kernel modules
LOAD_MODULES="true"

# Default configuration files for your hardware if any
LIRCMD_CONF=""

#Forcing noninteractive reconfiguration
#If lirc is to be reconfigured by an external application
#that doesn't have a debconf frontend available, the noninteractive
#frontend can be invoked and set to parse REMOTE and TRANSMITTER
#It will then populate all other variables without any user input
#If you would like to configure lirc via standard methods, be sure
#to leave this set to "false"
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
START_LIRCMD=""

irrecord doesn't seem to work.

irrecord new-lircd.conf

irrecord -  application for recording IR-codes for usage with lirc

Copyright (C) 1998,1999 Christoph Bartelmus(lirc@bartelmus.de)

irrecord: could not get file information for /dev/lirc
irrecord: default_init(): No such file or directory
irrecord: could not init hardware (lircd running ? --> close it, check permissions)

could someone point me in the right direction?

I would really appreciate.

Thanks

---

