---
title: "Overly sensetive touchpad"
date: 2019-03-24
forum: MINT
---

### Post by LastDino on 2019-03-24
Usually on Linux I do get slightly more sensitive touchpad, but on Mint 19.1 (Tessa) things have moved to another level, as I type this I'm pressing half the buttons in tools tab of thread post and I've to correct them again and again, that's how bad it is. I've to literally keep my hands in air while typing and not rest them around touchpad to avoid touching anything.I've reduced settings in UI touchpad setting, but still too sensitive.



I did little googling and found this command to get settings for this here is it
```
xinput list-props 15
```

Here is output
```

Device 'SynPS/2 Synaptics TouchPad':
    Device Enabled (143):    1
    Coordinate Transformation Matrix (145):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (274):    1
    Device Accel Constant Deceleration (275):    2.500000
    Device Accel Adaptive Deceleration (276):    1.000000
    Device Accel Velocity Scaling (277):    12.500000
    Synaptics Edges (297):    1618, 5366, 1356, 4536
    Synaptics Finger (298):    25, 30, 0
    Synaptics Tap Time (299):    180
    Synaptics Tap Move (300):    251
    Synaptics Tap Durations (301):    180, 180, 100
    Synaptics ClickPad (302):    0
    Synaptics Middle Button Timeout (303):    75
    Synaptics Two-Finger Pressure (304):    282
    Synaptics Two-Finger Width (305):    7
    Synaptics Scrolling Distance (306):    114, 114
    Synaptics Edge Scrolling (307):    1, 0, 0
    Synaptics Two-Finger Scrolling (308):    1, 0
    Synaptics Move Speed (309):    1.000000, 1.750000, 0.035014, 0.000000
    Synaptics Off (310):    0
    Synaptics Locked Drags (311):    0
    Synaptics Locked Drags Timeout (312):    5000
    Synaptics Tap Action (313):    2, 3, 0, 0, 1, 3, 0
    Synaptics Click Action (314):    1, 1, 0
    Synaptics Circular Scrolling (315):    0
    Synaptics Circular Scrolling Distance (316):    0.100000
    Synaptics Circular Scrolling Trigger (317):    0
    Synaptics Circular Pad (318):    0
    Synaptics Palm Detection (319):    0
    Synaptics Palm Dimensions (320):    10, 200
    Synaptics Coasting Speed (321):    20.000000, 50.000000
    Synaptics Pressure Motion (322):    30, 160
    Synaptics Pressure Motion Factor (323):    1.000000, 1.000000
    Synaptics Resolution Detect (324):    1
    Synaptics Grab Event Device (325):    0
    Synaptics Gestures (326):    1
    Synaptics Capabilities (327):    1, 0, 1, 1, 1, 1, 1
    Synaptics Pad Resolution (328):    76, 44
    Synaptics Area (329):    0, 0, 0, 0
    Synaptics Noise Cancellation (330):    28, 28
    Device Product ID (267):    2, 7
    Device Node (266):    "/dev/input/event8"

```
 
I assume, I've to change settings in "Synaptics Finger (298):    25, 30, 0"
But I'm not able to change them, how to do that? pls help

---

