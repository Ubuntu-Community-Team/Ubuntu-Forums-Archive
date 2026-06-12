---
title: "TVTime errors"
date: 2006-06-13
forum: Multimedia &amp; Video
---

### Post by tkman on 2006-06-13
I just installed the IVTV drivers per a few howto posts.  It appears that my card is detected properly.

The results of dmesg:

[PHP][4294689.455000] ivtv:  ==================== START INIT IVTV ====================
[4294689.455000] ivtv:  version 0.4.4 (tagged release) loading
[4294689.455000] ivtv:  Linux version: 2.6.15-23-386 preempt 486 gcc-4.0
[4294689.455000] ivtv:  In case of problems please include the debug info between
[4294689.455000] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[4294689.455000] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[4294689.455000] ivtv0: Autodetected WinTV PVR 150 card (cx23416 based)
[4294689.455000] ACPI: PCI Interrupt 0000:00:0e.0[A] -> GSI 19 (level, low) -> IRQ 209
[4294689.513000] tveeprom: ivtv version
[4294689.513000] tveeprom: Hauppauge: model = 26552, rev = C268, serial# = 8582212
[4294689.513000] tveeprom: tuner = LG TAPE H001F MK3 (idx = 68, type = 47)
[4294689.513000] tveeprom: tuner fmt = NTSC(M) (eeprom = 0x08, v4l2 = 0x00001000)
[4294689.513000] tveeprom: audio processor = CX25843 (type = 25)
[4294689.513000] tveeprom: decoder processor = CX25843 (type = 1e)
[4294689.513000] ivtv0: i2c attach to card #0 ok [client=tveeprom, addr=50]
[4294689.529000] tuner (ivtv): chip found at addr 0xc2 i2c-bus ivtv i2c driver #0
[4294689.529000] ivtv0: i2c attach to card #0 ok [client=(tuner unset), addr=61]
[4294689.928000] codec_read: codec 0 is not valid [0xfe0000]
[4294689.934000] codec_read: codec 0 is not valid [0xfe0000]
[4294689.941000] codec_read: codec 0 is not valid [0xfe0000]
[4294689.947000] codec_read: codec 0 is not valid [0xfe0000]
[4294690.236000] cx25840 1-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
[4294690.815000] skge eth0: enabling interface
[4294690.930000] usbcore: registered new driver hiddev
[4294690.951000] input: Microsoft Microsoft Wireless Optical Desktop 2.10 as /class/input/input1
[4294690.951000] input: USB HID v1.11 Keyboard [Microsoft Microsoft Wireless Optical Desktop 2.10] on usb-0000:00:10.0-1
[4294691.089000] input: Microsoft Microsoft Wireless Optical Desktop 2.10 as /class/input/input2
[4294691.089000] input: USB HID v1.11 Mouse [Microsoft Microsoft Wireless Optical Desktop 2.10] on usb-0000:00:10.0-1
[4294691.089000] usbcore: registered new driver usbhid
[4294691.089000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[4294691.157000] ts: Compaq touchscreen protocol output
[4294691.601000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 5 if 0 alt 1 proto 2 vid 0x03F0 pid 0x0317
[4294691.601000] usbcore: registered new driver usblp
[4294691.601000] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[4294692.502000] skge eth0: Link is up at 100 Mbps, full duplex, flow control tx and rx
[4294692.943000] NET: Registered protocol family 17
[4294694.990000] cx25840 1-0044: loaded v4l-cx25840.fw firmware (14264 bytes)
[4294695.040000] ivtv0: i2c attach to card #0 ok [client=cx25840, addr=44]
[4294695.081000] wm8775 1-001b: chip found @ 0x36 (ivtv i2c driver #0)
[4294695.088000] ivtv0: i2c attach to card #0 ok [client=wm8775, addr=1b]
[4294695.115000] tda9887 1-0043: (ivtv) chip found @ 0x86 (ivtv i2c driver #0)
[4294695.115000] ivtv0: i2c attach to card #0 ok [client=tda9887, addr=43]
[4294695.346000] NET: Registered protocol family 10
[4294695.346000] lo: Disabled Privacy Extensions
[4294695.346000] IPv6 over IPv4 tunneling driver
[4294695.779000] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[4294695.989000] ivtv0: Encoder revision: 0x02050032
[4294695.989000] ivtv0: Allocate DMA encoder MPEG stream: 128 x 32768 buffers (4096KB total)
[4294695.989000] ivtv0: Allocate DMA encoder YUV stream: 194 x 10800 buffers (2048KB total)
[4294695.989000] ivtv0: Allocate DMA encoder VBI stream: 120 x 17472 buffers (2048KB total)
[4294695.989000] ivtv0: Allocate DMA encoder PCM audio stream: 455 x 4608 buffers (2048KB total)
[4294695.990000] ivtv0: Create encoder radio stream
[4294695.990000] tuner: type set to 47 (LG NTSC (TAPE series)) by ivtv i2c driver #0
[4294696.180000] ivtv0: Initialized WinTV PVR 150, card #0
[4294696.181000] ivtv:  ====================  END INIT IVTV  ====================
[/PHP]

But it get this error when I try and run tvtime:

videoinput: Using video4linux2 driver 'ivtv', card 'WinTV PVR 150' (bus 0000:00:0e.0).
videoinput: Version is 1028, capabilities 1070011.
videoinput: Maximum input width: 720 pixels.
videoinput: Card failed to allocate capture buffers: Invalid argument

Any suggestions?

---

### Post by PryGuy on 2007-06-03
Got the same error. Have you solved the problem?

---

