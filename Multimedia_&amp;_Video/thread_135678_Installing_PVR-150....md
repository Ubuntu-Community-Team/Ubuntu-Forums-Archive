---
title: "Installing PVR-150..."
date: 2006-02-24
forum: Multimedia &amp; Video
---

### Post by Sonic-NKT on 2006-02-24
Hi,
im trying to install a pvr-150.
the first time it kind of worked, though i couldnt saw any program.
i restarted the computer and after that the device /dev/video0 was gone and never returned until now.
i reinstalled ivtv but nothing helped..
what can i do now, how can i get this card workind?

dmesg:
[4295205.280000] Linux video capture interface: v1.00
[4295205.299000] ivtv:  ==================== START INIT IVTV ====================
[4295205.299000] ivtv:  version 0.4.3 (tagged release) loading
[4295205.299000] ivtv:  Linux version: 2.6.12-9-386 386 gcc-3.4
[4295205.299000] ivtv:  In case of problems please include the debug info between
[4295205.299000] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[4295205.299000] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[4295205.307000] ivtv:  ====================  END INIT IVTV  ====================

Thanks

---

### Post by Sonic-NKT on 2006-02-24
ok, removed the card and put it back in again... now it gets recognized and /dev/video0 exists again..

dmesg:
[4294703.837000] ivtv:  ==================== START INIT IVTV ====================
[4294703.837000] ivtv:  version 0.4.3 (tagged release) loading
[4294703.837000] ivtv:  Linux version: 2.6.12-9-386 386 gcc-3.4
[4294703.837000] ivtv:  In case of problems please include the debug info between
[4294703.837000] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[4294703.837000] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[4294703.846000] ivtv0: Autodetected WinTV PVR 150 card (cx23416 based)
[4294703.847000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[4294703.847000] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[4294703.933000] tveeprom: ivtv version
[4294703.933000] tveeprom: Hauppauge: model = 26034, rev = C197, serial# = 7765763
[4294703.933000] tveeprom: tuner = TCL 2002MB_3H (idx = 97, type = 55)
[4294703.933000] tveeprom: tuner fmt = PAL(B/G) PAL(D/K) (eeprom = 0x44, v4l2 = 0x00000e07)
[4294703.933000] tveeprom: audio processor = CX25842 (type = 24)
[4294703.933000] tveeprom: decoder processor = CX25842 (type = 1d)
[4294703.933000] ivtv0: i2c attach to card #0 ok [client=tveeprom, addr=50]
[4294703.981000] tuner (ivtv): chip found at addr 0xc2 i2c-bus ivtv i2c driver #0
[4294703.981000] ivtv0: i2c attach to card #0 ok [client=(tuner unset), addr=61]
[4294704.181000] cx25840 1-0044: ivtv driver
[4294704.181000] cx25840 1-0044: cx25842-23 found @ 0x88 (ivtv i2c driver #0)
[4294707.587000] cx25840 1-0044: loaded v4l-cx25840.fw firmware (14264 bytes)
[4294707.652000] ivtv0: i2c attach to card #0 ok [client=cx25840, addr=44]
[4294707.696000] wm8775 1-001b: ivtv driver
[4294707.696000] wm8775 1-001b: chip found @ 0x36 (ivtv i2c driver #0)
[4294707.706000] ivtv0: i2c attach to card #0 ok [client=wm8775, addr=1b]
[4294708.622000] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[4294708.832000] ivtv0: Encoder revision: 0x02050032
[4294708.834000] ivtv0: Allocate DMA encoder MPEG stream: 128 x 32768 buffers (4096KB total)
[4294708.836000] ivtv0: Allocate DMA encoder YUV stream: 161 x 12960 buffers (2048KB total)
[4294708.839000] ivtv0: Allocate DMA encoder VBI stream: 80 x 26208 buffers (2048KB total)
[4294708.841000] ivtv0: Allocate DMA encoder PCM audio stream: 455 x 4608 buffers (2048KB total)
[4294708.842000] tuner: type set to 55 (TCL 2002MB) by ivtv i2c driver #0
[4294709.052000] ivtv0: Initialized WinTV PVR 150, card #0
[4294709.052000] ivtv:  ====================  END INIT IVTV  ====================

but i cant get anything else to work.. i can composite in, but its slow so console games are not playable, tuner doesnt work at all...
can someone help me?

---

### Post by dlai on 2006-05-20
i would recommend you trying this how to.... it is very straight forward [http://hyams.webhop.net/mythtv/myth_ubuntu.html]("http://hyams.webhop.net/mythtv/myth_ubuntu.html")... If you need a tv-app afterwards... you can use mythtv or else try xawtv by following this link [http://ubuntuforums.org/showthread.php?t=179191]("http://ubuntuforums.org/showthread.php?t=179191")

---

