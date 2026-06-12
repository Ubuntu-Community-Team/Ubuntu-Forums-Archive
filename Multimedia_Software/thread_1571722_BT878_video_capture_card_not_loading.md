---
title: "BT878 video capture card not loading"
date: 2010-09-10
forum: Multimedia Software
---

### Post by Sav1 on 2010-09-10
I have BT878 based card video capture card that is not loading correctly. It was working but then stopped and I cant get it to work even after a clean install.

I would appreciate any help.

Below is the output of dmesg | grep bttv

```

[ 11.503559] bttv: driver version 0.9.18 loaded 
[ 11.503562] bttv: using 8 buffers with 2080k (520 pages) each for capture 
[ 11.504215] bttv: Bt8xx card found (0). 
[ 11.504226] bttv 0000:01:08.0: Refused to change power state, currently in D3 
[ 11.504456] bttv 0000:01:08.0: PCI INT A -> Link[APC1] -> GSI 16 (level, low) -> IRQ 16 
[ 11.504465] bttv0: Bt878 (rev 255) at 0000:01:08.0, irq: 16, latency: 255, mmio: 0xe2000000 
[ 11.504751] bttv0: using: GrandTec Multi Capture Card (Bt878) [card=77,insmod option] 
[ 11.504754] IRQ 16/bttv0: IRQF_DISABLED is not guaranteed on shared IRQs 
[ 11.504787] bttv0: gpio: en=ffffffff, out=ffffffff in=00000000 [init] 
[ 11.504961] bttv0: tuner absent 
[ 11.504963] bttv0: the autoload option is obsolete. 
[ 11.504965] bttv0: use option msp3400, tda7432 or tvaudio to 
[ 11.504967] bttv0: override which audio module should be used. 
[ 11.505099] bttv0: registered device video0 
[ 11.505200] bttv0: registered device vbi0 
[ 11.505215] bttv0: PLL: 28636363 => 35468950 ......Console: switching to colour frame buffer device 80x30 
[ 11.676817] bttv0: PLL: 28636363 => 35468950 . 
[ 11.677602] bttv0: PLL: 28636363 => 35468950 ............. 
[ 11.837064] bttv0: PLL: 28636363 => 35468950 .failed 
[ 11.837078] bttv0: PLL: 28636363 => 35468950 ........... 
[ 20.222789] bttv0: PLL: 28636363 => 35468950 . 
[ 20.230599] bttv0: PLL: 28636363 => 35468950 ...................failed 
[ 20.384040] bttv0: PLL: 28636363 => 35468950 .failed 
[ 20.389042] bttv0: PLL: 28636363 => 35468950 ...................failed 
[ 102.931945] bttv0: PLL: 28636363 => 35468950 ..........failed 
[ 103.089091] bttv0: PLL: 28636363 => 35468950 ..........failed 
[ 103.249906] bttv0: PLL: 28636363 => 35468950 ..........failed 
[ 103.409020] bttv0: PLL: 28636363 => 35468950 ..........failed 
[ 104.085026] bttv0: timeout: drop=0 irq=0/0, risc=ffffffff, bits: FMTCHG VSYNC HSYNC OFLOW HLOCK VPRES 6 7 I2CDONE GPINT 10 RISCI FBUS FTRGT FDSR PPERR RIPERR PABORT OCERR SCERR 
[ 104.163701] bttv0: PLL: 28636363 => 35468950 ..........failed 
[ 104.320043] bttv0: PLL: 28636363 => 35468950 ..........failed 
[ 104.480177] bttv0: PLL: 28636363 => 35468950 ..........failed 
[ 104.640031] bttv0: PLL: 28636363 => 35468950 ..........failed 
[ 105.328028] bttv0: timeout: drop=0 irq=0/0, risc=ffffffff, bits: FMTCHG VSYNC HSYNC OFLOW HLOCK VPRES 6 7 I2CDONE GPINT 10 RISCI FBUS FTRGT FDSR PPERR RIPERR PABORT OCERR SCERR 
[ 110.114324] bttv0: PLL: 28636363 => 35468950 ..........failed 
[ 110.272040] bttv0: PLL: 28636363 => 35468950 ..........failed 
[ 110.432230] bttv0: PLL: 28636363 => 35468950 ..........failed 
[ 110.592055] bttv0: PLL: 28636363 => 35468950 ..........failed 
[ 111.280023] bttv0: timeout: drop=0 irq=0/0, risc=ffffffff, bits: FMTCHG VSYNC HSYNC OFLOW HLOCK VPRES 6 7 I2CDONE GPINT 10 RISCI FBUS FTRGT FDSR PPERR RIPERR PABORT OCERR SCERR 
[ 121.076583] bttv0: PLL: 28636363 => 35468950 ..........failed 
[ 121.237043] bttv0: PLL: 28636363 => 35468950 ..........failed 
[ 121.396188] bttv0: PLL: 28636363 => 35468950 ..........failed 
[ 121.556339] bttv0: PLL: 28636363 => 35468950 ..........failed 
[ 122.248023] bttv0: timeout: drop=0 irq=0/0, risc=ffffffff, bits: FMTCHG VSYNC HSYNC OFLOW HLOCK VPRES 6 7 I2CDONE GPINT 10 RISCI FBUS FTRGT FDSR PPERR RIPERR PABORT OCERR SCERR 
[ 142.102630] bttv0: PLL: 28636363 => 35468950 ..........failed 
[ 142.260039] bttv0: PLL: 28636363 => 35468950 ..........failed 
[ 142.420186] bttv0: PLL: 28636363 => 35468950 ..........failed 
[ 142.580036] bttv0: PLL: 28636363 => 35468950 ..........failed 
[ 143.268029] bttv0: timeout: drop=0 irq=0/0, risc=ffffffff, bits: FMTCHG VSYNC HSYNC OFLOW HLOCK VPRES 6 7 I2CDONE GPINT 10 RISCI FBUS FTRGT FDSR PPERR RIPERR PABORT OCERR SCERR 
[ 183.152446] bttv0: PLL: 28636363 => 35468950 ..........failed 
[ 183.308038] bttv0: PLL: 28636363 => 35468950 ..........failed 
[ 183.468182] bttv0: PLL: 28636363 => 35468950 ..........failed 
[ 183.628037] bttv0: PLL: 28636363 => 35468950 ..........failed 
[ 184.317038] bttv0: timeout: drop=0 irq=0/0, risc=ffffffff, bits: FMTCHG VSYNC HSYNC OFLOW HLOCK VPRES 6 7 I2CDONE GPINT 10 RISCI FBUS FTRGT FDSR PPERR RIPERR PABORT OCERR SCERR 
[ 264.068421] bttv0: PLL: 28636363 => 35468950 ..........failed 
[ 264.229092] bttv0: PLL: 28636363 => 35468950 ..........failed 
[ 264.388189] bttv0: PLL: 28636363 => 35468950 ..........failed 
[ 264.548029] bttv0: PLL: 28636363 => 35468950 ..........failed 
[ 265.240027] bttv0: timeout: drop=0 irq=0/0, risc=ffffffff, bits: FMTCHG VSYNC HSYNC OFLOW HLOCK VPRES 6 7 I2CDONE GPINT 10 RISCI FBUS FTRGT FDSR PPERR RIPERR PABORT OCERR SCERR 
[ 425.116902] bttv0: PLL: 28636363 => 35468950 ..........failed 
[ 425.272038] bttv0: PLL: 28636363 => 35468950 ..........failed 
[ 425.432205] bttv0: PLL: 28636363 => 35468950 ..........failed 
[ 425.592029] bttv0: PLL: 28636363 => 35468950 ..........failed 
[ 426.280026] bttv0: timeout: drop=0 irq=0/0, risc=ffffffff, bits: FMTCHG VSYNC HSYNC OFLOW HLOCK VPRES 6 7 I2CDONE GPINT 10 RISCI FBUS FTRGT FDSR PPERR RIPERR PABORT OCERR SCERR 
[ 746.065907] bttv0: PLL: 28636363 => 35468950 ..........failed 
[ 746.228025] bttv0: PLL: 28636363 => 35468950 ..........failed 
[ 746.388132] bttv0: PLL: 28636363 => 35468950 ..........failed 
[ 746.544038] bttv0: PLL: 28636363 => 35468950 ..........failed 
[ 747.220017] bttv0: timeout: drop=0 irq=0/0, risc=ffffffff, bits: FMTCHG VSYNC HSYNC OFLOW HLOCK VPRES 6 7 I2CDONE GPINT 10 RISCI FBUS FTRGT FDSR PPERR RIPERR PABORT OCERR SCERR

```

---

### Post by moboticdes on 2010-09-10
you might need to create a file named /etc/modprobe.d/bttv.modprobe and add the line below:   options bttv card=77
to support the bt878 video card.

Also check you didn't change any PCI configuration (added PCI cards or video cards) as that can make IRQ errors popup

---

### Post by Sav1 on 2010-09-10
> **moboticdes said:**
> you might need to create a file named /etc/modprobe.d/bttv.modprobe and add the line below:   options bttv card=77
to support the bt878 video card.

Thanks but I already have a file named /etc/modprobe.d/cctv.conf with "options bttv card=77 tuner=4 radio=0 triton1=0 vsfx=0 autoload=0" in it.

Have made no changes to the system, even did a clean install which didn't solve the problem.


Edit: Rebooted and it started working again. Didn't change anything.

---

