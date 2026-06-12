---
title: "wacom bamboo touch and pen pointer's speed"
date: 2011-02-27
forum: Multimedia Software
---

### Post by surryr on 2011-02-27
Hello, i have wacom bamboo touch and pen. i prefer relative mode and got a problem: my poiner is too fast. Is there any way to slow down pointer in relative mode?

Sorry for my terrible english :)

Thank u for help.

---

### Post by surryr on 2011-02-27
Sorry, i found solution using xinput.
[LIST]
First, i got my device list 
```
xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Logitech USB RECEIVER                   	id=8	[slave  pointer  (2)]
&#9116;   &#8627; Wacom BambooFun 2FG 4x5 Pen eraser      	id=11	[slave  pointer  (2)]
&#9116;   &#8627; Wacom BambooFun 2FG 4x5 Pen stylus      	id=12	[slave  pointer  (2)]
&#9116;   &#8627; Wacom BambooFun 2FG 4x5 Finger pad      	id=13	[slave  pointer  (2)]
&#9116;   &#8627; Wacom BambooFun 2FG 4x5 Finger touch    	id=14	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; BTC USB Multimedia Keyboard             	id=9	[slave  keyboard (3)]
    &#8627; BTC USB Multimedia Keyboard     

```
i need next devices: id=11 and id=12
[/LIST]
[LIST]
Next, i listed properties: 
```
xinput watch-props 11
Device 'Wacom BambooFun 2FG 4x5 Pen eraser':
	Device Enabled (142):	1
	Coordinate Transformation Matrix (144):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	Device Accel Profile (269):	0
	Device Accel Constant Deceleration (270):	1.000000
	Device Accel Adaptive Deceleration (271):	1.000000
	Device Accel Velocity Scaling (272):	10.000000
	Wacom Tablet Area (292):	0, 0, 14720, 9200
	Wacom Rotation (293):	0
	Wacom Pressurecurve (294):	0, 0, 100, 100
	Wacom Serial IDs (295):	209, 0, 10, 0
	Wacom Capacity (296):	-1
	Wacom Pressure Threshold (297):	27
	Wacom Sample and Suppress (298):	2, 4
	Wacom Enable Touch (299):	0
	Wacom Enable Touch Gesture (300):	0
	Wacom Touch Gesture Parameters (301):	50, 20, 250
	Wacom Tool Type (302):	"ERASER" (286)
	Wacom Button Actions (303):	"None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0)
	Wacom Debug Levels (304):	0, 0

```
I need change: Device Accel Constant Deceleration (270)
[/LIST]
[LIST]
and last, a just changed this property to 2.5 value:
```
xinput set-prop 12 270 2.5
xinput set-prop 11 270 2.5
```
[/LIST]

This solution works for me. Thank u.

---

