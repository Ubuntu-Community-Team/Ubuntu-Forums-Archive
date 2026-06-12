---
title: "xc5000 firmware not loading"
date: 2009-07-27
forum: Mythbuntu
---

### Post by tommyp on 2009-07-27
I am having a problem getting my Pinnacle 800i cards to work in Jaunty (they worked in Hardy).  I have placed the latest firmware in the /lib/firmware folder.  For some reason, the firmware is not loading.  Dmesg output:
```
[   18.959805] tuner' 2-0064: chip found @ 0xc8 (cx88[0])
[   19.009596] xc5000 2-0064: creating new instance
[   19.010242] xc5000: Successfully identified at address 0x64
[   19.010244] xc5000: Firmware has not been loaded previously
[   19.010851] xc5000: waiting for firmware upload (dvb-fe-xc5000-1.1.fw)...
[   19.010854] i2c-adapter i2c-2: firmware: requesting dvb-fe-xc5000-1.1.fw
[   19.044309] xc5000: Upload failed. (file not found?)
[   19.044313] xc5000: Unable to initialise tuner
[   19.044397] input: cx88 IR (Pinnacle PCTV HD 800i) as /devices/pci0000:00/0000:00:10.0/0000:03:06.0/input/input7
[   19.045443] cx88[0]/0: found at 0000:03:06.0, rev: 5, irq: 18, latency: 32, mmio: 0xfc000000
[   19.045520] cx88[0]/0: registered device video0 [v4l2]
[   19.045560] cx88[0]/0: registered device vbi0
[   19.046868] xc5000: waiting for firmware upload (dvb-fe-xc5000-1.1.fw)...
[   19.046871] i2c-adapter i2c-2: firmware: requesting dvb-fe-xc5000-1.1.fw
[   19.048748] xc5000: Upload failed. (file not found?)
[   19.147956] psmouse serio1: ID: 10 00 64<6>intel8x0_measure_ac97_clock: measured 53977 usecs
[   19.212022] intel8x0: clocking to 46965
[   19.685978] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input8
[   20.088500] i2c-adapter i2c-2: sendbytes: NAK bailout.
[   20.088519] xc5000: I2C write failed (len=4)
[   20.088521] xc5000: xc_SetTVStandard failed
[   20.088609] cx88_audio 0000:03:06.1: PCI INT A -> Link[APC3] -> GSI 18 (level, low) -> IRQ 18
[   20.088632] cx88[0]/1: CX88x/0: ALSA support for cx2388x boards
[   20.088987] cx88[0]/2: cx2388x 8802 Driver Manager
[   20.088996] cx88-mpeg driver manager 0000:03:06.2: PCI INT A -> Link[APC3] -> GSI 18 (level, low) -> IRQ 18
[   20.089002] cx88[0]/2: found at 0000:03:06.2, rev: 5, irq: 18, latency: 32, mmio: 0xfa000000
[   20.089010] cx8802_probe() allocating 1 frontend(s)
[   20.089370] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
[   20.089373] cx8800 0000:03:08.0: PCI INT A -> Link[APC1] -> GSI 16 (level, low) -> IRQ 16
[   20.089902] cx88[1]: subsystem: 11bd:0051, board: Pinnacle PCTV HD 800i [card=58,autodetected], frontend(s): 1
[   20.089904] cx88[1]: TV tuner type 76, Radio tuner type -1
[   20.212499] tuner' 3-0064: chip found @ 0xc8 (cx88[1])
[   20.244578] xc5000 3-0064: creating new instance
[   20.245199] xc5000: Successfully identified at address 0x64
[   20.245200] xc5000: Firmware has not been loaded previously
[   20.245807] xc5000: waiting for firmware upload (dvb-fe-xc5000-1.1.fw)...
[   20.245810] i2c-adapter i2c-3: firmware: requesting dvb-fe-xc5000-1.1.fw
[   20.249470] xc5000: Upload failed. (file not found?)
[   20.249475] xc5000: Unable to initialise tuner
[   20.249565] input: cx88 IR (Pinnacle PCTV HD 800i) as /devices/pci0000:00/0000:00:10.0/0000:03:08.0/input/input9
[   20.251459] cx88[1]/0: found at 0000:03:08.0, rev: 5, irq: 16, latency: 32, mmio: 0xf9000000
[   20.251537] cx88[1]/0: registered device video1 [v4l2]
[   20.251574] cx88[1]/0: registered device vbi1
[   20.252905] xc5000: waiting for firmware upload (dvb-fe-xc5000-1.1.fw)...
[   20.252907] i2c-adapter i2c-3: firmware: requesting dvb-fe-xc5000-1.1.fw
[   20.254611] xc5000: Upload failed. (file not found?)
[   21.292506] i2c-adapter i2c-3: sendbytes: NAK bailout.
[   21.292525] xc5000: I2C write failed (len=4)
[   21.292526] xc5000: xc_SetTVStandard failed

```

Any thoughts on how to get the firmware to load?

---

### Post by nasha on 2009-07-27
I noticed Jaunty requires you to place the fw in /lib/firmware/2.6.xx.x :)

---

### Post by tommyp on 2009-07-28
I realized that I was not using the right drivers for the firmware.  If you want to use the included kernel drivers, you have to use the old firmware.  To use the new firmware, you have to be using the latest v4l drivers or a newer kernel.  See here under "Fireware":

[http://www.linuxtv.org/wiki/index.php/Pinnacle_PCTV_HD_Card_(800i)](http://www.linuxtv.org/wiki/index.php/Pinnacle_PCTV_HD_Card_(800i))

---

