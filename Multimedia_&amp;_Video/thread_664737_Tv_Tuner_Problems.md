---
title: "Tv Tuner Problems"
date: 2008-01-11
forum: Multimedia &amp; Video
---

### Post by kempy1000 on 2008-01-11
Hello

I have searched the web for an answer but everything i try proves not to work.
Basically i am trying to set up my Kworld 7134 tv card (Chipset phillips saa7134) however it will not find any channels. 

I have tried modprobe saa7134 card=xx tuner=yy with a few different parameters (not saying i used the correct ones)

--

Here is  /etc/modprobe.d/options

# Enable double-buffering so gstreamer et. al. work
options quickcam compatible=2

# Default hostap to managed mode
options hostap_pci iw_mode=2
options hostap_cs iw_mode=2

options saa7134 card=59 tuner=56

-- And the output from dmesg

[   34.029469] Linux agpgart interface v0.102 (c) Dave Jones
[   34.088115] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   34.127300] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   34.161184] irda_init()
[   34.161218] NET: Registered protocol family 23
[   34.194802] agpgart: Detected VIA KT400/KT400A/KT600 chipset
[   34.199466] agpgart: AGP aperture is 64M @ 0xe0000000
[   34.283739] Linux video capture interface: v2.00
[   34.788540] saa7130/34: v4l2 driver version 0.2.14 loaded
[   34.789001] ACPI: PCI Interrupt 0000:00:0b.0[A] -> GSI 19 (level, low) -> IRQ 18
[   34.789013] saa7134[0]: found at 0000:00:0b.0, rev: 1, irq: 18, latency: 32, mmio: 0xdffffc00
[   34.789021] saa7134[0]: subsystem: 1131:0000, board: Philips Tiger reference design [card=81,insmod option]
[   34.789032] saa7134[0]: board init: gpio is 407f
[   34.892531] saa7134[0]: Huh, no eeprom present (err=-5)?
[   35.127477] tuner 0-0060: All bytes are equal. It is not a TEA5767
[   35.127486] tuner 0-0060: chip found @ 0xc0 (saa7134[0])
[   35.127549] tuner 0-0060: type set to 59 (Ymec TVision TVF-5533MF)
[   35.127554] tuner 0-0060: type set to 59 (Ymec TVision TVF-5533MF)
[   35.195628] saa7134[0]: registered device video0 [v4l2]
[   35.195679] saa7134[0]: registered device vbi0
[   35.195718] saa7134[0]: registered device radio0
[   35.414651] saa7134 ALSA driver for DMA sound loaded
[   35.414697] saa7134[0]/alsa: saa7134[0] at 0xdffffc00 irq 18 registered as card -2
[   35.572777] saa7134[0]/dvb: frontend initialization failed
[   35.755132] input: ImPS/2 Generic Wheel Mouse as /class/input/input2
[   35.757723] parport_pc 00:03: reported by Plug and Play ACPI
[   35.757833] parport0: PC-style at 0x378 (0x778), irq 7, dma 0 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   35.758979] input: PC Speaker as /class/input/input3
[   35.800172] ACPI: PCI Interrupt 0000:00:11.5[C] -> GSI 22 (level, low) -> IRQ 19
[   35.800324] PCI: Setting latency timer of device 0000:00:11.5 to 64
[   37.177769] lp0: using parport0 (interrupt-driven).
[   37.217555] w83627hf: Found W83697HF chip at 0x290
[   37.293843] Adding 746980k swap on /dev/hda5.  Priority:-1 extents:1 across:746980k
[   37.611429] EXT3 FS on hda1, internal journal
[   39.274653] No dock devices found.
[   39.471336] input: Power Button (FF) as /class/input/input4


Thanks
 Chris.

---

