---
title: "TVtime doesn't always work / Alsamixer samplerate problem"
date: 2006-01-28
forum: Multimedia &amp; Video
---

### Post by TripleSix on 2006-01-28
Two problems, that occurred in virtually the same period, and maybe somehow connected.

Problem 1: I have a TV tuner card, a Pinnacle PCTV stereo, and I use tvtime to watch. Somehow, in 75% of the cases, tvtime receives no signal after a fresh boot. I have to manually remove and reprobe the saa7134 module to get it to work again.

Problem 2: alsamixer. It worked fine for a couple of weeks, but after that, at every start of a new ubuntu session, the samplerate is changed to 8000Hz. I have to manually reset it to 44100 (or above) to have it produce proper sound again.

I just noticed that the samplerate is also reset to 8000Hz when I do the sound test in  the Ubuntu Device Database. FYI: My soundcard is a Terratec DMX6fire.

Any ideas on above troubles?

---

### Post by egodust on 2006-01-31
Are you sure the saa7134 module is picking up your card correctly? That seems like a high failure rate!

Do in a console:
```

dmesg | grep saa7134

```

Does it show a "insmod" option in the output? or is it an autodetect? you may need to select the card # and tuner # manually. The number depends on the kernel, you can find a list in the kernel sources in the drivers/media/video/saa7134, you need to install the sources for your running kernel.

The following is for 2.6.15, files **saa7134.h**
```

/* card configuration                                          */

#define SAA7134_BOARD_NOAUTO        UNSET
#define SAA7134_BOARD_UNKNOWN           0
#define SAA7134_BOARD_PROTEUS_PRO       1
#define SAA7134_BOARD_FLYVIDEO3000      2
#define SAA7134_BOARD_FLYVIDEO2000      3
#define SAA7134_BOARD_EMPRESS           4
#define SAA7134_BOARD_MONSTERTV         5
#define SAA7134_BOARD_MD9717            6
#define SAA7134_BOARD_TVSTATION_RDS     7
#define SAA7134_BOARD_CINERGY400	8
#define SAA7134_BOARD_MD5044		9
#define SAA7134_BOARD_KWORLD           10
#define SAA7134_BOARD_CINERGY600       11
#define SAA7134_BOARD_MD7134           12
#define SAA7134_BOARD_TYPHOON_90031    13
#define SAA7134_BOARD_ELSA             14
#define SAA7134_BOARD_ELSA_500TV       15
#define SAA7134_BOARD_ASUSTeK_TVFM7134 16
#define SAA7134_BOARD_VA1000POWER      17
#define SAA7134_BOARD_BMK_MPEX_NOTUNER 18
#define SAA7134_BOARD_VIDEOMATE_TV     19
#define SAA7134_BOARD_CRONOS_PLUS      20
#define SAA7134_BOARD_10MOONSTVMASTER  21
#define SAA7134_BOARD_MD2819           22
#define SAA7134_BOARD_BMK_MPEX_TUNER   23
#define SAA7134_BOARD_TVSTATION_DVR    24
#define SAA7134_BOARD_ASUSTEK_TVFM7133	25
#define SAA7134_BOARD_PINNACLE_PCTV_STEREO 26
#define SAA7134_BOARD_MANLI_MTV002     27
#define SAA7134_BOARD_MANLI_MTV001     28
#define SAA7134_BOARD_TG3000TV         29
#define SAA7134_BOARD_ECS_TVP3XP       30
#define SAA7134_BOARD_ECS_TVP3XP_4CB5  31
#define SAA7134_BOARD_AVACSSMARTTV     32
#define SAA7134_BOARD_AVERMEDIA_DVD_EZMAKER 33
#define SAA7134_BOARD_NOVAC_PRIMETV7133 34
#define SAA7134_BOARD_AVERMEDIA_STUDIO_305 35
#define SAA7134_BOARD_UPMOST_PURPLE_TV 36
#define SAA7134_BOARD_ITEMS_MTV005     37
#define SAA7134_BOARD_CINERGY200       38
#define SAA7134_BOARD_FLYTVPLATINUM_MINI 39
#define SAA7134_BOARD_VIDEOMATE_TV_PVR 40
#define SAA7134_BOARD_VIDEOMATE_TV_GOLD_PLUS 41
#define SAA7134_BOARD_SABRENT_SBTTVFM  42
#define SAA7134_BOARD_ZOLID_XPERT_TV7134 43
#define SAA7134_BOARD_EMPIRE_PCI_TV_RADIO_LE 44
#define SAA7134_BOARD_AVERMEDIA_STUDIO_307    45
#define SAA7134_BOARD_AVERMEDIA_CARDBUS 46
#define SAA7134_BOARD_CINERGY400_CARDBUS 47
#define SAA7134_BOARD_CINERGY600_MK3   48
#define SAA7134_BOARD_VIDEOMATE_GOLD_PLUS 49
#define SAA7134_BOARD_PINNACLE_300I_DVBT_PAL 50
#define SAA7134_BOARD_PROVIDEO_PV952   51
#define SAA7134_BOARD_AVERMEDIA_305    52
#define SAA7134_BOARD_ASUSTeK_TVFM7135 53
#define SAA7134_BOARD_FLYTVPLATINUM_FM 54
#define SAA7134_BOARD_FLYDVBTDUO 55
#define SAA7134_BOARD_AVERMEDIA_307    56
#define SAA7134_BOARD_AVERMEDIA_GO_007_FM 57
#define SAA7134_BOARD_ADS_INSTANT_TV 58
#define SAA7134_BOARD_KWORLD_VSTREAM_XPERT 59
#define SAA7134_BOARD_THYPHOON_DVBT_DUO_CARDBUS 60
#define SAA7134_BOARD_PHILIPS_TOUGH 61
#define SAA7134_BOARD_VIDEOMATE_TV_GOLD_PLUSII 62
#define SAA7134_BOARD_KWORLD_XPERT 63
#define SAA7134_BOARD_FLYTV_DIGIMATRIX 64
#define SAA7134_BOARD_KWORLD_TERMINATOR 65
#define SAA7134_BOARD_YUAN_TUN900 66
#define SAA7134_BOARD_BEHOLD_409FM 67
#define SAA7134_BOARD_GOTVIEW_7135 68
#define SAA7134_BOARD_PHILIPS_EUROPA  69
#define SAA7134_BOARD_VIDEOMATE_DVBT_300 70
#define SAA7134_BOARD_VIDEOMATE_DVBT_200 71
#define SAA7134_BOARD_RTD_VFG7350 72
#define SAA7134_BOARD_RTD_VFG7330 73
#define SAA7134_BOARD_FLYTVPLATINUM_MINI2 74
#define SAA7134_BOARD_AVERMEDIA_AVERTVHD_A180 75
#define SAA7134_BOARD_MONSTERTV_MOBILE 76
#define SAA7134_BOARD_PINNACLE_PCTV_110i 77
#define SAA7134_BOARD_ASUSTeK_P7131_DUAL 78
#define SAA7134_BOARD_SEDNA_PC_TV_CARDBUS     79
#define SAA7134_BOARD_ASUSTEK_DIGIMATRIX_TV 80
#define SAA7134_BOARD_PHILIPS_TIGER  81
#define SAA7134_BOARD_MSI_TVATANYWHERE_PLUS  82

```

And the tuner # can be found from include/media/tuner.h
```

#define TUNER_TEMIC_PAL			0        /* 4002 FH5 (3X 7756, 9483) */
#define TUNER_PHILIPS_PAL_I		1
#define TUNER_PHILIPS_NTSC		2
#define TUNER_PHILIPS_SECAM		3	/* you must actively select B/G, L, L` */

#define TUNER_ABSENT			4
#define TUNER_PHILIPS_PAL		5
#define TUNER_TEMIC_NTSC		6	/* 4032 FY5 (3X 7004, 9498, 9789)  */
#define TUNER_TEMIC_PAL_I		7	/* 4062 FY5 (3X 8501, 9957) */

#define TUNER_TEMIC_4036FY5_NTSC	8	/* 4036 FY5 (3X 1223, 1981, 7686) */
#define TUNER_ALPS_TSBH1_NTSC		9
#define TUNER_ALPS_TSBE1_PAL		10
#define TUNER_ALPS_TSBB5_PAL_I		11

#define TUNER_ALPS_TSBE5_PAL		12
#define TUNER_ALPS_TSBC5_PAL		13
#define TUNER_TEMIC_4006FH5_PAL		14	/* 4006 FH5 (3X 9500, 9501, 7291) */
#define TUNER_ALPS_TSHC6_NTSC		15

#define TUNER_TEMIC_PAL_DK		16	/* 4016 FY5 (3X 1392, 1393) */
#define TUNER_PHILIPS_NTSC_M		17
#define TUNER_TEMIC_4066FY5_PAL_I	18	/* 4066 FY5 (3X 7032, 7035) */
#define TUNER_TEMIC_4006FN5_MULTI_PAL	19	/* B/G, I and D/K autodetected (3X 7595, 7606, 7657) */

#define TUNER_TEMIC_4009FR5_PAL		20	/* incl. FM radio (3X 7607, 7488, 7711) */
#define TUNER_TEMIC_4039FR5_NTSC	21	/* incl. FM radio (3X 7246, 7578, 7732) */
#define TUNER_TEMIC_4046FM5		22	/* you must actively select B/G, D/K, I, L, L` !  (3X 7804, 7806, 8103, 8104) */
#define TUNER_PHILIPS_PAL_DK		23

#define TUNER_PHILIPS_FQ1216ME		24	/* you must actively select B/G/D/K, I, L, L` */
#define TUNER_LG_PAL_I_FM		25
#define TUNER_LG_PAL_I			26
#define TUNER_LG_NTSC_FM		27

#define TUNER_LG_PAL_FM			28
#define TUNER_LG_PAL			29
#define TUNER_TEMIC_4009FN5_MULTI_PAL_FM 30	/* B/G, I and D/K autodetected (3X 8155, 8160, 8163) */
#define TUNER_SHARP_2U5JF5540_NTSC	31

#define TUNER_Samsung_PAL_TCPM9091PD27	32
#define TUNER_MT2032			33
#define TUNER_TEMIC_4106FH5		34	/* 4106 FH5 (3X 7808, 7865) */
#define TUNER_TEMIC_4012FY5		35	/* 4012 FY5 (3X 0971, 1099) */

#define TUNER_TEMIC_4136FY5		36	/* 4136 FY5 (3X 7708, 7746) */
#define TUNER_LG_PAL_NEW_TAPC		37
#define TUNER_PHILIPS_FM1216ME_MK3	38
#define TUNER_LG_NTSC_NEW_TAPC		39

#define TUNER_HITACHI_NTSC		40
#define TUNER_PHILIPS_PAL_MK		41
#define TUNER_PHILIPS_ATSC		42
#define TUNER_PHILIPS_FM1236_MK3	43

#define TUNER_PHILIPS_4IN1		44	/* ATI TV Wonder Pro - Conexant */
/* Microtune mergeged with Temic 12/31/1999 partially financed by Alps - these may be similar to Temic */
#define TUNER_MICROTUNE_4049FM5 	45
#define TUNER_MICROTUNE_4042_FI5	46
#define TUNER_LG_NTSC_TAPE		47

#define TUNER_TNF_8831BGFF		48
#define TUNER_MICROTUNE_4042FI5		49	/* DViCO FusionHDTV 3 Gold-Q - 4042 FI5 (3X 8147) */
#define TUNER_TCL_2002N			50
#define TUNER_PHILIPS_FM1256_IH3	51

#define TUNER_THOMSON_DTT7610		52
#define TUNER_PHILIPS_FQ1286		53
#define TUNER_PHILIPS_TDA8290		54
#define TUNER_TCL_2002MB		55	/* Hauppauge PVR-150 PAL */

#define TUNER_PHILIPS_FQ1216AME_MK4	56	/* Hauppauge PVR-150 PAL */
#define TUNER_PHILIPS_FQ1236A_MK4	57	/* Hauppauge PVR-500MCE NTSC */
#define TUNER_YMEC_TVF_8531MF		58
#define TUNER_YMEC_TVF_5533MF		59	/* Pixelview Pro Ultra NTSC */

#define TUNER_THOMSON_DTT7611		60	/* DViCO FusionHDTV 3 Gold-T */
#define TUNER_TENA_9533_DI		61
#define TUNER_TEA5767			62	/* Only FM Radio Tuner */
#define TUNER_PHILIPS_FMD1216ME_MK3	63

#define TUNER_LG_TDVS_H062F		64	/* DViCO FusionHDTV 5 */
#define TUNER_YMEC_TVF66T5_B_DFF	65	/* Acorp Y878F */
#define TUNER_LG_NTSC_TALN_MINI		66
#define TUNER_PHILIPS_TD1316		67

#define TUNER_PHILIPS_TUV1236D		68	/* ATI HDTV Wonder */
#define TUNER_TNF_5335MF                69	/* Sabrent Bt848   */

```

For example, my card shows up via lspci as:
```

0000:02:02.0 Multimedia controller: Philips Semiconductors SAA7134 (rev 01)

```

But I know it's actually a cheapo VStream expert jobby, so:
```

#define SAA7134_BOARD_KWORLD_VSTREAM_XPERT 59

```

The autodetected tuner by the saa7134 module is wrong for this card # and via guess work I know it to be 
```

#define TUNER_TENA_9533_DI		61

```

So telling saa7134 can be done via the command line for testing and then via a modprobe file for when it works, like so:
```

sudo modprobe -r saa7134 tuner # remove any existing modules
sudo modprobe saa7134 card=59 tuner=61 # insert module again

```

And then do 
```

dmesg | grep saa7134

```

You should get output like this:
```

saa7134[0]: found at 0000:02:02.0, rev: 1, irq: 16, latency: 32, mmio: 0xff9ffc00
saa7134[0]: subsystem: 17de:7124, board: Kworld/Tevion V-Stream Xpert TV PVR7134 [card=59,insmod option]
saa7134[0]: board init: gpio is 40407f
input: saa7134 IR (Kworld/Tevion V-Str as /class/input/input2
saa7134[0]: i2c eeprom 00: de 17 24 71 10 28 ff ff ff ff ff ff ff ff ff ff
saa7134[0]: i2c eeprom 10: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
saa7134[0]: i2c eeprom 20: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
saa7134[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
saa7134[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
saa7134[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
saa7134[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
saa7134[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
tuner 0-0060: chip found @ 0xc0 (saa7134[0])
tuner 0-0061: chip found @ 0xc2 (saa7134[0])
saa7134[0]: registered device video0 [v4l2]
saa7134[0]: registered device vbi0
saa7134[0]: registered device radio0
saa7134 IR (Kworld/Tevion V-Str: unknown key: key=0x03 raw=0x03 down=1

```

When you have found a working card # plus tuner # combo that works via tvtime, etc -- you can create a modprobe.d file which auto loads your cards configuration even if you do:
```

sudo modprobe saa7134

```

And to do that:
```

sudo gedit /etc/modprobe.d/saa7134

```
then insert
```

options saa7134 card=# tuner=#

```

---

