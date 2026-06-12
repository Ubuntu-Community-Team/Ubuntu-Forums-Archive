---
title: "Kworld 355U"
date: 2010-02-14
forum: Multimedia Software
---

### Post by c.nordlohne on 2010-02-14
Hi,

I 'm trying tu install Kworld 355U on 

Linux 2.6.31-19-generic #56-Ubuntu SMP 

looking an dmesg shows like this

[ 9916.338326] Linux video capture interface: v2.00
[ 9916.377452] em28xx: New device USB 2870 Device @ 480 Mbps (eb1a:e355, interface 0, class 0)
[ 9916.377646] em28xx #0: chip ID is em2870
[ 9916.460245] em28xx #0: i2c eeprom 00: 1a eb 67 95 1a eb 55 e3 c0 12 62 40 6a 22 00 00
[ 9916.460339] em28xx #0: i2c eeprom 10: 00 00 04 57 6a 0d 00 00 60 00 00 00 02 00 00 00
[ 9916.460354] em28xx #0: i2c eeprom 20: 54 00 00 00 f0 10 01 00 00 00 00 00 5b 00 00 00
[ 9916.460369] em28xx #0: i2c eeprom 30: 00 00 20 40 20 80 02 20 01 01 00 00 00 00 00 00
[ 9916.460383] em28xx #0: i2c eeprom 40: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[ 9916.460397] em28xx #0: i2c eeprom 50: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[ 9916.460411] em28xx #0: i2c eeprom 60: 00 00 00 00 00 00 00 00 00 00 22 03 55 00 53 00
[ 9916.460425] em28xx #0: i2c eeprom 70: 42 00 20 00 32 00 38 00 37 00 30 00 20 00 44 00
[ 9916.460440] em28xx #0: i2c eeprom 80: 65 00 76 00 69 00 63 00 65 00 00 00 00 00 00 00
[ 9916.460454] em28xx #0: i2c eeprom 90: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[ 9916.460468] em28xx #0: i2c eeprom a0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[ 9916.460491] em28xx #0: i2c eeprom b0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[ 9916.460505] em28xx #0: i2c eeprom c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[ 9916.460519] em28xx #0: i2c eeprom d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[ 9916.460533] em28xx #0: i2c eeprom e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[ 9916.460548] em28xx #0: i2c eeprom f0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[ 9916.460563] em28xx #0: EEPROM ID= 0x9567eb1a, EEPROM hash = 0x16317f02
[ 9916.460565] em28xx #0: EEPROM info:
[ 9916.460568] em28xx #0:       No audio on board.
[ 9916.460570] em28xx #0:       500mA max power
[ 9916.460573] em28xx #0:       Table at 0x04, strings=0x226a, 0x0000, 0x0000
[ 9916.461242] em28xx #0: Identified as Kworld 355 U DVB-T (card=42)
[ 9916.461245] em28xx #0:
[ 9916.461247]
[ 9916.461249] em28xx #0: The support for this board weren't valid yet.
[ 9916.461252] em28xx #0: Please send a report of having this working
[ 9916.461254] em28xx #0: not to V4L mailing list (and/or to other addresses)
[ 9916.461256]
[ 9916.474242] em28xx #0: v4l2 driver version 0.1.2
[ 9916.480208] em28xx #0: V4L2 device registered as /dev/video0 and /dev/vbi0
[ 9916.480237] usbcore: registered new interface driver em28xx
[ 9916.480241] em28xx driver loaded


fula:~# lsmod |grep em
em28xx                 80968  0
ir_common              48512  1 em28xx
v4l2_common            17500  2 tuner,em28xx
videodev               36736  3 tuner,em28xx,v4l2_common
videobuf_vmalloc        6496  1 em28xx
videobuf_core          17952  2 em28xx,videobuf_vmalloc
tveeprom               11872  1 em28xx


fula:~# scantv

ioctl: VIDIOC_S_INPUT(int=0): Invalid argument
invalid value for input: Television
valid choices for "input":
vbi: open failed [/dev/vbi]
open /dev/vbi: Invalid argument

fula:~# ll /dev/v*
lrwxrwxrwx  1 root root        9 2010-02-14 13:22 /dev/vbi -> /dev/vbi0
crw-rw----+ 1 root video 81,   1 2010-02-14 14:48 /dev/vbi0

user@fula:~$ xawtv
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.31-19-generic)
xinerama 0: 1680x1050+0+0
WARNING: No DGA direct video mode for this display.
/dev/video0 [v4l2]: no overlay support
v4l-conf had some trouble, trying to continue anyway
Warning: Missing charsets in String to FontSet conversion
Warning: Cannot convert string "-*-lucidatypewriter-bold-r-normal-*-14-*-*-*-m-*-iso8859-*,           -*-courier-bold-r-normal-*-14-*-*-*-m-*-iso8859-*,          -gnu-unifont-bold-r-normal--16-*-*-*-c-*-*-*,        -efont-biwidth-bold-r-normal--16-*-*-*-*-*-*-*,                 -*-*-bold-r-normal-*-16-*-*-*-m-*-*-*,                 -*-*-bold-r-normal-*-16-*-*-*-c-*-*-*,                         -*-*-*-*-*-*-16-*-*-*-*-*-*-*,*" to type FontSet
Warning: Cannot convert string "-*-ledfixed-medium-r-*--39-*-*-*-c-*-*-*" to type FontStruct
Warning: Missing charsets in String to FontSet conversion
Warning: Cannot convert string "-*-lucidatypewriter-bold-r-normal-*-14-*-*-*-m-*-iso8859-*,           -*-courier-bold-r-normal-*-14-*-*-*-m-*-iso8859-*,          -gnu-unifont-bold-r-normal--16-*-*-*-c-*-*-*,        -efont-biwidth-bold-r-normal--16-*-*-*-*-*-*-*,                 -*-*-bold-r-normal-*-16-*-*-*-m-*-*-*,                 -*-*-bold-r-normal-*-16-*-*-*-c-*-*-*,                         -*-*-*-*-*-*-16-*-*-*-*-*-*-*, *" to type FontSet
ioctl: VIDIOC_S_INPUT(int=0): Argumento inválido
v4l2: oops: select timeout

Any idea how to get the stick started to solve the problem ?

---

