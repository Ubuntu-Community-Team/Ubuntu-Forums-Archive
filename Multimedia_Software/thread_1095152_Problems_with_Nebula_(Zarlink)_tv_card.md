---
title: "Problems with Nebula (Zarlink) tv card"
date: 2009-03-13
forum: Multimedia Software
---

### Post by bouncysteve on 2009-03-13
I have a nebula pci tv card, the 2nd version:
# DVB Demod/Decoder: Zarlink MT352
# PCI Interface: Conexant Fusion 878A
# Tuner: Alps TDED4 DVB-T

I did have this working for about a month under Gutsy I think, but it stopped working after a kernel update and hasn't worked since. I've consumed all sorts of forums, but nothing has worked.

output of lspci:

00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV11DDR [GeForce2 MX200] (rev b2)
02:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)
02:0a.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
02:0a.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)

(selected) output of lsmod:

dvb_bt8xx              22916  0 
dvb_core               86272  1 dvb_bt8xx
bt878                  17464  1 dvb_bt8xx
bttv                  171028  2 dvb_bt8xx,bt878
videodev               41344  1 bttv
ir_common              48900  1 bttv
compat_ioctl32          9344  1 bttv
i2c_algo_bit           14340  1 bttv
v4l2_common            19840  1 bttv
videobuf_dma_sg        20612  1 bttv
videobuf_core          26628  2 bttv,videobuf_dma_sg
btcx_risc              12552  1 bttv
tveeprom               20228  1 bttv
i2c_core               31892  6 dvb_bt8xx,bttv,i2c_algo_bit,v4l2_common,tveeprom,nvidia

(selected) output of /var/log/messages:

Mar 13 13:55:13 sv-desktop kernel: [   12.267013] nvidia: module license 'NVIDIA' taints kernel.
Mar 13 13:55:13 sv-desktop kernel: [   12.715932] input: PC Speaker as /devices/platform/pcspkr/input/input5
Mar 13 13:55:13 sv-desktop kernel: [   13.098092] parport_pc 00:09: reported by Plug and Play ACPI
Mar 13 13:55:13 sv-desktop kernel: [   13.098202] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
Mar 13 13:55:13 sv-desktop kernel: [   13.144151] Linux video capture interface: v2.00
Mar 13 13:55:13 sv-desktop kernel: [   13.175302] bttv: driver version 0.9.17 loaded
Mar 13 13:55:13 sv-desktop kernel: [   13.175309] bttv: using 8 buffers with 2080k (520 pages) each for capture
Mar 13 13:55:13 sv-desktop kernel: [   13.175419] bttv: Bt8xx card found (0).
Mar 13 13:55:13 sv-desktop kernel: [   13.175443] bttv 0000:02:0a.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
Mar 13 13:55:13 sv-desktop kernel: [   13.175458] bttv0: Bt878 (rev 17) at 0000:02:0a.0, irq: 21, latency: 64, mmio: 0xf7efe000
Mar 13 13:55:13 sv-desktop kernel: [   13.175476] bttv0: using: Nebula Electronics DigiTV [card=104,insmod option]
Mar 13 13:55:13 sv-desktop kernel: [   13.175621] bttv0: tuner absent
Mar 13 13:55:13 sv-desktop kernel: [   13.175814] bttv0: registered device video0
Mar 13 13:55:13 sv-desktop kernel: [   13.175908] bttv0: registered device vbi0
Mar 13 13:55:13 sv-desktop kernel: [   13.175931] bttv0: PLL: 28636363 => 35468950 .. ok
Mar 13 13:55:13 sv-desktop kernel: [   13.208601] bttv0: add subdevice "dvb0"
Mar 13 13:55:13 sv-desktop kernel: [   13.208888] input: bttv IR (card=104) as /devices/pci0000:00/0000:00:1e.0/0000:02:0a.0/input/input6
Mar 13 13:55:13 sv-desktop kernel: [   13.424227] bt878: AUDIO driver version 0.0.0 loaded
Mar 13 13:55:13 sv-desktop kernel: [   13.544800] dvb_bt8xx: unable to determine DMA core of card 0,
Mar 13 13:55:13 sv-desktop kernel: [   13.544806] dvb_bt8xx: if you have the ALSA bt87x audio driver installed, try removing it.
Mar 13 13:55:13 sv-desktop kernel: [   13.544817] dvb-bt8xx: probe of dvb0 failed with error -14


bt87x is not loaded, so I don't know what the problem is, or why there's no tuner assigned.

Please help!

---

### Post by wolfen69 on 2009-03-13
[This]("http://linuxtv.org/wiki/index.php/Bttv_devices_(bt848%2C_bt878)") may help.

---

### Post by bouncysteve on 2009-03-15
Thanks for the pointer, but I feel like I've read a mountain of documentation on this, and need a little guidance. 

I now understand that the bt878 in lspci is a red herring, because my card has a Fusion 878A chipset, so maybe I've been doing something wrong.

I was loading dst, bttv and dvb_bt8xx which I think might have been the cause of the conflict. I think that I only need to load bttv now (and maybe not even that - shouldn't Ubuntu scan my hardware and load the appropriate modules by default?).

I've cleaned out /etc/modules and rebooted, but I'm still getting dvb_bt8xx, (and hence bt878, bttv, dvb_core, etc) loaded automatically, and the card version is being set by insmod, and not autodetected, even though I thought I'd removed the settings from everywhere (/etc/modprobe.d/bttv, /etc/modprobe.conf).

Is bttv sufficient or should I be loading dvb_bt8xx?

---

### Post by xc3RnbFO8P on 2009-03-15
In Terminal:
> gedit /etc/modules
check  you got these lines:
[B]sa7134-dvb
dvb-bt8xx[/B]

---

### Post by bouncysteve on 2009-03-15
I've done that now, but I still get the bt87x warning message, and I don't think I need to load saa7134-dvb, as my card has a conexant chipset. Here's some of my dmesg:

[   16.461218] saa7130/34: v4l2 driver version 0.2.14 loaded
[   16.483141] saa7134 ALSA driver for DMA sound loaded
[   16.483146] saa7134 ALSA: no saa7134 cards found

---

### Post by xc3RnbFO8P on 2009-03-16
You can try to add **mt352** in Modules and
**modprobe mt352**

---

### Post by bouncysteve on 2009-03-18
I've tried adding mt352 explicitly in /etc/modules and also tried using mt352 in place of nxt600 in this supposed fix of the issue from [http://www.dtvforum.info/index.php?showtopic=13523&mode=linear](http://www.dtvforum.info/index.php?showtopic=13523&mode=linear)

modprobe.conf:
> install bttv /sbin/modprobe --ignore-install bttv && { /sbin/modprobe mt352; /sbin/modprobe dvb-bt8xx; /bin/true; }

In both cases, dmesg still reports the conflict

---

### Post by bouncysteve on 2009-04-08
I've used the instructions here ([http://www.linuxtv.org/wiki/index.php/Twinhan_VP-1020A](http://www.linuxtv.org/wiki/index.php/Twinhan_VP-1020A)) to rewrite the card's eeprom. The card is now autodetected as 104 and the conflict is no longer reported. When I load the bttv module now I get the message "tuner absent".

I have tried each possible value of tuner from 0 to 42 but each time I get the same message, "tuner absent".

Any ideas please?

---

