---
title: "bad configuration of /dev/video*"
date: 2006-07-25
forum: Multimedia &amp; Video
---

### Post by cymcy on 2006-07-25
hello.

I've a problem with a tv tuner and a usb webcam.
At a boot, tv tuner is registered under /dev/video0 and webcam under /dev/video1. At another boot,tv tuner is registered under /dev/video1 and webcam under /dev/video0 . It seems to be randomly registered. 

but my application (tvtime, webcam tools) are configured in hard (config files refers to /dev/video0 or to /dev/video symlink to /dev/video0)

so I've to change my configuration files randomly at each reboot.

here is a part of my dmesg :

[17179576.968000] usb 2-2: new full speed USB device using ohci_hcd and address
2
[17179587.384000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179587.412000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179587.740000] i2c-sis96x version 1.0.0
[17179587.740000] sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0x0c00
[17179588.028000] Linux agpgart interface v0.101 (c) Dave Jones
[...  pci network card ...]
[17179588.124000] Linux video capture interface: v1.00
[17179588.176000] bttv: driver version 0.9.16 loaded
[17179588.176000] bttv: using 8 buffers with 2080k (520 pages) each for capture
[17179588.176000] bttv: Bt8xx card found (0).
[17179588.176000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> GSI 19 (level, low) ->
IRQ 193
[17179588.176000] bttv0: Bt878 (rev 2) at 0000:00:0b.0, irq: 193, latency: 32, mmio: 0xcfcfe000
[17179588.176000] bttv0: detected: (Askey Magic/others) TView99 CPH06x [card=38], PCI subsystem ID is 144f:3000
[17179588.176000] bttv0: using: Askey CPH06X TView99 [card=38,insmod option]
[17179588.176000] bttv0: gpio: en=00000000, out=00000000 in=00ffeff7 [init]
[17179588.176000] bttv0: using tuner=3
[17179588.176000] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[17179588.180000] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[17179588.184000] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[17179588.284000] input: ImExPS/2 Generic Explorer Mouse as /class/input/input1
[17179588.388000] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[17179588.416000] tuner 1-0060: All bytes are equal. It is not a TEA5767
[17179588.416000] tuner 1-0060: chip found @ 0xc0 (bt878 #0 [sw])
[17179588.416000] tuner 1-0060: type set to 3 (Philips (SECAM+PAL_BG) (FI1216MF, FM1216MF, FR1216MF))
[17179588.448000] bttv0: registered device video0
[17179588.448000] bttv0: registered device vbi0
[17179588.448000] bttv0: PLL: 28636363 => 35468950 .. ok
[17179588.480000] bttv0: add subdevice "remote0"
[17179588.500000] input: PC Speaker as /class/input/input2
[17179588.528000] drivers/usb/media/spca5xx/spca5xx-main.c: USB SPCA5XX camera found. Pixart PAC207BCA
[17179588.540000] usbcore: registered new driver spca5xx
[17179588.540000] drivers/usb/media/spca5xx/spca5xx-main.c: spca5xx driver 00.57.08 registered
[17179588.600000] bt878: AUDIO driver version 0.0.0 loaded
[17179588.600000] bt878: Bt878 AUDIO function found (0).
[17179588.600000] ACPI: PCI Interrupt 0000:00:0b.1[A] -> GSI 19 (level, low) ->IRQ 193
[17179588.600000] bt878(0): Bt878 (rev 2) at 00:0b.1, irq: 193, latency: 32, memory: 0xcfcff000

I don't know how to configure it and if it's possible.

thanks for your help.

---

### Post by cymcy on 2006-07-27
for this time, the only thing to resolve the problem is to disconnect the webcam at boot and reconnect it after.

---

