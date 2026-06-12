---
title: "PVR-350 doesn't record sound after upgrade to Hardy"
date: 2008-05-23
forum: Mythbuntu
---

### Post by pcglue on 2008-05-23
I'm using MythTV with a Hauppauge PVR-350. Immediately after upgrading to Hardy Heron (kernel 2.6.24-16, ivtv 1.1.0, mythtv 0.21.0), there's no sound in my recordings anymore, nor is there sound when watching live tv. Everything was working fine in Gutsy Gibbon (using ivtv 1.0.0).

When I do "cat /dev/video0 > test.mpg", the video is fine, but there's no sound in test.mpg, even when played on another known working computer. When playing recordings from before the upgrade, the sound is there like normal.

Does anyone know what's wrong? Below is the ivtv output from dmesg. What other logs can I look at to troubleshoot the problem?

Thanks for your help!


```
[ 27.923522] ivtv: Start initialization, version 1.1.0
[ 27.923629] ivtv0: Initializing card #0
[ 27.923633] ivtv0: Autodetected Hauppauge card (cx23415 based)
[ 27.950994] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
[ 27.951006] ACPI: PCI Interrupt 0000:01:06.0[A] -> Link [APC2] -> GSI 17 (level, low) -> IRQ 20
[ 27.989441] wlan: 0.9.4
[ 28.035646] ath_pci: 0.9.4
[ 28.122045] tveeprom 2-0050: Hauppauge model 48132, rev K268, serial# 9945181
[ 28.122050] tveeprom 2-0050: tuner model is LG TAPE H001F MK3 (idx 68, type 47)
[ 28.122053] tveeprom 2-0050: TV standards NTSC(M) (eeprom 0x08)
[ 28.122056] tveeprom 2-0050: audio processor is MSP4448 (idx 27)
[ 28.122058] tveeprom 2-0050: decoder processor is SAA7115 (idx 19)
[ 28.122060] tveeprom 2-0050: has radio, has IR receiver, has no IR transmitter
[ 28.122063] ivtv0: Autodetected Hauppauge WinTV PVR-350
[ 28.428808] tuner 2-0043: chip found @ 0x86 (ivtv i2c driver #0)
[ 28.428828] tda9887 2-0043: tda988[5/6/7] found @ 0x43 (tuner)
[ 28.428831] tuner 2-0043: type set to tda9887
[ 28.431793] tuner 2-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[ 28.556557] saa7115 2-0021: saa7115 found (1f7115d0e100000) @ 0x42 (ivtv i2c driver #0)
[ 29.275868] parport_pc 00:09: reported by Plug and Play ACPI
[ 29.275920] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[ 29.348778] saa7127 2-0044: saa7129 found @ 0x88 (ivtv i2c driver #0)
[ 29.381224] msp3400 2-0040: MSP4448G-A2 found @ 0x80 (ivtv i2c driver #0)
[ 29.381228] msp3400 2-0040: MSP4448G-A2 supports radio, mode is autodetect and autoselect
[ 29.381021] tuner-simple 2-0061: type set to 47 (LG NTSC (TAPE series))
[ 29.381026] tuner 2-0061: type set to LG NTSC (TAPE serie
[ 29.390693] ivtv0: Registered device video0 for encoder MPG (4096 kB)
[ 29.390709] ivtv0: Registered device video32 for encoder YUV (2048 kB)
[ 29.390724] ivtv0: Registered device vbi0 for encoder VBI (1024 kB)
[ 29.390739] ivtv0: Registered device video24 for encoder PCM (320 kB)
[ 29.390754] ivtv0: Registered device radio0 for encoder radio
[ 29.390859] ivtv0: Registered device video16 for decoder MPG (1024 kB)
[ 29.390874] ivtv0: Registered device vbi8 for decoder VBI (64 kB)
[ 29.390889] ivtv0: Registered device vbi16 for decoder VOUT
[ 29.390905] ivtv0: Registered device video48 for decoder YUV (1024 kB)
[ 29.390907] ivtv0: Initialized card #0: Hauppauge WinTV PVR-350
[ 29.390924] ivtv: End initialization
[ 31.830094] ivtv0: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
[ 31.858921] ivtv0: Loaded v4l-cx2341x-dec.fw firmware (262144 bytes)
[ 32.055777] ivtv0: Encoder revision: 0x02060039
[ 32.055898] ivtv0: Decoder revision: 0x02020023
[ 32.146709] ivtv0: Loaded v4l-cx2341x-init.mpg firmware (155648 bytes)
[ 32.335012] ivtvfb0: Framebuffer at 0xed510000, mapped to 0xfa810000, size 1665k
[ 32.446826] ivtvfb0: Framebuffer registered on ivtv card id 0

```

---

### Post by pcglue on 2008-05-31
I've confirmed that the audio line going into the PVR-350 is still good and has sound.  Other than that I've been stuck.  Can anyone help?

---

### Post by s_p_a_r_k_y on 2008-06-09
> **pcglue said:**
> I've confirmed that the audio line going into the PVR-350 is still good and has sound.  Other than that I've been stuck.  Can anyone help?

[http://ivtv.writeme.ch/tiki-view_faq.php?faqId=1#q42](http://ivtv.writeme.ch/tiki-view_faq.php?faqId=1#q42) -- but I'm looking for this file or other ways to solve this problem.

---

