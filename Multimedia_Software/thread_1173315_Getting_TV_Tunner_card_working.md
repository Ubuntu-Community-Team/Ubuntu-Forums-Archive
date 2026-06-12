---
title: "Getting TV Tunner card working"
date: 2009-05-29
forum: Multimedia Software
---

### Post by bizhat on 2009-05-29
My TV Tunner Card PCTV 100i from pinnacle is shown in lspci and in dmesg

in dmesg

> 
[    7.835092] Linux video capture interface: v2.00
[    7.872814] bttv: driver version 0.9.17 loaded
[    7.872817] bttv: using 8 buffers with 2080k (520 pages) each for capture
[    7.872887] bttv: Bt8xx card found (0).
[    7.872901] bttv 0000:05:04.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    7.872911] bttv0: Bt878 (rev 17) at 0000:05:04.0, irq: 18, latency: 32, mmio: 0x90001000
[    7.872943] bttv0: detected: Pinnacle PCTV [card=39], PCI subsystem ID is 11bd:0012
[    7.872945] bttv0: using: Pinnacle PCTV Studio/Rave [card=39,autodetected]
[    7.872971] bttv0: gpio: en=00000000, out=00000000 in=00ffffff [init]
[    7.873036] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[    7.873681] bttv0: pinnacle/mt: id=1 info="PAL / mono" radio=no
[    7.873683] bttv0: tuner type=33
[    7.873686] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[    7.874308] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[    7.874913] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[    7.917361] tuner' 0-0043: chip found @ 0x86 (bt878 #0 [sw])
[    7.958864] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    7.958925] HDA Intel 0000:00:1b.0: setting latency timer to 64
[    7.959141] tda9887 0-0043: creating new instance
[    7.959143] tda9887 0-0043: tda988[5/6/7] found
[    7.968276] Chip ID is not zero. It is not a TEA5767
[    7.968338] tuner' 0-0060: chip found @ 0xc0 (bt878 #0 [sw])
[    7.982181] mt20xx 0-0060: microtune: companycode=3dbf part=42 rev=82



in lspci

> 
$ lspci
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
05:04.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
05:04.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
05:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
$ 


On a search i found  "Brooktree Corporation Bt878 Video Capture" is related to my tv tunner card.

How do i watch TV, what software i need to install ?


Thanks,

Annie

---

### Post by bowens44 on 2009-05-29
tvtime is available in the repos. It works well.

---

### Post by bizhat on 2009-05-30
Thanks, got it working.

But no sound yet, i increase volume, but only hissing shound increases, TV tunner card is connected to Sound card line-in. 

Also video quality is bad (most channels have lost it colours, displayed near black and white). On same computer, if i boot to windows the TV tuner card works fine with every channel displayed in proper colour.

Any idea how to fix the problem ?

---

