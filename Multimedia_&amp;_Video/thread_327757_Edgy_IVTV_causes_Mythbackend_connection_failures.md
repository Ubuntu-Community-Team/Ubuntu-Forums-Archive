---
title: "Edgy IVTV causes Mythbackend connection failures"
date: 2006-12-29
forum: Multimedia &amp; Video
---

### Post by davidl on 2006-12-29
I upgrade my system to Edgy and along the way I updated my mythtv to .20 and installed ivtv as per these instructions:

[https://help.ubuntu.com/community/Install_IVTV_Edgy](https://help.ubuntu.com/community/Install_IVTV_Edgy)

now if I load the ivtv module and then start mythbackend it seems to start ok (no erros int he logs), but it doesn't listen on any ports , which of course prevents the frontend from working properly. I can manually capture video by using cat on the /dev/videop interface so I know that ivtv is working in that regard.

If I unload the ivtv drivers the backend listens on the 6543 & 6544, the frontend connects just fine, but of course now I don't have any tuner cards working.

I don't see any errors anywhere in the logs.

dmesg IVTV startup:


[42960280.320000] ivtv:  ==================== START INIT IVTV ====================
[42960280.320000] ivtv:  version 0.7.0 (tagged release) loading
[42960280.320000] ivtv:  Linux version: 2.6.17-10-server SMP mod_unload 686 REGPARM gcc-4.1
[42960280.320000] ivtv:  In case of problems please include the debug info between
[42960280.320000] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[42960280.320000] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[42960280.320000] ivtv0: Autodetected Hauppauge WinTV PVR-150 card (cx23416 based)
[42960280.320000] ACPI: PCI Interrupt 0000:02:08.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[42960280.370000] tuner 1-0060: TEA5767 detected.
[42960280.370000] tuner 1-0060: chip found @ 0xc0 (ivtv i2c driver #0)
[42960280.370000] tuner 1-0060: type set to 62 (Philips TEA5767HN FM Radio)
[42960280.370000] tuner 1-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[42960280.550000] cx25840 1-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
[42960284.050000] cx25840 1-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[42960284.120000] wm8775 1-001b: chip found @ 0x36 (ivtv i2c driver #0)
[42960284.180000] tveeprom 1-0050: Hauppauge model 23552, rev D487, serial# 8921718
[42960284.180000] tveeprom 1-0050: tuner model is Samsung TCPN 2121P30A (idx 87, type 70)
[42960284.180000] tveeprom 1-0050: TV standards NTSC(M) (eeprom 0x08)
[42960284.180000] tveeprom 1-0050: second tuner model is Philips TEA5768HL FM Radio (idx 101, type 62)
[42960284.180000] tveeprom 1-0050: audio processor is CX25843 (idx 37)
[42960284.180000] tveeprom 1-0050: decoder processor is CX25843 (idx 30)
[42960284.180000] tveeprom 1-0050: has radio, has no IR remote
[42960284.180000] ivtv0: This is the first unit of a PVR500
[42960284.920000] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[42960285.140000] ivtv0: Encoder revision: 0x02050032
[42960285.140000] ivtv0: Allocate DMA encoder MPEG stream: 128 x 32768 buffers (4096KB total)
[42960285.140000] ivtv0: Allocate DMA encoder YUV stream: 194 x 10800 buffers (2048KB total)
[42960285.140000] ivtv0: Allocate DMA encoder VBI stream: 120 x 17472 buffers (2048KB total)
[42960285.140000] ivtv0: Allocate DMA encoder PCM audio stream: 455 x 4608 buffers (2048KB total)
[42960285.140000] ivtv0: Create encoder radio stream
[42960285.140000] tuner 1-0061: type set to 70 (Samsung TCPN 2121P30A)
[42960285.260000] ivtv0: Initialized WinTV PVR 500 (unit #1), card #0
[42960285.260000] ivtv:  ======================  NEXT CARD  ======================
[42960285.260000] ivtv1: Autodetected Hauppauge WinTV PVR-150 card (cx23416 based)
[42960285.270000] ACPI: PCI Interrupt 0000:02:09.0[A] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[42960285.320000] tuner 2-0061: chip found @ 0xc2 (ivtv i2c driver #1)
[42960285.510000] cx25840 2-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #1)
[42960289.000000] cx25840 2-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[42960289.070000] wm8775 2-001b: chip found @ 0x36 (ivtv i2c driver #1)
[42960289.130000] tveeprom 2-0050: Hauppauge model 23552, rev D487, serial# 8921718
[42960289.130000] tveeprom 2-0050: tuner model is Samsung TCPN 2121P30A (idx 87, type 70)
[42960289.130000] tveeprom 2-0050: TV standards NTSC(M) (eeprom 0x08)
[42960289.130000] tveeprom 2-0050: second tuner model is Philips TEA5768HL FM Radio (idx 101, type 62)
[42960289.130000] tveeprom 2-0050: audio processor is CX25843 (idx 37)
[42960289.130000] tveeprom 2-0050: decoder processor is CX25843 (idx 30)
[42960289.130000] tveeprom 2-0050: has radio, has no IR remote
[42960289.130000] ivtv1: This is the second unit of a PVR500
[42960289.130000] ivtv1: Correcting tveeprom data: no radio present on second unit
[42960289.860000] ivtv1: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[42960290.080000] ivtv1: Encoder revision: 0x02050032
[42960290.080000] ivtv1: Allocate DMA encoder MPEG stream: 128 x 32768 buffers (4096KB total)
[42960290.080000] ivtv1: Allocate DMA encoder YUV stream: 194 x 10800 buffers (2048KB total)
[42960290.080000] ivtv1: Allocate DMA encoder VBI stream: 120 x 17472 buffers (2048KB total)
[42960290.080000] ivtv1: Allocate DMA encoder PCM audio stream: 455 x 4608 buffers (2048KB total)
[42960290.080000] tuner 2-0061: type set to 70 (Samsung TCPN 2121P30A)
[42960290.200000] ivtv1: Initialized WinTV PVR 500 (unit #2), card #1
[42960290.200000] ivtv:  ====================  END INIT IVTV  ====================

mythbackend log:

2006-12-29 15:43:05.569 Using runtime prefix = /usr
2006-12-29 15:43:05.623 New DB connection, total: 1
2006-12-29 15:43:05.632 Connected to database 'mythconverg' at host: localhost
2006-12-29 15:43:05.648 Current Schema Version: 1160
Starting up as the master server.
2006-12-29 15:43:05.659 New DB connection, total: 2
2006-12-29 15:43:05.661 Connected to database 'mythconverg' at host: localhost
2006-12-29 15:43:05.665 EITHelper: localtime offset -8:00:00
2006-12-29 15:43:05.671 New DB connection, total: 3
2006-12-29 15:43:05.673 Connected to database 'mythconverg' at host: localhost
2006-12-29 15:43:05.695 EITHelper: localtime offset -8:00:00



-David

---

### Post by superm1 on 2007-01-01
> **davidl said:**
> I upgrade my system to Edgy and along the way I updated my mythtv to .20 and installed ivtv as per these instructions:

[https://help.ubuntu.com/community/Install_IVTV_Edgy](https://help.ubuntu.com/community/Install_IVTV_Edgy)

now if I load the ivtv module and then start mythbackend it seems to start ok (no erros int he logs), but it doesn't listen on any ports , which of course prevents the frontend from working properly. I can manually capture video by using cat on the /dev/videop interface so I know that ivtv is working in that regard.

If I unload the ivtv drivers the backend listens on the 6543 & 6544, the frontend connects just fine, but of course now I don't have any tuner cards working.

I don't see any errors anywhere in the logs.

dmesg IVTV startup:


[42960280.320000] ivtv:  ==================== START INIT IVTV ====================
[42960280.320000] ivtv:  version 0.7.0 (tagged release) loading
[42960280.320000] ivtv:  Linux version: 2.6.17-10-server SMP mod_unload 686 REGPARM gcc-4.1
[42960280.320000] ivtv:  In case of problems please include the debug info between
[42960280.320000] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[42960280.320000] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[42960280.320000] ivtv0: Autodetected Hauppauge WinTV PVR-150 card (cx23416 based)
[42960280.320000] ACPI: PCI Interrupt 0000:02:08.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[42960280.370000] tuner 1-0060: TEA5767 detected.
[42960280.370000] tuner 1-0060: chip found @ 0xc0 (ivtv i2c driver #0)
[42960280.370000] tuner 1-0060: type set to 62 (Philips TEA5767HN FM Radio)
[42960280.370000] tuner 1-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[42960280.550000] cx25840 1-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
[42960284.050000] cx25840 1-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[42960284.120000] wm8775 1-001b: chip found @ 0x36 (ivtv i2c driver #0)
[42960284.180000] tveeprom 1-0050: Hauppauge model 23552, rev D487, serial# 8921718
[42960284.180000] tveeprom 1-0050: tuner model is Samsung TCPN 2121P30A (idx 87, type 70)
[42960284.180000] tveeprom 1-0050: TV standards NTSC(M) (eeprom 0x08)
[42960284.180000] tveeprom 1-0050: second tuner model is Philips TEA5768HL FM Radio (idx 101, type 62)
[42960284.180000] tveeprom 1-0050: audio processor is CX25843 (idx 37)
[42960284.180000] tveeprom 1-0050: decoder processor is CX25843 (idx 30)
[42960284.180000] tveeprom 1-0050: has radio, has no IR remote
[42960284.180000] ivtv0: This is the first unit of a PVR500
[42960284.920000] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[42960285.140000] ivtv0: Encoder revision: 0x02050032
[42960285.140000] ivtv0: Allocate DMA encoder MPEG stream: 128 x 32768 buffers (4096KB total)
[42960285.140000] ivtv0: Allocate DMA encoder YUV stream: 194 x 10800 buffers (2048KB total)
[42960285.140000] ivtv0: Allocate DMA encoder VBI stream: 120 x 17472 buffers (2048KB total)
[42960285.140000] ivtv0: Allocate DMA encoder PCM audio stream: 455 x 4608 buffers (2048KB total)
[42960285.140000] ivtv0: Create encoder radio stream
[42960285.140000] tuner 1-0061: type set to 70 (Samsung TCPN 2121P30A)
[42960285.260000] ivtv0: Initialized WinTV PVR 500 (unit #1), card #0
[42960285.260000] ivtv:  ======================  NEXT CARD  ======================
[42960285.260000] ivtv1: Autodetected Hauppauge WinTV PVR-150 card (cx23416 based)
[42960285.270000] ACPI: PCI Interrupt 0000:02:09.0[A] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[42960285.320000] tuner 2-0061: chip found @ 0xc2 (ivtv i2c driver #1)
[42960285.510000] cx25840 2-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #1)
[42960289.000000] cx25840 2-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[42960289.070000] wm8775 2-001b: chip found @ 0x36 (ivtv i2c driver #1)
[42960289.130000] tveeprom 2-0050: Hauppauge model 23552, rev D487, serial# 8921718
[42960289.130000] tveeprom 2-0050: tuner model is Samsung TCPN 2121P30A (idx 87, type 70)
[42960289.130000] tveeprom 2-0050: TV standards NTSC(M) (eeprom 0x08)
[42960289.130000] tveeprom 2-0050: second tuner model is Philips TEA5768HL FM Radio (idx 101, type 62)
[42960289.130000] tveeprom 2-0050: audio processor is CX25843 (idx 37)
[42960289.130000] tveeprom 2-0050: decoder processor is CX25843 (idx 30)
[42960289.130000] tveeprom 2-0050: has radio, has no IR remote
[42960289.130000] ivtv1: This is the second unit of a PVR500
[42960289.130000] ivtv1: Correcting tveeprom data: no radio present on second unit
[42960289.860000] ivtv1: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[42960290.080000] ivtv1: Encoder revision: 0x02050032
[42960290.080000] ivtv1: Allocate DMA encoder MPEG stream: 128 x 32768 buffers (4096KB total)
[42960290.080000] ivtv1: Allocate DMA encoder YUV stream: 194 x 10800 buffers (2048KB total)
[42960290.080000] ivtv1: Allocate DMA encoder VBI stream: 120 x 17472 buffers (2048KB total)
[42960290.080000] ivtv1: Allocate DMA encoder PCM audio stream: 455 x 4608 buffers (2048KB total)
[42960290.080000] tuner 2-0061: type set to 70 (Samsung TCPN 2121P30A)
[42960290.200000] ivtv1: Initialized WinTV PVR 500 (unit #2), card #1
[42960290.200000] ivtv:  ====================  END INIT IVTV  ====================

mythbackend log:

2006-12-29 15:43:05.569 Using runtime prefix = /usr
2006-12-29 15:43:05.623 New DB connection, total: 1
2006-12-29 15:43:05.632 Connected to database 'mythconverg' at host: localhost
2006-12-29 15:43:05.648 Current Schema Version: 1160
Starting up as the master server.
2006-12-29 15:43:05.659 New DB connection, total: 2
2006-12-29 15:43:05.661 Connected to database 'mythconverg' at host: localhost
2006-12-29 15:43:05.665 EITHelper: localtime offset -8:00:00
2006-12-29 15:43:05.671 New DB connection, total: 3
2006-12-29 15:43:05.673 Connected to database 'mythconverg' at host: localhost
2006-12-29 15:43:05.695 EITHelper: localtime offset -8:00:00



-David
Hi David,

Did you perhaps accidentally choose the wrong type of device in mythtv-setup?  The Hauppauge cards do require that you choose the PVR-XXX type in mythtv-setup rather then 'Analog V4L Card'.

---

### Post by davidl on 2007-01-09
doesn't seem to be the case, as soon as I load the ivtv modules  mythbackend just stops listening on the ports.

I'm pretty much at a loss

---

### Post by superm1 on 2007-01-09
> **davidl said:**
> doesn't seem to be the case, as soon as I load the ivtv modules  mythbackend just stops listening on the ports.

I'm pretty much at a loss

Take a look at /etc/default/mythtv-backend.  You can add some debugging options to further determine what the cause of the problem is when mythbackend is started.

You are starting it from the init scripts correct?
```
sudo /etc/init.d/mythtv-backend start
```

If you attempt to start it by just
```
mythbackend&
```

Then this is a matter of permissions most likely

---

### Post by clas on 2007-05-18
I had the same problem when removing my NOVA-T from the tuner card list in mythtv-setup.

I added it again. Then is had mistaken one of the tuners in the PVR-500 for the NOVA-T card. I corrected that problem too, and got mythbackend to listen to port 6543 again.

/Claus

> **davidl said:**
> I upgrade my system to Edgy and along the way I updated my mythtv to .20 and installed ivtv as per these instructions:

[https://help.ubuntu.com/community/Install_IVTV_Edgy](https://help.ubuntu.com/community/Install_IVTV_Edgy)

now if I load the ivtv module and then start mythbackend it seems to start ok (no erros int he logs), but it doesn't listen on any ports , which of course prevents the frontend from working properly. I can manually capture video by using cat on the /dev/videop interface so I know that ivtv is working in that regard.

If I unload the ivtv drivers the backend listens on the 6543 & 6544, the frontend connects just fine, but of course now I don't have any tuner cards working.

I don't see any errors anywhere in the logs.

dmesg IVTV startup:


[42960280.320000] ivtv:  ==================== START INIT IVTV ====================
[42960280.320000] ivtv:  version 0.7.0 (tagged release) loading
[42960280.320000] ivtv:  Linux version: 2.6.17-10-server SMP mod_unload 686 REGPARM gcc-4.1
[42960280.320000] ivtv:  In case of problems please include the debug info between
[42960280.320000] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[42960280.320000] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[42960280.320000] ivtv0: Autodetected Hauppauge WinTV PVR-150 card (cx23416 based)
[42960280.320000] ACPI: PCI Interrupt 0000:02:08.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[42960280.370000] tuner 1-0060: TEA5767 detected.
[42960280.370000] tuner 1-0060: chip found @ 0xc0 (ivtv i2c driver #0)
[42960280.370000] tuner 1-0060: type set to 62 (Philips TEA5767HN FM Radio)
[42960280.370000] tuner 1-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[42960280.550000] cx25840 1-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
[42960284.050000] cx25840 1-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[42960284.120000] wm8775 1-001b: chip found @ 0x36 (ivtv i2c driver #0)
[42960284.180000] tveeprom 1-0050: Hauppauge model 23552, rev D487, serial# 8921718
[42960284.180000] tveeprom 1-0050: tuner model is Samsung TCPN 2121P30A (idx 87, type 70)
[42960284.180000] tveeprom 1-0050: TV standards NTSC(M) (eeprom 0x08)
[42960284.180000] tveeprom 1-0050: second tuner model is Philips TEA5768HL FM Radio (idx 101, type 62)
[42960284.180000] tveeprom 1-0050: audio processor is CX25843 (idx 37)
[42960284.180000] tveeprom 1-0050: decoder processor is CX25843 (idx 30)
[42960284.180000] tveeprom 1-0050: has radio, has no IR remote
[42960284.180000] ivtv0: This is the first unit of a PVR500
[42960284.920000] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[42960285.140000] ivtv0: Encoder revision: 0x02050032
[42960285.140000] ivtv0: Allocate DMA encoder MPEG stream: 128 x 32768 buffers (4096KB total)
[42960285.140000] ivtv0: Allocate DMA encoder YUV stream: 194 x 10800 buffers (2048KB total)
[42960285.140000] ivtv0: Allocate DMA encoder VBI stream: 120 x 17472 buffers (2048KB total)
[42960285.140000] ivtv0: Allocate DMA encoder PCM audio stream: 455 x 4608 buffers (2048KB total)
[42960285.140000] ivtv0: Create encoder radio stream
[42960285.140000] tuner 1-0061: type set to 70 (Samsung TCPN 2121P30A)
[42960285.260000] ivtv0: Initialized WinTV PVR 500 (unit #1), card #0
[42960285.260000] ivtv:  ======================  NEXT CARD  ======================
[42960285.260000] ivtv1: Autodetected Hauppauge WinTV PVR-150 card (cx23416 based)
[42960285.270000] ACPI: PCI Interrupt 0000:02:09.0[A] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[42960285.320000] tuner 2-0061: chip found @ 0xc2 (ivtv i2c driver #1)
[42960285.510000] cx25840 2-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #1)
[42960289.000000] cx25840 2-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[42960289.070000] wm8775 2-001b: chip found @ 0x36 (ivtv i2c driver #1)
[42960289.130000] tveeprom 2-0050: Hauppauge model 23552, rev D487, serial# 8921718
[42960289.130000] tveeprom 2-0050: tuner model is Samsung TCPN 2121P30A (idx 87, type 70)
[42960289.130000] tveeprom 2-0050: TV standards NTSC(M) (eeprom 0x08)
[42960289.130000] tveeprom 2-0050: second tuner model is Philips TEA5768HL FM Radio (idx 101, type 62)
[42960289.130000] tveeprom 2-0050: audio processor is CX25843 (idx 37)
[42960289.130000] tveeprom 2-0050: decoder processor is CX25843 (idx 30)
[42960289.130000] tveeprom 2-0050: has radio, has no IR remote
[42960289.130000] ivtv1: This is the second unit of a PVR500
[42960289.130000] ivtv1: Correcting tveeprom data: no radio present on second unit
[42960289.860000] ivtv1: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[42960290.080000] ivtv1: Encoder revision: 0x02050032
[42960290.080000] ivtv1: Allocate DMA encoder MPEG stream: 128 x 32768 buffers (4096KB total)
[42960290.080000] ivtv1: Allocate DMA encoder YUV stream: 194 x 10800 buffers (2048KB total)
[42960290.080000] ivtv1: Allocate DMA encoder VBI stream: 120 x 17472 buffers (2048KB total)
[42960290.080000] ivtv1: Allocate DMA encoder PCM audio stream: 455 x 4608 buffers (2048KB total)
[42960290.080000] tuner 2-0061: type set to 70 (Samsung TCPN 2121P30A)
[42960290.200000] ivtv1: Initialized WinTV PVR 500 (unit #2), card #1
[42960290.200000] ivtv:  ====================  END INIT IVTV  ====================

mythbackend log:

2006-12-29 15:43:05.569 Using runtime prefix = /usr
2006-12-29 15:43:05.623 New DB connection, total: 1
2006-12-29 15:43:05.632 Connected to database 'mythconverg' at host: localhost
2006-12-29 15:43:05.648 Current Schema Version: 1160
Starting up as the master server.
2006-12-29 15:43:05.659 New DB connection, total: 2
2006-12-29 15:43:05.661 Connected to database 'mythconverg' at host: localhost
2006-12-29 15:43:05.665 EITHelper: localtime offset -8:00:00
2006-12-29 15:43:05.671 New DB connection, total: 3
2006-12-29 15:43:05.673 Connected to database 'mythconverg' at host: localhost
2006-12-29 15:43:05.695 EITHelper: localtime offset -8:00:00



-David

---

