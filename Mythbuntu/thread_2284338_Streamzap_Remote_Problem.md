---
title: "Streamzap Remote Problem"
date: 2015-06-28
forum: Mythbuntu
---

### Post by CSharpe67 on 2015-06-28
Hi all,  I had the remote working after an update it stopped.  I installed  ir-keytable and have the following results:

mike@myth1:~$ sudo ir-keytable 
Found /sys/class/rc/rc0/ (/dev/input/event4) with:
    Driver cx88xx, table rc-hauppauge
    Supported protocols: NEC RC-5 RC-6 JVC SONY SANYO LIRC RC-5-SZ other 
    Enabled protocols: LIRC 
    Name: cx88 IR (pcHDTV HD5500 HDTV)
    bus: 1, vendor/product: 7063:5500, version: 0x0001
    Repeat delay = 500 ms, repeat period = 125 ms
Found /sys/class/rc/rc1/ (/dev/input/event6) with:
    Driver streamzap, table rc-streamzap
    Supported protocols: NEC RC-5 RC-6 JVC SONY SANYO LIRC RC-5-SZ other 
    Enabled protocols: LIRC 
    Name: Streamzap PC Remote Infrared Rec
    bus: 3, vendor/product: 0e9c:0000, version: 0x0100
    Repeat delay = 500 ms, repeat period = 125 ms

rco is the tuner card while rc1 is the actual remote.  How can I get the remote to be rc0/ the first option for programs?

Thanks in advance.

Mike

Just Copied this

mode2: could not get file information for /dev/lirc
mode2: default_init(): No such file or directory





sudo ir-keytable -t -v --sysdev rc1
Found device /sys/class/rc/rc0/
Found device /sys/class/rc/rc1/
Input sysfs node is /sys/class/rc/rc1/input15/
Event sysfs node is /sys/class/rc/rc1/input15/event15/
Parsing uevent /sys/class/rc/rc1/input15/event15/uevent
/sys/class/rc/rc1/input15/event15/uevent uevent MAJOR=13
/sys/class/rc/rc1/input15/event15/uevent uevent MINOR=79
/sys/class/rc/rc1/input15/event15/uevent uevent DEVNAME=input/event15
Parsing uevent /sys/class/rc/rc1/uevent
/sys/class/rc/rc1/uevent uevent NAME=rc-streamzap
/sys/class/rc/rc1/uevent uevent DRV_NAME=streamzap
input device is /dev/input/event15
/sys/class/rc/rc1/protocols protocol rc-5 (disabled)
/sys/class/rc/rc1/protocols protocol nec (disabled)
/sys/class/rc/rc1/protocols protocol rc-6 (disabled)
/sys/class/rc/rc1/protocols protocol jvc (disabled)
/sys/class/rc/rc1/protocols protocol sony (disabled)
/sys/class/rc/rc1/protocols protocol rc-5-sz (disabled)
/sys/class/rc/rc1/protocols protocol sanyo (disabled)
/sys/class/rc/rc1/protocols protocol sharp (disabled)
/sys/class/rc/rc1/protocols protocol mce_kbd (disabled)
/sys/class/rc/rc1/protocols protocol lirc (enabled)
Opening /dev/input/event15
Input Protocol version: 0x00010001
Testing events. Please, press CTRL-C to abort.

mike@myth1:~sudo ir-keytable --read --device=/dev/input/event15
scancode 0x28c0 = KEY_NUMERIC_0 (0x200)
scancode 0x28c1 = KEY_NUMERIC_1 (0x201)
scancode 0x28c2 = KEY_NUMERIC_2 (0x202)
scancode 0x28c3 = KEY_NUMERIC_3 (0x203)
scancode 0x28c4 = KEY_NUMERIC_4 (0x204)
scancode 0x28c5 = KEY_NUMERIC_5 (0x205)
scancode 0x28c6 = KEY_NUMERIC_6 (0x206)
scancode 0x28c7 = KEY_NUMERIC_7 (0x207)
scancode 0x28c8 = KEY_NUMERIC_8 (0x208)
scancode 0x28c9 = KEY_NUMERIC_9 (0x209)
scancode 0x28ca = KEY_POWER (0x74)
scancode 0x28cb = KEY_MUTE (0x71)
scancode 0x28cc = KEY_CHANNELUP (0x192)
scancode 0x28cd = KEY_VOLUMEUP (0x73)
scancode 0x28ce = KEY_CHANNELDOWN (0x193)
scancode 0x28cf = KEY_VOLUMEDOWN (0x72)
scancode 0x28d0 = KEY_UP (0x67)
scancode 0x28d1 = KEY_LEFT (0x69)
scancode 0x28d2 = KEY_OK (0x160)
scancode 0x28d3 = KEY_RIGHT (0x6a)
scancode 0x28d4 = KEY_DOWN (0x6c)
scancode 0x28d5 = KEY_MENU (0x8b)
scancode 0x28d6 = KEY_EXIT (0xae)
scancode 0x28d7 = KEY_PLAY (0xcf)
scancode 0x28d8 = KEY_PAUSE (0x77)
scancode 0x28d9 = KEY_STOP (0x80)
scancode 0x28da = KEY_BACK (0x9e)
scancode 0x28db = KEY_FORWARD (0x9f)
scancode 0x28dc = KEY_RECORD (0xa7)
scancode 0x28dd = KEY_REWIND (0xa8)
scancode 0x28de = KEY_FASTFORWARD (0xd0)
scancode 0x28e0 = KEY_RED (0x18e)
scancode 0x28e1 = KEY_GREEN (0x18f)
scancode 0x28e2 = KEY_YELLOW (0x190)
scancode 0x28e3 = KEY_BLUE (0x191)
Enabled protocols: NEC RC-6 JVC SONY SANYO LIRC RC-5-SZ

---

