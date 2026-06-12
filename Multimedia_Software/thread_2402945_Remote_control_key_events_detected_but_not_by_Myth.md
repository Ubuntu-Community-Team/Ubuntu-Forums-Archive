---
title: "Remote control key events detected but not by MythTV or Kodi"
date: 2018-10-05
forum: Multimedia Software
---

### Post by philled on 2018-10-05
I recently upgraded to Ubuntu 18.04 and it's common knowledge that this often breaks the previous infrared remote control setup. I use a Harmony universal remote which worked fine on my 16.04 Ubuntu MythTV frontend. I had it set up with devinput so I didn't need to run lirc. After upgrading to Ubuntu 18.04 the only buttons that generated a response in MythTV are up, down, left, and right. 

But after a bit of work I think I'm now close to getting it working again. I'm trying to set it up using the devinput kernel driver so that the remote control button presses are detected like keyboard presses. When I run ir-keytable -t I get responses like these, which must mean the button presses are being detected:

```
$ sudo ir-keytable -t --verbose
Found device /sys/class/rc/rc0/
Parsing uevent /sys/class/rc/rc0/lirc0/uevent
/sys/class/rc/rc0/lirc0/uevent uevent MAJOR=236
/sys/class/rc/rc0/lirc0/uevent uevent MINOR=0
/sys/class/rc/rc0/lirc0/uevent uevent DEVNAME=lirc0
Input sysfs node is /sys/class/rc/rc0/input7/
Event sysfs node is /sys/class/rc/rc0/input7/event4/
Parsing uevent /sys/class/rc/rc0/input7/event4/uevent
/sys/class/rc/rc0/input7/event4/uevent uevent MAJOR=13
/sys/class/rc/rc0/input7/event4/uevent uevent MINOR=68
/sys/class/rc/rc0/input7/event4/uevent uevent DEVNAME=input/event4
Parsing uevent /sys/class/rc/rc0/uevent
/sys/class/rc/rc0/uevent uevent NAME=rc-rc6-mce
/sys/class/rc/rc0/uevent uevent DRV_NAME=mceusb
/sys/class/rc/rc0/uevent uevent DEV_NAME=Media Center Ed. eHome Infrared Remote Transceiver (1934:5168)
input device is /dev/input/event4
/sys/class/rc/rc0/protocols protocol rc-5 (enabled)
/sys/class/rc/rc0/protocols protocol nec (enabled)
/sys/class/rc/rc0/protocols protocol rc-6 (enabled)
/sys/class/rc/rc0/protocols protocol jvc (enabled)
/sys/class/rc/rc0/protocols protocol sony (enabled)
/sys/class/rc/rc0/protocols protocol rc-5-sz (enabled)
/sys/class/rc/rc0/protocols protocol sanyo (enabled)
/sys/class/rc/rc0/protocols protocol sharp (enabled)
/sys/class/rc/rc0/protocols protocol mce_kbd (enabled)
/sys/class/rc/rc0/protocols protocol xmp (enabled)
/sys/class/rc/rc0/protocols protocol lirc (enabled)
Opening /dev/input/event4
Input Protocol version: 0x00010001
Testing events. Please, press CTRL-C to abort.
687.002319: event type EV_MSC(0x04): scancode = 0x800f0422
687.002319: event type EV_KEY(0x01) key_down: KEY_OK(0x0160)
687.002319: event type EV_SYN(0x00).
687.108320: event type EV_MSC(0x04): scancode = 0x800f0422
687.108320: event type EV_SYN(0x00).
687.388012: event type EV_KEY(0x01) key_up: KEY_OK(0x0160)
687.388012: event type EV_SYN(0x00).
690.297390: event type EV_MSC(0x04): scancode = 0x800f0424
690.297390: event type EV_KEY(0x01) key_down: KEY_DVD(0x0185)
690.297390: event type EV_SYN(0x00).
690.403392: event type EV_MSC(0x04): scancode = 0x800f0424
690.403392: event type EV_SYN(0x00).
690.684009: event type EV_KEY(0x01) key_up: KEY_DVD(0x0185)
690.684009: event type EV_SYN(0x00).
694.242480: event type EV_MSC(0x04): scancode = 0x800f040f
694.242480: event type EV_KEY(0x01) key_down: KEY_INFO(0x0166)
694.242480: event type EV_SYN(0x00).
694.349478: event type EV_MSC(0x04): scancode = 0x800f040f
694.349478: event type EV_SYN(0x00).
694.604011: event type EV_KEY(0x01) key_up: KEY_INFO(0x0166)
694.604011: event type EV_SYN(0x00).
696.692538: event type EV_MSC(0x04): scancode = 0x800f0423
696.692538: event type EV_KEY(0x01) key_down: KEY_EXIT(0x00ae)
696.692538: event type EV_SYN(0x00).
696.798535: event type EV_MSC(0x04): scancode = 0x800f0423
696.798535: event type EV_SYN(0x00).
697.052024: event type EV_KEY(0x01) key_up: KEY_EXIT(0x00ae)
697.052024: event type EV_SYN(0x00).
699.849604: event type EV_MSC(0x04): scancode = 0x800f0426
699.849604: event type EV_KEY(0x01) key_down: KEY_EPG(0x016d)
699.849604: event type EV_SYN(0x00).
699.955602: event type EV_MSC(0x04): scancode = 0x800f0426
699.955602: event type EV_SYN(0x00).
700.220010: event type EV_KEY(0x01) key_up: KEY_EPG(0x016d)
700.220010: event type EV_SYN(0x00).
702.733668: event type EV_MSC(0x04): scancode = 0x800f0401
702.733668: event type EV_KEY(0x01) key_down: KEY_NUMERIC_1(0x0201)
702.733668: event type EV_SYN(0x00).
702.839666: event type EV_MSC(0x04): scancode = 0x800f0401
702.839666: event type EV_SYN(0x00).
703.100010: event type EV_KEY(0x01) key_up: KEY_NUMERIC_1(0x0201)
703.100010: event type EV_SYN(0x00).
704.231704: event type EV_MSC(0x04): scancode = 0x800f0402
704.231704: event type EV_KEY(0x01) key_down: KEY_NUMERIC_2(0x0202)
704.231704: event type EV_SYN(0x00).
704.338701: event type EV_MSC(0x04): scancode = 0x800f0402
704.338701: event type EV_SYN(0x00).
704.604011: event type EV_KEY(0x01) key_up: KEY_NUMERIC_2(0x0202)
704.604011: event type EV_SYN(0x00).
```

But when I fire up MythTV the button presses aren't detected at all. Here's an extract of my $HOME/.lircrc:

```
[FONT=Arial]...
begin
    remote = devinput
    prog = mythtv
    button = KEY_NUMERIC_1
    config = 1
    repeat = 0
    delay = 10
end


begin
    remote = devinput
    prog = mythtv
    button = KEY_NUMERIC_0
    config = 0
    repeat = 0
    delay = 10
end
[/FONT][FONT=Arial]...etc...[/FONT]
```


Can anyone please advise what I need to do to get MythTV, and Kodi for that matter, to register the button presses?

One last thing, and I know this may sound dumb, but I DON'T have the lirc daemon running. Do I need to be running it in order for MythTV to detect the remote control presses? I thought the idea of the kernel devinput driver was that lirc isn't needed any more because the remote control is detected as if it was a keyboard so I don't run it and was actually looking forward to totally removing the lirc packages. Maybe I'm misunderstanding the whole devinput thing?

---

### Post by vidtek on 2018-10-11
Phil-

I had this problem too-after days of stuffing around I wrote this how-to: 
[https://ubuntuforums.org/showthread.php?t=2403337]("https://ubuntuforums.org/showthread.php?t=2403337")

Any problems please post,  cheers, Tony.

---

