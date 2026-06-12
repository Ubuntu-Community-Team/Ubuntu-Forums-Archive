---
title: "MCE remote HID - some keys behave strange"
date: 2010-10-01
forum: Mythbuntu
---

### Post by juxmw on 2010-10-01
Hi all 

I've got a Hama MCE Remote ([http://www.hama.de/portal/articleId*158507/searchMode*1/action*2563/bySearch*00052451?lid=0](http://www.hama.de/portal/articleId*158507/searchMode*1/action*2563/bySearch*00052451?lid=0))

Basically - it works ... without Lirc. 
But not all buttons - eg in Mythtv up/down/... are ok but I can not use "1", "2", or the colored buttons on top. 

When I try to change the settings from withing MythFrontend to use "Button 1" as "1" the system asks me if I want to assign "NumLock" - so something is wrong here.

When leaving out Myth and simply asking system tools the following happens:

```

# evtest /dev/input/event3 
Input driver version is 1.0.0
Input device ID: bus 0x3 vendor 0x5a4 product 0x9881 version 0x110
Input device name: "HID 05a4:9881"
Supported events:
  Event type 0 (Sync)
  Event type 1 (Key)
    Event code 1 (Esc)
    Event code 2 (1)
    Event code 3 (2)
....
<seems ok>
....

```

When I press "1" ONCE I see several lines of output:
```

Event: time 1285969547.322670, type 4 (Misc), code 4 (ScanCode), value 70053
Event: time 1285969547.322700, type 1 (Key), code 69 (NumLock), value 1
Event: time 1285969547.322707, -------------- Report Sync ------------
Event: time 1285969547.323032, type 17 (LED), code 0 (NumLock), value 1
Event: time 1285969547.330667, type 4 (Misc), code 4 (ScanCode), value 70053
Event: time 1285969547.330703, type 1 (Key), code 69 (NumLock), value 0
Event: time 1285969547.330709, -------------- Report Sync ------------
Event: time 1285969547.338672, type 4 (Misc), code 4 (ScanCode), value 70059
Event: time 1285969547.338706, type 1 (Key), code 79 (KP1), value 1
Event: time 1285969547.338712, -------------- Report Sync ------------
Event: time 1285969547.394686, type 4 (Misc), code 4 (ScanCode), value 70059
Event: time 1285969547.394716, type 1 (Key), code 79 (KP1), value 0
Event: time 1285969547.394724, type 4 (Misc), code 4 (ScanCode), value 70053
Event: time 1285969547.394730, type 1 (Key), code 69 (NumLock), value 1
Event: time 1285969547.394735, -------------- Report Sync ------------
Event: time 1285969547.395208, type 17 (LED), code 0 (NumLock), value 0
Event: time 1285969547.402685, type 4 (Misc), code 4 (ScanCode), value 70053
Event: time 1285969547.402717, type 1 (Key), code 69 (NumLock), value 0
Event: time 1285969547.402722, -------------- Report Sync ------------

```


This explains the problem with "NumLock".

Differnet view on the same data when cat-ing /sys/kernel/debug/hid/0003:05A4:9881.0001/events and pressing "1" ONCE

```
report (size 8) (unnumbered)
report 0 (size 8) =  00 00 53 00 00 00 00 00
Keyboard.00e0 = 0
Keyboard.00e1 = 0
Keyboard.00e2 = 0
Keyboard.00e3 = 0
Keyboard.00e4 = 0
Keyboard.00e5 = 0
Keyboard.00e6 = 0
Keyboard.00e7 = 0
Keyboard.0053 = 1
LED.NumLock = 1

report (size 8) (unnumbered)
report 0 (size 8) =  00 00 00 00 00 00 00 00
Keyboard.00e0 = 0
Keyboard.00e1 = 0
Keyboard.00e2 = 0
Keyboard.00e3 = 0
Keyboard.00e4 = 0
Keyboard.00e5 = 0
Keyboard.00e6 = 0
Keyboard.00e7 = 0
Keyboard.0053 = 0

report (size 8) (unnumbered)
report 0 (size 8) =  00 00 59 00 00 00 00 00
Keyboard.00e0 = 0
Keyboard.00e1 = 0
Keyboard.00e2 = 0
Keyboard.00e3 = 0
Keyboard.00e4 = 0
Keyboard.00e5 = 0
Keyboard.00e6 = 0
Keyboard.00e7 = 0
Keyboard.0059 = 1

report (size 8) (unnumbered)
report 0 (size 8) =  00 00 53 00 00 00 00 00
Keyboard.00e0 = 0
Keyboard.00e1 = 0
Keyboard.00e2 = 0
Keyboard.00e3 = 0
Keyboard.00e4 = 0
Keyboard.00e5 = 0
Keyboard.00e6 = 0
Keyboard.00e7 = 0
Keyboard.0059 = 0
Keyboard.0053 = 1
LED.NumLock = 0

report (size 8) (unnumbered)
report 0 (size 8) =  00 00 00 00 00 00 00 00
Keyboard.00e0 = 0
Keyboard.00e1 = 0
Keyboard.00e2 = 0
Keyboard.00e3 = 0
Keyboard.00e4 = 0
Keyboard.00e5 = 0
Keyboard.00e6 = 0
Keyboard.00e7 = 0
Keyboard.0053 = 0
```

If I press a button that does work in MyhtFrontend:


```
Event: time 1285969823.990400, type 4 (Misc), code 4 (ScanCode), value 70050
Event: time 1285969823.990447, type 1 (Key), code 105 (Left), value 1
Event: time 1285969823.990454, -------------- Report Sync ------------
Event: time 1285969824.126424, type 4 (Misc), code 4 (ScanCode), value 70050
Event: time 1285969824.126457, type 1 (Key), code 105 (Left), value 0
Event: time 1285969824.126462, -------------- Report Sync ------------

```

So this works fine and also the output of the HID raw device is ok.

Any idea what is going on here and how to fix this. 
I want to avoid those lirc-based mce_usb drivers and use this as HID (it has a mouse input device also)

THanks for your help

---

