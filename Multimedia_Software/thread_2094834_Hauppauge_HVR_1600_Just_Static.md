---
title: "Hauppauge HVR 1600 Just Static"
date: 2012-12-14
forum: Multimedia Software
---

### Post by josesanders on 2012-12-14
I have been running MythTV in Ubuntu 10.10 for a few years.  The other day, I started getting random restart issues, and it suddenly stopped recognizing my HVR 1600.  So I figured the card must just be fried.  I bought a new one, which I thought was exactly identical.  Now when I start up, the card is recognized, but all I'm getting out of it is static, either through MythTV watching live or recording, or with just using 'cat /dev/video0 > test.mpg'.  Any help would be much appreciated.  I feel like I've come across this before and solved it, but it's been too many years, and I can't remember how to do anything.

Here's the relevant portion when I run lspci:

[PHP]
04:01.0 Multimedia video controller: Conexant Systems, Inc. CX23418 Single-Chip MPEG-2 Encoder with Integrated Analog Video/Broadcast Audio Decoder
[/PHP]

Here is the portion of the dmesg output that appears to be relevant:

[PHP][   10.312245] tveeprom 0-0050: Hauppauge model 74141, rev C6B6, serial# 7105193
[   10.312248] tveeprom 0-0050: MAC address is 00:0d:fe:6c:6a:a9
[   10.312250] tveeprom 0-0050: tuner model is Philips FM1236 MK5 (idx 116, type 43)
[   10.312252] tveeprom 0-0050: TV standards NTSC(M) (eeprom 0x08)
[   10.312254] tveeprom 0-0050: audio processor is CX23418 (idx 38)
[   10.312256] tveeprom 0-0050: decoder processor is CX23418 (idx 31)
[   10.312258] tveeprom 0-0050: has radio, has IR receiver, has IR transmitter
[   10.312260] cx18-0: Autodetected Hauppauge HVR-1600
[   10.312261] cx18-0: Simultaneous Digital and Analog TV capture supported
[   10.412735] tuner 1-0043: chip found @ 0x86 (cx18 i2c driver #0-1)
[   10.414221] tda9887 1-0043: creating new instance
[   10.414223] tda9887 1-0043: tda988[5/6/7] found
[   10.416249] tuner 1-0061: chip found @ 0xc2 (cx18 i2c driver #0-1)
[   10.418063] cs5345 0-004c: chip found @ 0x98 (cx18 i2c driver #0-0)
[   10.442671] IR RC6 protocol handler initialized
[   10.444781] IR JVC protocol handler initialized
[   10.446470] IR Sony protocol handler initialized
[   10.449115] lirc_dev: IR Remote Control driver registered, major 250 
[   10.450563] rc rc0: lirc_dev: driver ir-lirc-codec (streamzap) registered at minor = 0
[   10.450566] IR LIRC bridge handler initialized
[   10.451267] Registered IR keymap rc-hauppauge-new
[   10.451332] input: i2c IR (Hauppauge HVR-1600) as /devices/virtual/rc/rc1/input6
[   10.451372] rc1: i2c IR (Hauppauge HVR-1600) as /devices/virtual/rc/rc1
[   10.451374] ir-kbd-i2c: i2c IR (Hauppauge HVR-1600) detected at i2c-0/0-0071/ir0 [cx18 i2c driver #0-0]
[   10.647638] xc2028 1-0061: creating new instance
[   10.647641] xc2028 1-0061: type set to XCeive xc2028/xc3028 tuner
[   10.647965] cx18-0: Registered device video0 for encoder MPEG (64 x 32.00 kB)
[   10.647968] DVB: registering new adapter (cx18)
[   10.703461] MXL5005S: Attached at address 0x63
[   10.703467] DVB: registering adapter 0 frontend 0 (Samsung S5H1409 QAM/8VSB Frontend)...
[   10.703557] cx18-0: DVB Frontend registered
[   10.703559] cx18-0: Registered DVB adapter0 for TS (32 x 32.00 kB)
[   10.703586] cx18-0: Registered device video32 for encoder YUV (20 x 101.25 kB)
[   10.703610] cx18-0: Registered device vbi0 for encoder VBI (20 x 51984 bytes)
[   10.703641] cx18-0: Registered device video24 for encoder PCM audio (256 x 4.00 kB)
[   10.703662] cx18-0: Registered device radio0 for encoder radio
[   10.703664] cx18-0: Initialized card: Hauppauge HVR-1600
[   10.703682] cx18:  End initialization
[   10.714306] cx18-alsa: module loading...
[   10.787355] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input7
[   10.862575] cx18-0: loaded v4l-cx23418-cpu.fw firmware (158332 bytes)
[   10.988772] cx18-0: loaded v4l-cx23418-apu.fw firmware V00120000 (141200 bytes)
[   10.994990] cx18-0: FW version: 0.0.74.0 (Release 2007/03/12)
[/PHP]

---

