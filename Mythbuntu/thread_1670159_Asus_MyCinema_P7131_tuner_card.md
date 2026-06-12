---
title: "Asus MyCinema P7131 tuner card"
date: 2011-01-18
forum: Mythbuntu
---

### Post by perjojek on 2011-01-18
My new tuner card does not work under Mythtv:

2011-01-18 22:02:37.658 TV: Attempting to change from None to WatchingLiveTV
2011-01-18 22:02:37.658 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2011-01-18 22:02:37.659 Using protocol version 23056
2011-01-18 22:02:37.663 Spawning LiveTV Recorder -- begin
2011-01-18 22:02:44.665 MythSocket(7fd300224450:56): readStringList: Error, timed out after 7000 ms.
2011-01-18 22:02:44.666 RemoteEncoder::SendReceiveStringList(): No response.
2011-01-18 22:02:44.666 Spawning LiveTV Recorder -- end
2011-01-18 22:02:44.670 ProgramInfo(): Updated pathname '':'' -> '1104_20110118220243.nuv'
2011-01-18 22:02:44.679 We have a playbackURL(/var/lib/mythtv/livetv/1104_20110118220243.nuv) & cardtype(V4L)
2011-01-18 22:02:47.309 We have a RingBuffer
2011-01-18 22:02:47.363 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2011-01-18 22:02:48.801 Using protocol version 23056
2011-01-18 22:03:27.363 TV Error: StartRecorder() -- timed out waiting for recorder to start
2011-01-18 22:03:27.363 TV Error: LiveTV not successfully started

Does anybody know what the problem may be?
thx

---

### Post by BicyclerBoy on 2011-01-18
The tuner card support comes from the kernel module dvb from video4linux project. LinuxTV.org

You can start to debug by looking in the output of
dmesg
lspci
lsmod


But you should check LinuxTV.org website for support before buying windoze market hardware.

There appears to be a lot a code change around this card trying to get dual tuners etc to work..
Seems like the original (2007/2008) support was incomplete.

---

### Post by perjojek on 2011-01-19
I  checked on the [linuxtv project site]("http://www.linuxtv.org/wiki/index.php/ASUS_My_Cinema-P7131_Hybrid") - the card is supported.  Since I am trying to set up analog channels, it should work out of the box..

It is interesting that I am able to watch TV on tvtime (no sound but at least video is there) whereas mythtv quits..

Here are some outputs of interest:
lspci
01:06.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)

dmesg
[    4.425846] saa7130/34: v4l2 driver version 0.2.16 loaded
[    4.437480] saa7134 0000:01:06.0: PCI INT A -> Link[LNKA] -> GSI 17 (level, low) -> IRQ 17
[    4.437485] saa7133[0]: found at 0000:01:06.0, rev: 209, irq: 17, latency: 64, mmio: 0xfaeff800
[    4.437492] saa7133[0]: subsystem: 1043:4876, board: ASUSTeK P7131 Hybrid [card=112,autodetected]
[    4.437511] saa7133[0]: board init: gpio is 0
[    4.470260] input: saa7134 IR (ASUSTeK P7131 Hybri as /devices/pci0000:00/0000:00:08.0/0000:01:06.0/rc/rc0/input7
[    4.470309] rc0: saa7134 IR (ASUSTeK P7131 Hybri as /devices/pci0000:00/0000:00:08.0/0000:01:06.0/rc/rc0
[    4.670185] saa7133[0]: i2c eeprom 00: 43 10 76 48 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[    4.670192] saa7133[0]: i2c eeprom 10: ff ff ff 0f ff 20 ff ff ff ff ff ff ff ff ff ff
[    4.670197] saa7133[0]: i2c eeprom 20: 01 40 01 02 03 01 01 03 08 ff 00 d5 ff ff ff ff
[    4.670203] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    4.670208] saa7133[0]: i2c eeprom 40: ff 21 00 c2 96 10 03 32 55 50 ff ff ff ff ff ff
[    4.670213] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    4.670218] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    4.670223] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    4.670228] saa7133[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    4.670233] saa7133[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    4.670238] saa7133[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    4.670243] saa7133[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    4.670248] saa7133[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    4.670253] saa7133[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    4.670258] saa7133[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    4.670263] saa7133[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    4.889225] tuner 0-004b: chip found @ 0x96 (saa7133[0])
[   11.060321] saa7133[0]: dsp access error
[   11.210132] saa7133[0]: registered device video0 [v4l2]
[   11.210156] saa7133[0]: registered device vbi0
[   11.210174] saa7133[0]: registered device radio0
[   11.214465] saa7134 ALSA driver for DMA sound loaded
[   11.214493] saa7133[0]/alsa: saa7133[0] at 0xfaeff800 irq 17 registered as card -2
[   12.200110] DVB: registering new adapter (saa7133[0])

---

### Post by perjojek on 2011-01-19
-

---

### Post by perjojek on 2011-01-19
-

---

### Post by perjojek on 2011-01-19
-

---

