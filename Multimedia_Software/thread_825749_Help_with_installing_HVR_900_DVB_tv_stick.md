---
title: "Help with installing HVR 900 DVB tv stick"
date: 2008-06-11
forum: Multimedia Software
---

### Post by tunznath on 2008-06-11
heres the output of dmesg

[ 925.543248] tveeprom 1-0050: Hauppauge model 65018, rev B2C0, serial# 1054XXX
[ 925.543258] tveeprom 1-0050: tuner model is Xceive XC3028 (idx 120, type 71)
[ 925.543262] tveeprom 1-0050: TV standards PAL(B/G) PAL(I) PAL(D/D1/K) ATSC/DVB Digital (eeprom 0xd4)
[ 925.543265] tveeprom 1-0050: audio processor is None (idx 0)
[ 925.543267] tveeprom 1-0050: has radio
[ 925.618089] tuner’ 1-0061: chip found @ 0xc2 (em28xx #0)
[ 925.698393] xc2028 1-0061: creating new instance
[ 925.698403] xc2028 1-0061: type set to XCeive xc2028/xc3028 tuner
[ 925.744473] xc2028 1-0061: Error: firmware xc3028-v27.fw not found.
[ 925.839267] tvp5150 1-005c: tvp5150am1 detected.
[ 925.987980] em28xx #0: V4L2 device registered as /dev/video0 and /dev/vbi0
[ 925.987991] em28xx #0: Found Hauppauge WinTV HVR 900 (R2)
[ 925.988037] usbcore: registered new interface driver em28xx
[ 926.075335] tvp5150 1-005c: tvp5150am1 detected.


What is wrong with it - why doesnt MyTV see the DVB stick
Any help appreciated
Nath

---

### Post by tunznath on 2008-06-11
bump

---

### Post by tunznath on 2008-06-20
bump again

---

### Post by xc3RnbFO8P on 2008-06-20
Here is a Howto:
[http://mcentral.de/wiki/index.php5/Installation_Guide]("http://mcentral.de/wiki/index.php5/Installation_Guide")
[http://http://www.2nrds.com/digital-tv-in-linux-with-em28xx-devices]("http://http://www.2nrds.com/digital-tv-in-linux-with-em28xx-devices")

---

