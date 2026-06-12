---
title: "No sound after upgrade from Gutsy to Hardy"
date: 2008-05-21
forum: Mythbuntu
---

### Post by pcglue on 2008-05-21
After upgrading to Hardy, there's no sound in my MythTV recordings anymore, nor is there sound when watching live tv.  

When I do "cat /dev/video0 > test.mpg", there's no sound in test.mpg when played on another computer.  When playing recordings from before the upgrade, the sound is there like normal.

After the upgrade, I'm using kernel 2.6.24-16-generic, mythtv 0.21.0+fixes16838-0ubuntu3 and ivtv 1.1.0.  I'm using a Hauppauge PVR-350 and using the TV-out on it.

Does anyone know what's wrong?  Below is ivtv output from dmesg. 

Thanks for your help!

```

[   27.923522] ivtv:  Start initialization, version 1.1.0
[   27.923629] ivtv0: Initializing card #0
[   27.923633] ivtv0: Autodetected Hauppauge card (cx23415 based)
[   27.950994] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
[   27.951006] ACPI: PCI Interrupt 0000:01:06.0[A] -> Link [APC2] -> GSI 17 (level, low) -> IRQ 20
[   27.989441] wlan: 0.9.4
[   28.035646] ath_pci: 0.9.4
[   28.122045] tveeprom 2-0050: Hauppauge model 48132, rev K268, serial# 9945181
[   28.122050] tveeprom 2-0050: tuner model is LG TAPE H001F MK3 (idx 68, type 47)
[   28.122053] tveeprom 2-0050: TV standards NTSC(M) (eeprom 0x08)
[   28.122056] tveeprom 2-0050: audio processor is MSP4448 (idx 27)
[   28.122058] tveeprom 2-0050: decoder processor is SAA7115 (idx 19)
[   28.122060] tveeprom 2-0050: has radio, has IR receiver, has no IR transmitter
[   28.122063] ivtv0: Autodetected Hauppauge WinTV PVR-350
[   28.428808] tuner 2-0043: chip found @ 0x86 (ivtv i2c driver #0)
[   28.428828] tda9887 2-0043: tda988[5/6/7] found @ 0x43 (tuner)
[   28.428831] tuner 2-0043: type set to tda9887
[   28.431793] tuner 2-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   28.556557] saa7115 2-0021: saa7115 found (1f7115d0e100000) @ 0x42 (ivtv i2c driver #0)
[   29.275868] parport_pc 00:09: reported by Plug and Play ACPI
[   29.275920] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   29.348778] saa7127 2-0044: saa7129 found @ 0x88 (ivtv i2c driver #0)
[   29.381224] msp3400 2-0040: MSP4448G-A2 found @ 0x80 (ivtv i2c driver #0)
[   29.381228] msp3400 2-0040: MSP4448G-A2 supports radio, mode is autodetect and autoselect
[   29.381021] tuner-simple 2-0061: type set to 47 (LG NTSC (TAPE series))
[   29.381026] tuner 2-0061: type set to LG NTSC (TAPE serie
[   29.390693] ivtv0: Registered device video0 for encoder MPG (4096 kB)
[   29.390709] ivtv0: Registered device video32 for encoder YUV (2048 kB)
[   29.390724] ivtv0: Registered device vbi0 for encoder VBI (1024 kB)
[   29.390739] ivtv0: Registered device video24 for encoder PCM (320 kB)
[   29.390754] ivtv0: Registered device radio0 for encoder radio
[   29.390859] ivtv0: Registered device video16 for decoder MPG (1024 kB)
[   29.390874] ivtv0: Registered device vbi8 for decoder VBI (64 kB)
[   29.390889] ivtv0: Registered device vbi16 for decoder VOUT
[   29.390905] ivtv0: Registered device video48 for decoder YUV (1024 kB)
[   29.390907] ivtv0: Initialized card #0: Hauppauge WinTV PVR-350
[   29.390924] ivtv:  End initialization
[   31.830094] ivtv0: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
[   31.858921] ivtv0: Loaded v4l-cx2341x-dec.fw firmware (262144 bytes)
[   32.055777] ivtv0: Encoder revision: 0x02060039
[   32.055898] ivtv0: Decoder revision: 0x02020023
[   32.146709] ivtv0: Loaded v4l-cx2341x-init.mpg firmware (155648 bytes)
[   32.335012] ivtvfb0: Framebuffer at 0xed510000, mapped to 0xfa810000, size 1665k
[   32.446826] ivtvfb0: Framebuffer registered on ivtv card id 0

```

---

### Post by TheOtherShoe on 2008-05-28
It might be an issue with the switch in Hardy from ESD to PulseAudio. I have the same problem; and switching sound playback to ALSA in Gnome Sound Preferences got sound working for me.

I have not found a way to fix PulseAudio yet.

---

### Post by TheOtherShoe on 2008-05-28
I just discovered my problem! I had Gizmo starting up when I logged in, which grabbed the sound thus preventing PulseAudio from using the sound output.

I closed Gizmo, and now my PulseAudio works fine. You may have Gizmo or another program running that is not gstreamer or PulseAudio compatible.

So now I just need to find a way to make Gizmo use PulseAudio.

---

### Post by pcglue on 2008-05-28
I'm not sure that that's my problem.  My soundcard output is fine.   Playing an MPEG that's known to have sound works.  

It's when I'm capturing video from my PVR-350 that there's no corresponding audio.  It's the sound input from my PVR-350 that is no longer working after the upgrade to Hardy.  It was working in Gutsy.

---

