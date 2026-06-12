---
title: "ir-keytable multiple events"
date: 2021-06-10
forum: Multimedia Software
---

### Post by mapota on 2021-06-10
Hi,

I have a new installation of xubuntu desktop 20.04.2 to be used for mythtv. I am having trouble with ir-keytable and multiple presses for a single ir remote press.

```
sudo ir-keytable

```returns


```
Found /sys/class/rc/rc0/ with:
    Name: Media Center Ed. eHome Infrared Remote Transceiver (0609:0334)
    Driver: mceusb
    Default keymap: rc-rc6-mce
    Input device: /dev/input/event7
    LIRC device: /dev/lirc0
    Attached BPF protocols: Operation not supported
    Supported kernel protocols: lirc rc-5 rc-5-sz jvc sony nec sanyo mce_kbd rc-6 sharp xmp imon rc-mm 
    Enabled kernel protocols: lirc rc-6 
    bus: 3, vendor/product: 0609:0334, version: 0x0100
    Repeat delay = 500 ms, repeat period = 125 ms

```

```
sudo ir-keytable --test -verbose
```
returns
```
Found device /sys/class/rc/rc0/Parsing uevent /sys/class/rc/rc0/lirc0/uevent
/sys/class/rc/rc0/lirc0/uevent uevent MAJOR=239
/sys/class/rc/rc0/lirc0/uevent uevent MINOR=0
/sys/class/rc/rc0/lirc0/uevent uevent DEVNAME=lirc0
Input sysfs node is /sys/class/rc/rc0/input4/
Event sysfs node is /sys/class/rc/rc0/input4/event7/
Parsing uevent /sys/class/rc/rc0/input4/event7/uevent
/sys/class/rc/rc0/input4/event7/uevent uevent MAJOR=13
/sys/class/rc/rc0/input4/event7/uevent uevent MINOR=71
/sys/class/rc/rc0/input4/event7/uevent uevent DEVNAME=input/event7
Parsing uevent /sys/class/rc/rc0/uevent
/sys/class/rc/rc0/uevent uevent NAME=rc-rc6-mce
/sys/class/rc/rc0/uevent uevent DRV_NAME=mceusb
/sys/class/rc/rc0/uevent uevent DEV_NAME=Media Center Ed. eHome Infrared Remote Transceiver (0609:0334)
input device is /dev/input/event7
/sys/class/rc/rc0/protocols protocol rc-5 (disabled)
/sys/class/rc/rc0/protocols protocol nec (disabled)
/sys/class/rc/rc0/protocols protocol rc-6 (enabled)
/sys/class/rc/rc0/protocols protocol jvc (disabled)
/sys/class/rc/rc0/protocols protocol sony (disabled)
/sys/class/rc/rc0/protocols protocol rc-5-sz (disabled)
/sys/class/rc/rc0/protocols protocol sanyo (disabled)
/sys/class/rc/rc0/protocols protocol sharp (disabled)
/sys/class/rc/rc0/protocols protocol mce_kbd (disabled)
/sys/class/rc/rc0/protocols protocol xmp (disabled)
/sys/class/rc/rc0/protocols protocol imon (disabled)
/sys/class/rc/rc0/protocols protocol rc-mm (disabled)
/sys/class/rc/rc0/protocols protocol lirc (enabled)
Opening /dev/input/event7
Input Protocol version: 0x00010001
Testing events. Please, press CTRL-C to abort.
5982.257056: lirc protocol(rc6_mce): scancode = 0x800f0416
5982.257069: event type EV_REP(0x14): value = 125
5982.257069: event type EV_MSC(0x04): scancode = 0x800f0416
5982.257069: event type EV_KEY(0x01) key_down: KEY_PLAY(0x00cf)
5982.257069: event type EV_SYN(0x00).
5982.363046: lirc protocol(rc6_mce): scancode = 0x800f0416
5982.363063: event type EV_MSC(0x04): scancode = 0x800f0416
5982.363063: event type EV_SYN(0x00).
5982.469043: lirc protocol(rc6_mce): scancode = 0x800f0416
5982.469059: event type EV_MSC(0x04): scancode = 0x800f0416
5982.469059: event type EV_SYN(0x00).
5982.788717: event type EV_KEY(0x01) key_down: KEY_PLAY(0x00cf)
5982.788717: event type EV_SYN(0x00).
5982.799027: lirc protocol(rc6_mce): scancode = 0x800f0416 toggle=1
5982.788717: event type EV_KEY(0x01) key_up: KEY_PLAY(0x00cf)
5982.788717: event type EV_MSC(0x04): scancode = 0x800f0416
5982.788717: event type EV_KEY(0x01) key_down: KEY_PLAY(0x00cf)
5982.788717: event type EV_SYN(0x00).
5982.905005: lirc protocol(rc6_mce): scancode = 0x800f0416 toggle=1
5982.905017: event type EV_MSC(0x04): scancode = 0x800f0416
5982.905017: event type EV_SYN(0x00).
5983.011011: lirc protocol(rc6_mce): scancode = 0x800f0416 toggle=1
5983.011019: event type EV_MSC(0x04): scancode = 0x800f0416
5983.011019: event type EV_SYN(0x00).
5983.300713: event type EV_KEY(0x01) key_down: KEY_PLAY(0x00cf)
5983.300713: event type EV_SYN(0x00).
5983.432716: event type EV_KEY(0x01) key_down: KEY_PLAY(0x00cf)
5983.432716: event type EV_SYN(0x00).
5983.564715: event type EV_KEY(0x01) key_down: KEY_PLAY(0x00cf)
5983.564715: event type EV_SYN(0x00).
...
multiple repeats 
...
5995.584716: event type EV_KEY(0x01) key_down: KEY_PLAY(0x00cf)
5995.584716: event type EV_SYN(0x00).
5995.716715: event type EV_KEY(0x01) key_down: KEY_PLAY(0x00cf)
5995.716715: event type EV_SYN(0x00).
5995.716715: event type EV_KEY(0x01) key_up: KEY_PLAY(0x00cf)
5995.716715: event type EV_SYN(0x00).

```

You can see the (repeat) events start at 5983.300713 and end at 5995.716715 for a period of 12.4 seconds!!!

I have tried changing the Repeat Delay and Repeat period, as suggested on many sites but no joy. I do see a difference in how frequent the events are seen but still get many repeats.

Any suggestions? 

ir-keytable version is IR keytable control version 1.18.0, in case that helps.

---

