---
title: "Hauppauge HVR-950 audio driver fails to load"
date: 2007-09-03
forum: Multimedia &amp; Video
---

### Post by Zyrshnikashnu on 2007-09-03
I'm using a Hauppauge HVR-950 on my Feisty laptop. I installed the v4l dvb drivers using the infamous Lunapark article as a guide. The picture is fine, but the em28xx-audio module fails to load when the tuner is plugged in:

dmesg:
```
[ 7728.472000] usb 7-1: new high speed USB device using ehci_hcd and address 6
[ 7728.608000] usb 7-1: configuration #1 chosen from 1 choice
[ 7728.608000] em28xx new video device (2040:6513): interface 0, class 255
[ 7728.608000] em28xx: device is attached to a USB 2.0 bus
[ 7728.608000] em28xx: you're using the experimental/unstable tree from mcentral.de
[ 7728.608000] em28xx: there's also a stable tree available but which is limited to
[ 7728.608000] em28xx: linux <=2.6.19.2
[ 7728.608000] em28xx: it's fine to use this driver but keep in mind that it will move
[ 7728.608000] em28xx: to http://mcentral.de/hg/~mrec/v4l-dvb-kernel as soon as it's
[ 7728.608000] em28xx: proved to be stable
[ 7728.608000] em28xx #0: Alternate settings: 8
[ 7728.608000] em28xx #0: Alternate setting 0, max size= 0
[ 7728.608000] em28xx #0: Alternate setting 1, max size= 0
[ 7728.608000] em28xx #0: Alternate setting 2, max size= 1448
[ 7728.608000] em28xx #0: Alternate setting 3, max size= 2048
[ 7728.608000] em28xx #0: Alternate setting 4, max size= 2304
[ 7728.608000] em28xx #0: Alternate setting 5, max size= 2580
[ 7728.608000] em28xx #0: Alternate setting 6, max size= 2892
[ 7728.608000] em28xx #0: Alternate setting 7, max size= 3072
[ 7728.992000] attach_inform: eeprom detected.
[ 7729.020000] em28xx #0: i2c eeprom 00: 1a eb 67 95 40 20 13 65 d0 12 5c 03 82 1e 6a 18
[ 7729.020000] em28xx #0: i2c eeprom 10: 00 00 24 57 66 07 01 00 00 00 00 00 00 00 00 00
[ 7729.020000] em28xx #0: i2c eeprom 20: 46 00 01 00 f0 10 02 00 b8 00 00 00 5b 1c 00 00
[ 7729.020000] em28xx #0: i2c eeprom 30: 00 00 20 40 20 80 02 20 01 01 01 01 00 00 00 00
[ 7729.020000] em28xx #0: i2c eeprom 40: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[ 7729.020000] em28xx #0: i2c eeprom 50: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[ 7729.020000] em28xx #0: i2c eeprom 60: 00 00 00 00 00 00 00 00 00 00 18 03 34 00 30 00
[ 7729.020000] em28xx #0: i2c eeprom 70: 32 00 38 00 34 00 34 00 33 00 37 00 38 00 39 00
[ 7729.020000] em28xx #0: i2c eeprom 80: 00 00 1e 03 57 00 69 00 6e 00 54 00 56 00 20 00
[ 7729.020000] em28xx #0: i2c eeprom 90: 48 00 56 00 52 00 2d 00 39 00 38 00 30 00 00 00
[ 7729.020000] em28xx #0: i2c eeprom a0: 84 12 00 00 05 50 1a 7f d4 78 23 b1 fe d0 18 85
[ 7729.020000] em28xx #0: i2c eeprom b0: ff 00 00 00 04 84 0a 00 01 01 20 77 00 40 8d 2c
[ 7729.020000] em28xx #0: i2c eeprom c0: 1d f0 74 02 01 00 01 79 d0 00 00 00 00 00 00 00
[ 7729.020000] em28xx #0: i2c eeprom d0: 84 12 00 00 05 50 1a 7f d4 78 23 b1 fe d0 18 85
[ 7729.020000] em28xx #0: i2c eeprom e0: ff 00 00 00 04 84 0a 00 01 01 20 77 00 40 8d 2c
[ 7729.020000] em28xx #0: i2c eeprom f0: 1d f0 74 02 01 00 01 79 d0 00 00 00 00 00 00 00
[ 7729.020000] EEPROM ID= 0x9567eb1a
[ 7729.020000] Vendor/Product ID= 2040:6513
[ 7729.020000] AC97 audio (5 sample rates)
[ 7729.020000] 500mA max power
[ 7729.020000] Table at 0x24, strings=0x1e82, 0x186a, 0x0000
[ 7729.020000] tveeprom 3-0050: Hauppauge model 65201, rev A1C0, serial# 1911949
[ 7729.020000] tveeprom 3-0050: tuner model is Xceive XC3028 (idx 120, type 71)
[ 7729.020000] tveeprom 3-0050: TV standards PAL(B/G) PAL(I) PAL(D/D1/K) ATSC/DVB Digital (eeprom 0xd4)
[ 7729.020000] tveeprom 3-0050: audio processor is None (idx 0)
[ 7729.020000] tveeprom 3-0050: has radio
[ 7729.024000] tuner 3-0061: chip found @ 0xc2 (em28xx #0)
[ 7729.024000] attach inform (default): detected I2C address c2
[ 7729.024000] /lib/firmware/v4l-dvb-experimental/v4l/tuner-core.c: setting tuner callback
[ 7729.024000] tuner 0x61: Configuration acknowledged
[ 7729.024000] /lib/firmware/v4l-dvb-experimental/v4l/tuner-core.c: setting tuner callback
[ 7729.024000] /lib/firmware/v4l-dvb-experimental/v4l/xc3028-tuner.c: attach request!
[ 7729.024000] /lib/firmware/v4l-dvb-experimental/v4l/tuner-core.c: xc3028 tuner successfully loaded
[ 7729.028000] attach_inform: tvp5150 detected.
[ 7729.096000] tvp5150 3-005c: tvp5150am1 detected.
[ 7729.184000] Loading base firmware: xc3028_init0.i2c.fw
[ 7730.208000] Loading default analogue TV settings: xc3028_BG_PAL_A2_A.i2c.fw
[ 7730.232000] xc3028-tuner.c: firmware 2.7
[ 7730.232000] ANALOG TV REQUEST
[ 7730.240000] em28xx #0: V4L2 device registered as /dev/video0
[ 7730.240000] em2880-dvb.c: DVB Init
[ 7730.240000] Loading base firmware: xc3028_8MHz_init0.i2c.fw
[ 7730.252000] em28xx_audio: disagrees about version of symbol snd_pcm_new
[ 7730.252000] em28xx_audio: Unknown symbol snd_pcm_new
[ 7730.252000] em28xx_audio: disagrees about version of symbol snd_card_register
[ 7730.252000] em28xx_audio: Unknown symbol snd_card_register
[ 7730.252000] em28xx_audio: disagrees about version of symbol snd_card_free
[ 7730.252000] em28xx_audio: Unknown symbol snd_card_free
[ 7730.252000] em28xx_audio: disagrees about version of symbol snd_card_new
[ 7730.252000] em28xx_audio: Unknown symbol snd_card_new
[ 7730.252000] em28xx_audio: disagrees about version of symbol snd_pcm_lib_ioctl
[ 7730.252000] em28xx_audio: Unknown symbol snd_pcm_lib_ioctl
[ 7730.252000] em28xx_audio: disagrees about version of symbol snd_pcm_set_ops
[ 7730.252000] em28xx_audio: Unknown symbol snd_pcm_set_ops
[ 7730.252000] em28xx_audio: disagrees about version of symbol snd_pcm_hw_constraint_integer
[ 7730.252000] em28xx_audio: Unknown symbol snd_pcm_hw_constraint_integer
[ 7730.252000] em28xx_audio: disagrees about version of symbol snd_pcm_period_elapsed
[ 7730.252000] em28xx_audio: Unknown symbol snd_pcm_period_elapsed
[ 7731.448000] Loading default dtv settings: xc3028_DTV8_2633.i2c.fw
[ 7731.468000] xc3028-tuner.c: firmware 2.7
[ 7731.468000] Sending extra call for Digital TV!
[ 7731.572000] /lib/firmware/v4l-dvb-experimental/v4l/xc3028-tuner.c: attach request!
[ 7731.572000] DVB: registering new adapter (em2880 DVB-T)
[ 7731.572000] DVB: registering frontend 0 (LG Electronics LGDT3303 VSB/QAM Frontend)...
[ 7731.572000] em28xx #0: Found Hauppauge WinTV HVR 950
```

modprobe -v em28xx-audio:
```
insmod /lib/modules/2.6.20-16-generic/kernel/drivers/media/video/em28xx/em28xx-audio.ko 
FATAL: Error inserting em28xx_audio (/lib/modules/2.6.20-16-generic/kernel/drivers/media/video/em28xx/em28xx-audio.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```

I've tried both the stable and experimental branches of v4l-dvb, but both yield the same results. I've recompiled several times.

I'm running Feisty 7.04 with kernel 2.6.20-16-generic. Can anyone help me diagnose the issue?

---

