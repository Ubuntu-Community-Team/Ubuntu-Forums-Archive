---
title: "MCE Remote Stops Working After A Few Hours"
date: 2010-10-30
forum: Mythbuntu
---

### Post by 1770 DFS on 2010-10-30
I have recently added a frontend to the Myth collection after running a combined frontend\backend and secondary frontend. I have now split the backend up so the frontend is seperate but hit the protocol mismatch issues with the new frontend so upgraded all machines to 10.10. I have managed to sort out all\most glitches but have issues with lirc on one frontend. 

The frontend with the issues is a Dell Dimension C521, everything is basically standard, I have an ipazzport wireless keyboard attached, a RC6 remote with MCEUSB receiver and an Acer V233Hb on VGA. 

When I first installed Ubuntu 10.10, via upgrade from an existing fresh 10.04 install, IR worked briefly but then stopped. I then found the following;

[http://ubuntuforums.org/showthread.php?p=9984844#post9984844](http://ubuntuforums.org/showthread.php?p=9984844#post9984844)

and tried option 2 as it seemed to be the most popular, which worked as a fix for a while but then stopped several hours after. IRW shows no output when the IR stops working. I restarted lirc, no joy. After rebooting the machine it works again for a few hours.

I also tried option 1 and it killed the IR completely so went back through option 2, which then brought about the same problem, IR stops working after several hours for some reason.

Now I'm at a loss, I'd say I'm a novice-intermediate with Ubuntu so any pointers would be handy. As the machine is locked in a cupboard and the ipazzport winds me up I do most administration via SSH from another machine.

Many thanks for reading.

---

### Post by 1770 DFS on 2010-10-30
Further to that, it's not neccesarily a few hours as it's just done it 5 mins after a reboot. It stopped working, checked irw, nothing, rebooted, all working and irw shows an output, 5 minutes later nothing in myth or irw.

This is why I stopped updating. :/

---

### Post by 1770 DFS on 2010-10-31
I'm just guessing here but I will add more if required. Whilst working;

lsusb
```
myth@MYTH-CL01:~$ lsusb
Bus 002 Device 003: ID 0168:0998
Bus 002 Device 002: ID 0471:0815 Philips (or NXP) eHome Infrared Receiver
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```irw
```
myth@MYTH-CL01:~$ irw
000000037ff07be1 00 Up mceusb
000000037ff07be0 00 Down mceusb
000000037ff07bdf 00 Left mceusb
000000037ff07bdf 01 Left mceusb
000000037ff07bde 00 Right mceusb
000000037ff07bf2 00 Home mceusb
000000037ff07bf2 01 Home mceusb
^C
myth@MYTH-CL01:~$
```lsinput
```
myth@MYTH-CL01:~$ sudo lsinput
[sudo] password for myth:
/dev/input/event0
   bustype : BUS_HOST
   vendor  : 0x0
   product : 0x1
   version : 0
   name    : "Power Button"
   phys    : "PNP0C0C/button/input0"
   bits ev : EV_SYN EV_KEY

/dev/input/event1
   bustype : BUS_HOST
   vendor  : 0x0
   product : 0x1
   version : 0
   name    : "Power Button"
   phys    : "LNXPWRBN/button/input0"
   bits ev : EV_SYN EV_KEY

/dev/input/event2
   bustype : BUS_USB
   vendor  : 0x168
   product : 0x998
   version : 273
   name    : "iPazzPort Wireless KM"
   phys    : "usb-0000:00:0b.0-8/input0"
   uniq    : ""
   bits ev : EV_SYN EV_KEY EV_REL EV_MSC

/dev/input/event3
   bustype : BUS_USB
   vendor  : 0x168
   product : 0x998
   version : 273
   name    : "iPazzPort Wireless KM"
   phys    : "usb-0000:00:0b.0-8/input1"
   uniq    : ""
   bits ev : EV_SYN EV_KEY EV_MSC EV_LED EV_REP

/dev/input/event4
   bustype : (null)
   vendor  : 0x0
   product : 0x0
   version : 0
   name    : "HDA NVidia Line In at Ext Rear J"
   phys    : "ALSA"
   bits ev : EV_SYN EV_SW

/dev/input/event5
   bustype : (null)
   vendor  : 0x0
   product : 0x0
   version : 0
   name    : "HDA NVidia Mic at Ext Front Jack"
   phys    : "ALSA"
   bits ev : EV_SYN EV_SW

/dev/input/event6
   bustype : (null)
   vendor  : 0x0
   product : 0x0
   version : 0
   name    : "HDA NVidia Mic at Ext Rear Jack"
   phys    : "ALSA"
   bits ev : EV_SYN EV_SW

/dev/input/event7
   bustype : (null)
   vendor  : 0x0
   product : 0x0
   version : 0
   name    : "HDA NVidia Speaker at Ext Rear J"
   phys    : "ALSA"
   bits ev : EV_SYN EV_SW

/dev/input/event8
   bustype : (null)
   vendor  : 0x0
   product : 0x0
   version : 0
   name    : "HDA NVidia Speaker at Ext Rear J"
   phys    : "ALSA"
   bits ev : EV_SYN EV_SW

/dev/input/event9
   bustype : (null)
   vendor  : 0x0
   product : 0x0
   version : 0
   name    : "HDA NVidia Speaker at Ext Rear J"
   phys    : "ALSA"
   bits ev : EV_SYN EV_SW

/dev/input/event10
   bustype : (null)
   vendor  : 0x0
   product : 0x0
   version : 0
   name    : "HDA NVidia Speaker at Ext Rear J"
   phys    : "ALSA"
   bits ev : EV_SYN EV_SW

/dev/input/event11
   bustype : (null)
   vendor  : 0x0
   product : 0x0
   version : 0
   name    : "HDA NVidia HP Out at Ext Front J"
   phys    : "ALSA"
   bits ev : EV_SYN EV_SW

/dev/input/event12
   bustype : (null)
   vendor  : 0x0
   product : 0x0
   version : 0
   name    : "Media Center Ed. eHome Infrared "
   phys    : "usb-0000:00:0b.0-4/input0"
   bits ev : EV_SYN EV_KEY EV_REP

myth@MYTH-CL01:~$
```evtest
```
myth@MYTH-CL01:~$ sudo evtest /dev/input/event12
Input driver version is 1.0.1
Input device ID: bus 0x0 vendor 0x0 product 0x0 version 0x0
Input device name: "Media Center Ed. eHome Infrared Remote Transceiver (0471:0815)"
Supported events:
  Event type 0 (Sync)
  Event type 1 (Key)
    Event code 28 (Enter)
    Event code 103 (Up)
    Event code 105 (Left)
    Event code 106 (Right)
    Event code 108 (Down)
    Event code 111 (Delete)
    Event code 113 (Mute)
    Event code 114 (VolumeDown)
    Event code 115 (VolumeUp)
    Event code 116 (Power)
    Event code 119 (Pause)
    Event code 128 (Stop)
    Event code 148 (Prog1)
    Event code 167 (Record)
    Event code 168 (Rewind)
    Event code 174 (Exit)
    Event code 207 (Play)
    Event code 208 (Fast Forward)
    Event code 212 (Camera)
    Event code 352 (Ok)
    Event code 358 (Info)
    Event code 365 (EPG)
    Event code 366 (PVR)
    Event code 368 (Language)
    Event code 369 (Title)
    Event code 370 (Subtitle)
    Event code 372 (Zoom)
    Event code 377 (TV)
    Event code 385 (Radio)
    Event code 386 (Tuner)
    Event code 389 (DVD)
    Event code 392 (Audio)
    Event code 393 (Video)
    Event code 398 (Red)
    Event code 399 (Green)
    Event code 400 (Yellow)
    Event code 401 (Blue)
    Event code 402 (ChannelUp)
    Event code 403 (ChannelDown)
    Event code 407 (Next)
    Event code 412 (Previous)
    Event code 512 (?)
    Event code 513 (?)
    Event code 514 (?)
    Event code 515 (?)
    Event code 516 (?)
    Event code 517 (?)
    Event code 518 (?)
    Event code 519 (?)
    Event code 520 (?)
    Event code 521 (?)
    Event code 522 (?)
    Event code 523 (?)
  Event type 20 (Repeat)
Testing ... (interrupt to exit)
^C
myth@MYTH-CL01:~$
```One thing I have just noticed is that the receiver doesn;t always show up in lsinput, it used to always be on 4 but now seems to have moved. Maybe this is one reason it didn;t work with using option 1 in the link in post 1 as it's always moving after every reboot? evtest doesn;t seem to be responding for some reason, but irw and Myth are working.

And it's just stopped working again, and the outputs of all the above remain the same except for irw which shows nothing.

---

### Post by movieman on 2010-11-02
Mine regularly doesn't work in 10.04 after booting, we either have to wait for some minutes until it starts working or reboot and hope it works this time. In the former case nothing shows up in irw, then we see one or two key presses with others still missing, and then we suddenly see all of them.

---

