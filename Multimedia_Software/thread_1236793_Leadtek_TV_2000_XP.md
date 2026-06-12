---
title: "Leadtek TV 2000 XP"
date: 2009-08-10
forum: Multimedia Software
---

### Post by luddie on 2009-08-10
[FONT=Arial][SIZE=2]Leadtek TV 2000 XP[/SIZE][/FONT]
 
[FONT=Arial][SIZE=2]I have spent the better part of the week reading the forums and seeing if anyone has a problem that resembles mine[/SIZE][/FONT]
 
[FONT=Arial][SIZE=2]I have a Leadtek TV 2000 XP and it seems ubuntu 9.04 has picked it up and installed the drivers for it.[/SIZE][/FONT]
 
[FONT=Arial][SIZE=2]lspci:[/SIZE][/FONT]
[FONT=Arial][SIZE=2]04:01.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)[/SIZE][/FONT]
[FONT=Arial][SIZE=2]04:01.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)[/SIZE][/FONT]
 
[FONT=Arial][SIZE=2]dmesg:[/SIZE][/FONT]
[FONT=Arial][SIZE=2][ 13.080754] bttv: driver version 0.9.17 loaded[/SIZE][/FONT]
[FONT=Arial][SIZE=2][ 13.080759] bttv: using 8 buffers with 2080k (520 pages) each for capture[/SIZE][/FONT]
[FONT=Arial][SIZE=2][ 13.080841] bttv: Bt8xx card found (0).[/SIZE][/FONT]
[FONT=Arial][SIZE=2][ 13.080861] bttv 0000:04:01.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19[/SIZE][/FONT]
[FONT=Arial][SIZE=2][ 13.080876] bttv0: Bt878 (rev 17) at 0000:04:01.0, irq: 19, latency: 32, mmio: 0xd4100000[/SIZE][/FONT]
[FONT=Arial][SIZE=2][ 13.081154] bttv0: detected: Leadtek TV 2000 XP [card=34], PCI subsystem ID is 107d:6609[/SIZE][/FONT]
[FONT=Arial][SIZE=2][ 13.081159] bttv0: using: Leadtek WinFast 2000/ WinFast 2000 XP [card=34,autodetected][/SIZE][/FONT]
[FONT=Arial][SIZE=2][ 13.081223] bttv0: gpio: en=00000000, out=00000000 in=003ff500 [init][/SIZE][/FONT]
[FONT=Arial][SIZE=2][ 13.081302] bttv0: tuner type=5[/SIZE][/FONT]
[FONT=Arial][SIZE=2][ 13.081308] bttv0: i2c: checking for MSP34xx @ 0x80... not found[/SIZE][/FONT]
[FONT=Arial][SIZE=2][ 13.083384] bttv0: i2c: checking for TDA9875 @ 0xb0... not found[/SIZE][/FONT]
[FONT=Arial][SIZE=2][ 13.084007] bttv0: i2c: checking for TDA7432 @ 0x8a... not found[/SIZE][/FONT]
[FONT=Arial][SIZE=2][ 13.144450] tuner' 0-0043: chip found @ 0x86 (bt878 #0 [sw])[/SIZE][/FONT]
[FONT=Arial][SIZE=2][ 13.167802] tuner' 0-0061: chip found @ 0xc2 (bt878 #0 [sw])[/SIZE][/FONT]
[FONT=Arial][SIZE=2][ 13.191586] tuner' 0-0063: chip found @ 0xc6 (bt878 #0 [sw])[/SIZE][/FONT]
[FONT=Arial][SIZE=2][ 13.197721] bttv0: registered device video0[/SIZE][/FONT]
[FONT=Arial][SIZE=2][ 13.197775] bttv0: registered device vbi0[/SIZE][/FONT]
[FONT=Arial][SIZE=2][ 13.197821] bttv0: registered device radio0[/SIZE][/FONT]
[FONT=Arial][SIZE=2][ 13.197843] bttv0: PLL: 28636363 => 35468950 .. ok[/SIZE][/FONT]
[FONT=Arial][SIZE=2][ 13.233117] input: bttv IR (card=34) as /devices/pci0000:00/0000:00:1e.0/0000:04:01.0/input/input5[/SIZE][/FONT]
 
[FONT=Arial][SIZE=3][SIZE=2]However, it is unable to scan and pick up channels in, mythtv, tvtime, xawtv. Does anyone have any advice or should I stop being cheap and just buy a new tuner?[/SIZE] [/SIZE][/FONT]

---

### Post by peacox27 on 2009-10-15
Luddie,

I am in the same boat as you. I have been fighting with this for a week now. I believe we are having the same issue, and I believe it has to do with the tuner type and not the card type. The bttv driver will try and auto detect both the card:

*[ 13.081154] bttv0: detected: Leadtek TV 2000 XP [card=34], PCI subsystem ID is 107d:6609*

which is did in this case, along with the tuner type:

*[ 13.081302] bttv0: tuner type=5*

and this is where I think our problem is. tuner type=5 is for a PAL signal, and I'm not sure about your case, but I live in the US which is an NTSC signal. So I have set my tuner type=2. Here is a list of the tuner types:

tuner=0 - Temic PAL (4002 FH5)
tuner=1 - Philips PAL_I (FI1246 and compatibles)
tuner=2 - Philips NTSC (FI1236,FM1236 and compatibles)
tuner=3 - Philips (SECAM+PAL_BG) (FI1216MF, FM1216MF, FR1216MF)
tuner=4 - NoTuner
tuner=5 - Philips PAL_BG (FI1216 and compatibles)
tuner=6 - Temic NTSC (4032 FY5)
tuner=7 - Temic PAL_I (4062 FY5)
tuner=8 - Temic NTSC (4036 FY5)
tuner=9 - Alps HSBH1
tuner=10 - Alps TSBE1
tuner=11 - Alps TSBB5
tuner=12 - Alps TSBE5
tuner=13 - Alps TSBC5
tuner=14 - Temic PAL_BG (4006FH5)
tuner=15 - Alps TSCH6
tuner=16 - Temic PAL_DK (4016 FY5)
tuner=17 - Philips NTSC_M (MK2)
tuner=18 - Temic PAL_I (4066 FY5)
tuner=19 - Temic PAL* auto (4006 FN5)
tuner=20 - Temic PAL_BG (4009 FR5) or PAL_I (4069 FR5)
tuner=21 - Temic NTSC (4039 FR5)
tuner=22 - Temic PAL/SECAM multi (4046 FM5)
tuner=23 - Philips PAL_DK (FI1256 and compatibles)
tuner=24 - Philips PAL/SECAM multi (FQ1216ME)
tuner=25 - LG PAL_I+FM (TAPC-I001D)
tuner=26 - LG PAL_I (TAPC-I701D)
tuner=27 - LG NTSC+FM (TPI8NSR01F)
tuner=28 - LG PAL_BG+FM (TPI8PSB01D)
tuner=29 - LG PAL_BG (TPI8PSB11D)
tuner=30 - Temic PAL* auto + FM (4009 FN5)
tuner=31 - SHARP NTSC_JP (2U5JF5540)
tuner=32 - Samsung PAL TCPM9091PD27
tuner=33 - MT20xx universal
tuner=34 - Temic PAL_BG (4106 FH5)
tuner=35 - Temic PAL_DK/SECAM_L (4012 FY5)
tuner=36 - Temic NTSC (4136 FY5)
tuner=37 - LG PAL (newer TAPC series)
tuner=38 - Philips PAL/SECAM multi (FM1216ME MK3)
tuner=39 - LG NTSC (newer TAPC series)
tuner=40 - HITACHI V7-J180AT
tuner=41 - Philips PAL_MK (FI1216 MK)
tuner=42 - Philips 1236D ATSC/NTSC dual in
tuner=43 - Philips NTSC MK3 (FM1236MK3 or FM1236/F)
tuner=44 - Philips 4 in 1 (ATI TV Wonder Pro/Conexant)
tuner=45 - Microtune 4049 FM5
tuner=46 - Panasonic VP27s/ENGE4324D
tuner=47 - LG NTSC (TAPE series)
tuner=48 - Tenna TNF 8831 BGFF)
tuner=49 - Microtune 4042 FI5 ATSC/NTSC dual in
tuner=50 - TCL 2002N
tuner=51 - Philips PAL/SECAM_D (FM 1256 I-H3)
tuner=52 - Thomson DTT 7610 (ATSC/NTSC)
tuner=53 - Philips FQ1286
tuner=54 - tda8290+75
tuner=55 - TCL 2002MB
tuner=56 - Philips PAL/SECAM multi (FQ1216AME MK4)
tuner=57 - Philips FQ1236A MK4
tuner=58 - Ymec TVision TVF-8531MF/8831MF/8731MF
tuner=59 - Ymec TVision TVF-5533MF
tuner=60 - Thomson DTT 761X (ATSC/NTSC)
tuner=61 - Tena TNF9533-D/IF/TNF9533-B/DF
tuner=62 - Philips TEA5767HN FM Radio
tuner=63 - Philips FMD1216ME MK3 Hybrid Tuner
tuner=64 - LG TDVS-H062F/TUA6034
tuner=65 - Ymec TVF66T5-B/DFF
tuner=66 - LG TALN series
tuner=67 - Philips TD1316 Hybrid Tuner
tuner=68 - Philips TUV1236D ATSC/NTSC dual in
tuner=69 - Tena TNF 5335 and similar models
tuner=70 - Samsung TCPN 2121P30A
tuner=71 - Xceive xc3028
tuner=72 - Thomson FE6600

Everything I have read seems to point to that, but I still get "no signal" from tvtime. This probably doesn't help much, but maybe if we get all the information out there we can get this figured out.

---

