---
title: "Mouse Side button not working"
date: 2010-10-08
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by tehkain on 2010-10-08
The large side button(back) on my Microsoft Intellimouse Explorer 2.0 no longer works after an upgrade to 10.10. The smaller side button(forward) atop of it works fine. I tested it with both xev and "xinput test mouse_id" and neither of them detect any click. I guess the button would be number 8 if it was detected.

I have never had an issue on any early release or distro and the mouse works great on my 10.04 install.

Output of xinput list mouse_id
```

Microsoft Microsoft Wireless Optical Desktop® 1.00	id=9	[slave  pointer  (2)]
	Reporting 6 classes:
		Class originated from: 9
		Buttons supported: 13
		Button labels: Button Left Button Middle Button Right Button Wheel Up Button Wheel Down Button Horiz Wheel Left Button Horiz Wheel Right Button Side Button Extra Button Unknown Button Unknown Button Unknown Button Unknown
		Button state:
		Class originated from: 9
		Keycodes supported: 248
		Class originated from: 9
		Detail for Valuator 0:
		  Label: Rel X
		  Range: -1.000000 - -1.000000
		  Resolution: 1 units/m
		  Mode: relative
		Class originated from: 9
		Detail for Valuator 1:
		  Label: Rel Y
		  Range: -1.000000 - -1.000000
		  Resolution: 1 units/m
		  Mode: relative
		Class originated from: 9
		Detail for Valuator 2:
		  Label: Rel Misc
		  Range: -1.000000 - -1.000000
		  Resolution: 1 units/m
		  Mode: relative
		Class originated from: 9
		Detail for Valuator 3:
		  Label: None
		  Range: -1.000000 - -1.000000
		  Resolution: 1 units/m
		  Mode: relative

```

list-props output
```

Device 'Microsoft Microsoft Wireless Optical Desktop® 1.00':
	Device Enabled (121):	1
	Coordinate Transformation Matrix (123):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	Device Accel Profile (243):	0
	Device Accel Constant Deceleration (244):	1.000000
	Device Accel Adaptive Deceleration (245):	1.000000
	Device Accel Velocity Scaling (246):	10.000000
	Evdev Reopen Attempts (238):	10
	Evdev Axis Inversion (247):	0, 0
	Evdev Axes Swap (249):	0
	Axis Labels (250):	"Rel X" (131), "Rel Y" (132), "Rel Misc" (242), "None" (0)
	Button Labels (251):	"Button Left" (124), "Button Middle" (125), "Button Right" (126), "Button Wheel Up" (127), "Button Wheel Down" (128), "Button Horiz Wheel Left" (129), "Button Horiz Wheel Right" (130), "Button Side" (240), "Button Extra" (241), "Button Unknown" (239), "Button Unknown" (239), "Button Unknown" (239), "Button Unknown" (239)
	Evdev Middle Button Emulation (252):	2
	Evdev Middle Button Timeout (253):	50
	Evdev Wheel Emulation (254):	0
	Evdev Wheel Emulation Axes (255):	0, 0, 4, 5
	Evdev Wheel Emulation Inertia (256):	10
	Evdev Wheel Emulation Timeout (257):	200
	Evdev Wheel Emulation Button (258):	4
	Evdev Drag Lock Buttons (259):	0

```

Anyone else having this issue and know of a way to solve it?

---

