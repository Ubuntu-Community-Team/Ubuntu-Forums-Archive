---
title: "dvb tuner card"
date: 2006-08-10
forum: Multimedia &amp; Video
---

### Post by madsporkmurderer on 2006-08-10
I have a yuan stratford pg300 pci dvb card, it is based around the Conexant CX23880/1/2/3 chipset (relivent lspci sections are:

0000:02:08.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
0000:02:08.2 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
0000:02:08.4 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [IR Port] (rev 05))

which I believe is the same as the Hauppauge Nova-T DVB-T. In a guide I read that it should be automatically detected and to look in /var/log/dmesg for conformation. The relevent part of my /var/log/dmesg reads:

[17179616.172000] Linux video capture interface: v1.00
[17179616.228000] cx2388x dvb driver version 0.0.5 loaded
[17179616.228000] cx88[0]: Your board isn't known (yet) to the driver.  You can
[17179616.228000] cx88[0]: try to pick one of the existing card configs via
[17179616.228000] cx88[0]: card=<n> insmod option.  Updating to the latest
[17179616.228000] cx88[0]: version might help as well.
[17179616.228000] cx88[0]: Here is a list of valid choices for the card=<n> insmod option:
[17179616.228000] cx88[0]:    card=0 -> UNKNOWN/GENERIC
[17179616.228000] cx88[0]:    card=1 -> Hauppauge WinTV 34xxx models
[17179616.228000] cx88[0]:    card=2 -> GDI Black Gold
[17179616.228000] cx88[0]:    card=3 -> PixelView
[17179616.228000] cx88[0]:    card=4 -> ATI TV Wonder Pro
[17179616.228000] cx88[0]:    card=5 -> Leadtek Winfast 2000XP Expert
[17179616.228000] cx88[0]:    card=6 -> AverTV Studio 303 (M126)
[17179616.228000] cx88[0]:    card=7 -> MSI TV-@nywhere Master
[17179616.228000] cx88[0]:    card=8 -> Leadtek Winfast DV2000
[17179616.228000] cx88[0]:    card=9 -> Leadtek PVR 2000
[17179616.228000] cx88[0]:    card=10 -> IODATA GV-VCP3/PCI
[17179616.228000] cx88[0]:    card=11 -> Prolink PlayTV PVR
[17179616.228000] cx88[0]:    card=12 -> ASUS PVR-416
[17179616.228000] cx88[0]:    card=13 -> MSI TV-@nywhere
[17179616.228000] cx88[0]:    card=14 -> KWorld/VStream XPert DVB-T
[17179616.228000] cx88[0]:    card=15 -> DViCO FusionHDTV DVB-T1
[17179616.228000] cx88[0]:    card=16 -> KWorld LTV883RF
[17179616.228000] cx88[0]:    card=17 -> DViCO FusionHDTV 3 Gold-Q
[17179616.228000] cx88[0]:    card=18 -> Hauppauge Nova-T DVB-T
[17179616.228000] cx88[0]:    card=19 -> Conexant DVB-T reference design
[17179616.228000] cx88[0]:    card=20 -> Provideo PV259
[17179616.228000] cx88[0]:    card=21 -> DViCO FusionHDTV DVB-T Plus
[17179616.228000] cx88[0]:    card=22 -> pcHDTV HD3000 HDTV
[17179616.228000] cx88[0]:    card=23 -> digitalnow DNTV Live! DVB-T
[17179616.228000] cx88[0]:    card=24 -> Hauppauge WinTV 28xxx (Roslyn) models
[17179616.228000] cx88[0]:    card=25 -> Digital-Logic MICROSPACE Entertainment Center (MEC)
[17179616.228000] cx88[0]:    card=26 -> IODATA GV/BCTV7E
[17179616.228000] cx88[0]:    card=27 -> PixelView PlayTV Ultra Pro (Stereo)
[17179616.228000] cx88[0]:    card=28 -> DViCO FusionHDTV 3 Gold-T
[17179616.228000] cx88[0]:    card=29 -> ADS Tech Instant TV DVB-T PCI
[17179616.228000] cx88[0]:    card=30 -> TerraTec Cinergy 1400 DVB-T
[17179616.228000] cx88[0]:    card=31 -> DViCO FusionHDTV 5 Gold
[17179616.228000] cx88[0]:    card=32 -> AverMedia UltraTV Media Center PCI 550
[17179616.228000] cx88[0]:    card=33 -> Kworld V-Stream Xpert DVD
[17179616.228000] cx88[0]:    card=34 -> ATI HDTV Wonder
[17179616.228000] cx88[0]:    card=35 -> WinFast DTV1000-T
[17179616.228000] cx88[0]:    card=36 -> AVerTV 303 (M126)
[17179616.228000] CORE cx88[0]: subsystem: 12ab:2300, board: UNKNOWN/GENERIC [card=0,autodetected]
[17179616.228000] TV tuner -1 at 0x1fe, Radio tuner -1 at 0x1fe
[17179616.492000] cx2388x v4l2 driver version 0.0.5 loaded
[17179616.492000] ACPI: PCI Interrupt 0000:02:08.0[A] -> GSI 16 (level, low) -> IRQ 193
[17179616.492000] cx88[0]: Your board isn't known (yet) to the driver.  You can
[17179616.492000] cx88[0]: try to pick one of the existing card configs via
[17179616.492000] cx88[0]: card=<n> insmod option.  Updating to the latest
[17179616.492000] cx88[0]: version might help as well.
[17179616.492000] cx88[0]: Here is a list of valid choices for the card=<n> insmod option:
[17179616.492000] cx88[0]:    card=0 -> UNKNOWN/GENERIC
[17179616.492000] cx88[0]:    card=1 -> Hauppauge WinTV 34xxx models
[17179616.492000] cx88[0]:    card=2 -> GDI Black Gold
[17179616.492000] cx88[0]:    card=3 -> PixelView
[17179616.492000] cx88[0]:    card=4 -> ATI TV Wonder Pro
[17179616.492000] cx88[0]:    card=5 -> Leadtek Winfast 2000XP Expert
[17179616.492000] cx88[0]:    card=6 -> AverTV Studio 303 (M126)
[17179616.492000] cx88[0]:    card=7 -> MSI TV-@nywhere Master
[17179616.492000] cx88[0]:    card=8 -> Leadtek Winfast DV2000
[17179616.492000] cx88[0]:    card=9 -> Leadtek PVR 2000
[17179616.492000] cx88[0]:    card=10 -> IODATA GV-VCP3/PCI
[17179616.492000] cx88[0]:    card=11 -> Prolink PlayTV PVR
[17179616.492000] cx88[0]:    card=12 -> ASUS PVR-416
[17179616.492000] cx88[0]:    card=13 -> MSI TV-@nywhere
[17179616.492000] cx88[0]:    card=14 -> KWorld/VStream XPert DVB-T
[17179616.492000] cx88[0]:    card=15 -> DViCO FusionHDTV DVB-T1
[17179616.492000] cx88[0]:    card=16 -> KWorld LTV883RF
[17179616.492000] cx88[0]:    card=17 -> DViCO FusionHDTV 3 Gold-Q
[17179616.492000] cx88[0]:    card=18 -> Hauppauge Nova-T DVB-T
[17179616.492000] cx88[0]:    card=19 -> Conexant DVB-T reference design
[17179616.492000] cx88[0]:    card=20 -> Provideo PV259
[17179616.492000] cx88[0]:    card=21 -> DViCO FusionHDTV DVB-T Plus
[17179616.492000] cx88[0]:    card=22 -> pcHDTV HD3000 HDTV
[17179616.492000] cx88[0]:    card=23 -> digitalnow DNTV Live! DVB-T
[17179616.492000] cx88[0]:    card=24 -> Hauppauge WinTV 28xxx (Roslyn) models
[17179616.492000] cx88[0]:    card=25 -> Digital-Logic MICROSPACE Entertainment Center (MEC)
[17179616.492000] cx88[0]:    card=26 -> IODATA GV/BCTV7E
[17179616.492000] cx88[0]:    card=27 -> PixelView PlayTV Ultra Pro (Stereo)
[17179616.492000] cx88[0]:    card=28 -> DViCO FusionHDTV 3 Gold-T
[17179616.492000] cx88[0]:    card=29 -> ADS Tech Instant TV DVB-T PCI
[17179616.492000] cx88[0]:    card=30 -> TerraTec Cinergy 1400 DVB-T
[17179616.492000] cx88[0]:    card=31 -> DViCO FusionHDTV 5 Gold
[17179616.492000] cx88[0]:    card=32 -> AverMedia UltraTV Media Center PCI 550
[17179616.492000] cx88[0]:    card=33 -> Kworld V-Stream Xpert DVD
[17179616.492000] cx88[0]:    card=34 -> ATI HDTV Wonder
[17179616.492000] cx88[0]:    card=35 -> WinFast DTV1000-T
[17179616.492000] cx88[0]:    card=36 -> AVerTV 303 (M126)
[17179616.492000] CORE cx88[0]: subsystem: 12ab:2300, board: UNKNOWN/GENERIC [card=0,autodetected]
[17179616.492000] TV tuner -1 at 0x1fe, Radio tuner -1 at 0x1fe
[17179616.712000] cx88[0]/0: found at 0000:02:08.0, rev: 5, irq: 193, latency: 66, mmio: 0xdc000000
[17179616.904000] tuner 0-0060: All bytes are equal. It is not a TEA5767
[17179616.904000] tuner 0-0060: chip found @ 0xc0 (cx88[0])
[17179616.940000] cx88[0]/0: registered device video0 [v4l2]
[17179616.940000] cx88[0]/0: registered device vbi0
[17179616.940000] tuner 0-0060: tuner type not set
[17179616.944000] cx2388x blackbird driver version 0.0.5 loaded

what command do I use to tell it which card I have?

---

### Post by Jussi Kukkonen on 2006-08-10
Well, your card is not on the list, so... I'd try with newer versions of the drivers and then ask at dvb mailing list (both found at linuxtv.org).

When you know what number you have to choose, or want to experiment, you'll have to add a line like 
```
options cx88xx card=19

```(where 19 is the card number) into /etc/modprobe.conf. After that the module will be loaded with correct parameter (on boot or with *modprobe cx88xx*).

---

### Post by madsporkmurderer on 2006-09-29
That number didn't work. I have found a few suggestions on other sites of numbers to use but in using that one I appear to have changed a setting somewhere in such a way as I am now unable to get back to an undecided state.

Is there a way of getting back to where I was with the options open?

---

### Post by Kadin2048 on 2006-09-29
The default setting is 0, or UNKNOWN/GENERIC. It's at the top of the list, and it's what the driver defaults to if it doesn't recognize your card.

Maybe you want to try a CVS version of the driver?

---

### Post by pseudonym on 2006-09-29
Or, after finding out from linuxtv.org which kernel has native support for your card, download the source from kernel.org and build a custom kernel. A good Ubuntu howto for that can be found [here]("http://www.ubuntuforums.org/showthread.php?t=217657&highlight=kernel+2.6.17").

---

### Post by madsporkmurderer on 2006-09-30
The problem is that as much as I tell it that I want to use different card numbers, it doesnt change what is in the dmesg file of which the relivent part is: 

[17179618.964000] Linux video capture interface: v1.00
[17179619.004000] Real Time Clock Driver v1.12
[17179619.116000] ts: Compaq touchscreen protocol output
[17179619.156000] FDC 0 is a post-1991 82077
[17179619.804000] input: PC Speaker as /class/input/input2
[17179619.928000] parport: PnPBIOS parport detected.
[17179619.928000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[17179620.104000] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[17179620.148000] cx2388x v4l2 driver version 0.0.5 loaded
[17179620.148000] ACPI: PCI Interrupt 0000:02:08.0[A] -> GSI 16 (level, low) -> IRQ 185
[17179620.148000] CORE cx88[0]: subsystem: 12ab:2300, board: Hauppauge Nova-T DVB-T [card=18,insmod option]
[17179620.148000] TV tuner 4 at 0x1fe, Radio tuner -1 at 0x1fe
[17179620.176000] Initializing USB Mass Storage driver...
[17179620.176000] scsi1 : SCSI emulation for USB Mass Storage devices
[17179620.176000] usb-storage: device found at 3
[17179620.176000] usb-storage: waiting for device to settle before scanning
[17179620.176000] usbcore: registered new driver usb-storage
[17179620.176000] USB Mass Storage support registered.
[17179620.356000] cx2388x dvb driver version 0.0.5 loaded
[17179620.376000] tveeprom 0-0050: Encountered bad packet header [14]. Corrupt or not a Hauppauge eeprom.
[17179620.376000] cx88[0]: warning: unknown hauppauge model #0
[17179620.376000] cx88[0]: hauppauge eeprom: model=0
[17179620.376000] input: cx88 IR (Hauppauge Nova-T DVB-T as /class/input/input3
[17179620.376000] cx88[0]/0: found at 0000:02:08.0, rev: 5, irq: 185, latency: 66, mmio: 0xdc000000
[17179620.436000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 193
[17179620.436000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[17179620.752000] intel8x0_measure_ac97_clock: measured 54900 usecs
[17179620.752000] intel8x0: clocking to 48000
[17179621.204000] NET: Registered protocol family 17
[17179621.204000] cx88[0]/0: registered device video0 [v4l2]
[17179621.204000] cx88[0]/0: registered device vbi0
[17179621.212000] ACPI: PCI Interrupt 0000:02:08.2[A] -> GSI 16 (level, low) -> IRQ 185
[17179621.212000] cx88[0]/2: found at 0000:02:08.2, rev: 5, irq: 185, latency: 66, mmio: 0xdd000000
[17179621.212000] cx88[0]/2: cx2388x based dvb card
[17179621.212000] DVB: registering new adapter (cx88[0]).
[17179621.212000] DVB: registering frontend 0 (Conexant CX22702 DVB-T)...
[17179621.260000] cx2388x blackbird driver version 0.0.5 loaded

---

### Post by madsporkmurderer on 2006-10-01
Ive got around that problem now, but the issue seems to be that my kernel doesn't support option 43, which worked for someone else. The newest kernel in the repositaries is 2.6.15-27 while they are using "2.6.16 "gentoo-sources-r9" kernel" is there a way for me to get a later kernel version

---

