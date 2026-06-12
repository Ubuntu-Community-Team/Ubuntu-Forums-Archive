---
title: "web cam and tv card trading places"
date: 2007-01-03
forum: Multimedia &amp; Video
---

### Post by mrpixels0 on 2007-01-03
hello i do not know if this is happing to anyone else but i got a USB cam a Pixart brand aka Ezonics and it works great but now the tv card wants to be where my messengers web cam should be and my web cam wants to be where my tv card should be.

I downloaded and followed all of the intructions for the modified version of the spca5xx driver and all went without a hitch.

here is my dmesg output:

```

17179588.020000] usbcore: registered new driver usbhid
[17179588.020000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179588.044000] Linux video capture interface: v1.00
[17179588.064000] /usr/src/spca5xx-20060501/drivers/usb/spca5xx.c: USB SPCA5XX camera found. Pixart PAC207BCA
[17179588.064000] /usr/src/spca5xx-20060501/drivers/usb/spca5xx.c: [spca5xx_probe:5480] Camera type GBRG
[17179588.076000] /usr/src/spca5xx-20060501/drivers/usb/spca5xx.c: [spca5xx_getcapability:1765] maxw 352 maxh 288 minw 160 minh 120
[17179588.076000] usbcore: registered new driver spca5xx
[17179588.076000] /usr/src/spca5xx-20060501/drivers/usb/spca5xx.c: spca5xx driver 00.60.00 registered
[17179588.220000] Linux agpgart interface v0.101 (c) Dave Jones
[17179588.276000] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 22
[17179588.276000] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [APCJ] -> GSI 22 (level, low) -> IRQ 225
[17179588.276000] PCI: Setting latency timer of device 0000:00:04.0 to 64
[17179588.344000] ts: Compaq touchscreen protocol output
[17179588.372000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17179588.436000] nvidia: module license 'NVIDIA' taints kernel.
[17179588.440000] saa7130/34: v4l2 driver version 0.2.14 loaded
[17179588.596000] intel8x0_measure_ac97_clock: measured 54707 usecs
[17179588.596000] intel8x0: clocking to 46892
[17179588.620000] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[17179588.620000] ACPI: PCI Interrupt 0000:05:00.0[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 58
[17179588.620000] PCI: Setting latency timer of device 0000:05:00.0 to 64
[17179588.620000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8776  Mon Oct 16 21:56:04 PDT 2006
[17179588.868000] ACPI: PCI Interrupt 0000:01:08.0[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 58
[17179588.868000] saa7130[0]: found at 0000:01:08.0, rev: 1, irq: 58, latency: 15, mmio: 0xfdeff000
[17179588.868000] PCI: Setting latency timer of device 0000:01:08.0 to 64
[17179588.868000] saa7130[0]: subsystem: 1131:0000, board: LifeView FlyVIDEO3000 [card=2,insmod option]
[17179588.868000] saa7130[0]: board init: gpio is 3f000
[17179588.868000] saa7130[0]: there are different flyvideo cards with different tuners
[17179588.868000] saa7130[0]: out there, you might have to use the tuner=<nr> insmod
[17179588.868000] saa7130[0]: option to override the default value.
[17179588.872000] input: saa7134 IR (LifeView FlyVIDEO30 as /class/input/input3
[17179588.976000] saa7130[0]: Huh, no eeprom present (err=-5)?
[17179588.996000] tuner 2-0061: chip found @ 0xc2 (saa7130[0])
[17179588.996000] tuner 2-0061: type set to 17 (Philips NTSC_M (MK2))
[17179588.996000] saa7130[0]: registered device video1 [v4l2]
[17179588.996000] saa7130[0]: registered device vbi0
[17179588.996000] saa7130[0]: registered device radio0
[17179589.028000] saa7134 ALSA driver for DMA sound loaded
[17179589.028000] saa7130[0]/alsa: saa7130[0] at 0xfdeff000 irq 58 registered as card -1
[17179589.292000] NET: Registered protocol family 17
[17179589.308000] lp0: using parport0 (interrupt-driven).
[17179589.340000] Adding 1502036k swap on /dev/disk/by-uuid/537c8a1b-95fc-4e22-98d2-4d09941ab81a.  Priority:-1 extents:1 across:1502036k
[17179589.408000] EXT3 FS on sda1, internal journal
[17179595.324000] ACPI: Power Button (FF) [PWRF]
[17179595.324000] ACPI: Power Button (CM) [PWRB]
[17179595.456000] ibm_acpi: ec object not found
[17179595.492000] pcc_acpi: loading...
[17179595.820000] powernow-k8: Found 1 AMD Athlon 64 / Opteron processors (version 1.60.2)
[17179595.824000] powernow-k8: BIOS error - no PSB or ACPI _PSS objects
[17179597.356000] NET: Registered protocol family 10
[17179597.360000] lo: Disabled Privacy Extensions
[17179597.360000] IPv6 over IPv4 tunneling driver
[17179598.316000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[17179598.316000] apm: overridden by ACPI.
[17179607.936000] Bluetooth: Core ver 2.8
[17179607.936000] NET: Registered protocol family 31
[17179607.936000] Bluetooth: HCI device and connection manager initialized
[17179607.936000] Bluetooth: HCI socket layer initialized
[17179607.948000] Bluetooth: L2CAP ver 2.8
[17179607.948000] Bluetooth: L2CAP socket layer initialized
[17179607.976000] Bluetooth: RFCOMM socket layer initialized
[17179607.976000] Bluetooth: RFCOMM TTY layer initialized
[17179607.976000] Bluetooth: RFCOMM ver 1.7
[17179608.220000] eth0: no IPv6 routers present

```

this is my tvcard settings in /etc/modprobe.d/saa7134:
```

alias char-major-81 videodev0
alias char-major-81-0 saa7134
options saa7134 card=2 tuner=17 oss=1

```

and these are my settings in /etc/modprobe.d/spca5xx
```

alias char-major-81 videodev1
alias char-major-81-0 spca5xx
options spca5xx GRed=217 GBlue=300 GGreen=224 gamma=4

```

I imagine it is somthing simple i am over looking there has to be a way to make sure they are where they are supposed to be at all times and i am just not seeing it, 

if anyone could help me out i would be really greatful to you, thanks in advance for taking time to read this and help me out.

MP0

---

