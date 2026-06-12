---
title: "Wintv HVR 1250 card not working"
date: 2009-02-15
forum: Multimedia Software
---

### Post by madmagic on 2009-02-15
Well after a few days of trying to get it to work with ubuntu, i went to mythbuntu. Its being recognized a little better.

sudo lspci -v
```
03:00.0 Multimedia video controller: Conexant Systems, Inc. CX23885 PCI Video and Audio Decoder (rev 03)
	Subsystem: Hauppauge computer works Inc. Device 7911
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at fea00000 (64-bit, non-prefetchable) [size=2M]
	Capabilities: [40] Express Endpoint, MSI 00
	Capabilities: [80] Power Management version 2
	Capabilities: [90] Vital Product Data <?>
	Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [200] Virtual Channel <?>
	Kernel driver in use: cx23885
	Kernel modules: cx23885

```

this is were i think my problem is
dmesg | grep cx23885
```
[    8.785826] cx23885 driver version 0.0.1 loaded
[    8.785871] cx23885 0000:03:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    8.785922] CORE cx23885[0]: subsystem: 0070:7911, board: Hauppauge WinTV-HVR1250 [card=3,autodetected]
[B][    8.915649] cx23885[0]: warning: unknown hauppauge model #0
[    8.915651] cx23885[0]: hauppauge eeprom: model=0[/B]
[    8.915655] cx23885_dvb_register() allocating 1 frontend(s)
[    8.916182] cx23885[0]: cx23885 based dvb card
[    9.044048] DVB: registering new adapter (cx23885[0])
[    9.044476] cx23885_dev_checkrevision() Hardware revision = 0xc0
[    9.044487] cx23885[0]/0: found at 0000:03:00.0, rev: 3, irq: 19, latency: 0, mmio: 0xfea00000
[    9.044522] cx23885 0000:03:00.0: setting latency timer to 64

```

as you can see there is a error that comes up. Any help or insight into this problem would be much appreciated

---

### Post by madmagic on 2009-02-15
ok i used the command make insmod in the v4l directory and i now get this
dmesg | grep cx23885
```
[    8.785826] cx23885 driver version 0.0.1 loaded
[    8.785871] cx23885 0000:03:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    8.785922] CORE cx23885[0]: subsystem: 0070:7911, board: Hauppauge WinTV-HVR1250 [card=3,autodetected]
[    8.915649] cx23885[0]: warning: unknown hauppauge model #0
[    8.915651] cx23885[0]: hauppauge eeprom: model=0
[    8.915655] cx23885_dvb_register() allocating 1 frontend(s)
[    8.916182] cx23885[0]: cx23885 based dvb card
[    9.044048] DVB: registering new adapter (cx23885[0])
[    9.044476] cx23885_dev_checkrevision() Hardware revision = 0xc0
[    9.044487] cx23885[0]/0: found at 0000:03:00.0, rev: 3, irq: 19, latency: 0, mmio: 0xfea00000
[    9.044522] cx23885 0000:03:00.0: setting latency timer to 64
[B][ 2509.806441] msp3400' 2-0044: MSP144188L-&#65533;28 found @ 0x88 (cx23885[0])
[ 2510.728715] tvaudio' 2-004c: tea6420 found @ 0x98 (cx23885[0])
[ 2510.853731] vpx3220' 1-0043: chip (0f:0e0e) found @ 0x86 (cx23885[0])[/B]

```

The output of uname -r
```
2.6.27-11-generic
```

yet again when i try to do make allmodconfig in the v4l directory i get
```
make -C /home/server/Desktop/tv/v4l allmodconfig
make[1]: Entering directory `/home/server/Desktop/tv/v4l'
./scripts/make_kconfig.pl /lib/modules/2.6.27-11-generic/build /lib/modules/2.6.27-11-generic/build 1
Preparing to compile for kernel version 2.6.27

***WARNING:*** You do not have the full kernel sources installed.
This does not prevent you from building the v4l-dvb tree if you have the
kernel headers, but the full kernel source may be required in order to use
make menuconfig / xconfig / qconfig.

If you are experiencing problems building the v4l-dvb tree, please try
building against a vanilla kernel before reporting a bug.

Vanilla kernels are available at http://kernel.org.
On most distros, this will compile a newly downloaded kernel:

cp /boot/config-`uname -r` <your kernel dir>/.config
cd <your kernel dir>
make all modules_install install

Please see your distro's web site for instructions to build a new kernel.

VIDEO_PXA27x: Requires at least kernel 2.6.29
USB_STV06XX: Requires at least kernel 2.6.28
Created default (all yes) .config file
make[1]: Leaving directory `/home/server/Desktop/tv/v4l'

```

So is it saying that i don't have a high enough kernel version to do that command?

---

### Post by wolfen69 on 2009-02-15
see [this]("http://linuxtv.org/wiki/index.php/Cx88_devices_(cx2388x)").

---

### Post by madmagic on 2009-02-15
Ok i must be doing something wrong because when i type "/usr/src/Linux" it says No such file or directory. This is were i must recompile the kernel right?

---

### Post by madmagic on 2009-02-15
Ok, im currently recompiling the kernel, ill post back tomorrow when its done

---

### Post by madmagic on 2009-02-17
ok, dmesg | grep cx23885 now posts as this
```
[   12.347302] cx23885 driver version 0.0.1 loaded
[   12.347412] cx23885 0000:03:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   12.347524] CORE cx23885[0]: subsystem: 0070:7911, board: Hauppauge WinTV-HVR1250 [card=3,autodetected]
[   12.448556] cx23885[0]: i2c bus 0 registered
[   12.452756] cx23885[0]: i2c bus 1 registered
[   12.458034] cx23885[0]: i2c bus 2 registered
[   12.486894] cx23885[0]: warning: unknown hauppauge model #0
[   12.486953] cx23885[0]: hauppauge eeprom: model=0
[   12.487017] cx23885[0]: cx23885 based dvb card
[   12.775529] DVB: registering new adapter (cx23885[0])
[   12.776156] cx23885_dev_checkrevision() Hardware revision = 0xc0
[   12.776232] cx23885[0]/0: found at 0000:03:00.0, rev: 3, irq: 19, latency: 0, mmio: 0xfea00000
[   12.776331] cx23885 0000:03:00.0: setting latency timer to 64

```
Still have that error -_-

Also
modprobe cx88-dvb gives a weird error to, even though my card is being recognized as a cx88 card,
```
FATAL: Error inserting cx88_dvb (/lib/modules/2.6.27/kernel/drivers/media/video/cx88/cx88-dvb.ko): No such device

```
i dont know if this is coming from one problem of there being no /dev/video0 or if because of this problem there is no /dev/video0. Any help would be appreciated.

EDIT:
i forgot to post dmesg | grep cx88
```
[ 1717.148085] cx88/2: cx2388x MPEG-TS Driver Manager version 0.0.6 loaded
[ 1717.160982] cx88/2: cx2388x dvb driver version 0.0.6 loaded
[ 1717.160988] cx88/2: registering cx8802 driver, type: dvb access: shared

```

---

### Post by madmagic on 2009-02-17
Just going to throw out an idea here, what if i was able to change the model number from 0 to the correct model number, would that make /dev/video0 appear?
/dev/dvb/adapter0 is there, i dont know if that means any thing, but i cant use it as a device (i tried).

---

