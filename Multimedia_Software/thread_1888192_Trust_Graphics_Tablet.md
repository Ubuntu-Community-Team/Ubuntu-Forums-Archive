---
title: "Trust Graphics Tablet"
date: 2011-11-28
forum: Multimedia Software
---

### Post by ayenack on 2011-11-28
Hello all.

I've just bought a Trust Slimline Widescreen Graphics Tablet and am wondering what functionality I can get out of it on Ubuntu.

It works OK with GIMP but does not have pressure sensitivity or many of the other features that Windows has... So I was wondering if anyone has one of these tabs (or something like) and has edited their xorg (or any other config file) to get more functionality out of it.

When I run:-

```
cat /sys/bus/usb/devices/*/product
```

I get Slim Tablet.


Thanks for any help.

---

### Post by Favux on 2011-11-28
Hi ayenack,

Should say more than "Slim Tablet" so we know what driver to use.  Like maybe Waltop?

What is the ouput in a terminal of?
```
xinput list
```
And what's the tablet line in?
```
lsusb
```

---

### Post by ayenack on 2011-11-28
Hello Favux, thanks for the reply.

1, WALTOP International Corp. Slim Tablet stylus	id=14	[slave  pointer  (2)]


2, WALTOP International Corp. Slim Tablet stylus	id=14	[slave  pointer  (2)]

You're correct WALTOP does this help?

---

### Post by Favux on 2011-11-28
Sure, it depends on the Ubuntu release you're using.  The Waltop tablets are suppose to use the Wacom X driver but that got broken in Lucid so you need to use the WizardPen X driver.  See the [Waltop tablet HOW TO]("http://ubuntuforums.org/showthread.php?t=1595648").

By the way the lsusb tablet line should also have the Vendor and Product IDs.

---

### Post by ayenack on 2011-11-29
Thanks for that Favux.

I'll follow your tutorial and report back.

I'm running 11.10 BTW.


> By the way the lsusb tablet line should also have the Vendor and Product IDs. 

You're right, edited it out by mistake.

**ID 172f:0034**

---

### Post by Favux on 2011-11-29
OK.

The reason there's nothing on the tutorial for Oneiric is that I haven't had enough feedback from folks trying to set up Waltops in Oneiric.

As long as the match is made to WALTOP in a wacom.conf it should work, I hope.  If you can, could you show me the default /usr/share/X11/xorg.conf.d/50-wacom.conf?  Also some of the Slimline's had deformed descriptors from the kernel so there might be a problem with the match.  To check for the keywords what is the output of:
```
xinput list
```
with the tablet plugged in?

And:
Vendor ID (Waltop) = 172f
Product ID (Trust Slimline Widescreen Graphics Tablet) = 0034

---

### Post by ayenack on 2011-11-29
No problem.

1, 50-wacom.conf

[B]Section "InputClass"
	Identifier "Wacom class"
	MatchProduct "Wacom|WALTOP|WACOM|Hanwang|ISD-V4"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
EndSection

Section "InputClass"
	Identifier "Wacom serial class"
	MatchProduct "Serial Wacom Tablet"
	Driver "wacom"
EndSection

Section "InputClass"
        Identifier "Wacom serial class identifiers"
        MatchProduct "WACf|FUJ02e5|FUJ02e7|FUJ02e9"
        Driver "wacom"
EndSection


# N-Trig Duosense Electromagnetic Digitizer
Section "InputClass"
	Identifier "Wacom N-Trig class"
	MatchProduct "HID 1b96:0001|N-Trig Pen"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
	Option "Button2" "3"
EndSection[/B]

2, Full output from xinput.list with device plugged in. Not much help.

[B]&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; ImPS/2 Generic Wheel Mouse              	id=13	[slave  pointer  (2)]
&#9116;   &#8627; WALTOP International Corp. Slim Tablet stylus	id=14	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; USB 2.0 UVC VGA WebCam                  	id=10	[slave  keyboard (3)]
    &#8627; Eee PC WMI hotkeys                      	id=11	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=12	[slave  keyboard (3)]

[/B]

---

### Post by Favux on 2011-11-29
Alright, so the default 50-wacom.conf already has a WALTOP match.  So it should work out of the box without you having to do anything.  I gather it isn't working?

It appears to be on the Wacom X driver because 'stylus' is appended to the name in *xinput list* and it looks like the match to the keyword WALTOP should be good.  But let's see if it is actually on the Wacom X driver.  What is the output of?
```
xinput list-props "WALTOP International Corp. Slim Tablet stylus"
```
and also:
```
xsetwacom list
```

---

### Post by ayenack on 2011-11-29
No, it's working but it does not seem to have full features as in Windows, pressure does not seem to make any difference etc. Although looking through the output of 1 pressure features seem to be enabled, and by the looks of it I'll need to config the other features?

1, xinput list-props "WALTOP International Corp. Slim Tablet stylus"

[B]Device 'WALTOP International Corp. Slim Tablet stylus':
	Device Enabled (135):	1
	Coordinate Transformation Matrix (137):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	Device Accel Profile (255):	0
	Device Accel Constant Deceleration (256):	1.000000
	Device Accel Adaptive Deceleration (257):	1.000000
	Device Accel Velocity Scaling (258 ):	10.000000
	Wacom Tablet Area (504):	0, 0, 20000, 12500
	Wacom Rotation (505):	0
	Wacom Pressurecurve (506):	0, 0, 100, 100
	Wacom Serial IDs (507):	52, 0, 2, 0
	Wacom Capacity (508 ):	-1
	Wacom Pressure Threshold (509):	27
	Wacom Sample and Suppress (510):	2, 4
	Wacom Enable Touch (511):	0
	Wacom Hover Click (512):	0
	Wacom Enable Touch Gesture (513):	0
	Wacom Touch Gesture Parameters (514):	50, 20, 250
	Wacom Tool Type (515):	"STYLUS" (503)
	Wacom Button Actions (516):	"None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0)
	Wacom Debug Levels (517):	0, 0[/B]

2,** WALTOP International Corp. Slim Tablet stylus	id: 14	type: STYLUS**

BTW. I think you know this but... I haven't tried your tutorial. have not had time to read through it as of yet and not sure I'll need to do it now as you pointed out the tablet is working just wondering if I can get more features working on it.

---

### Post by Favux on 2011-11-29
OK.  Well in Gimp (Edit > Preferences) and Inkscape you have to set the extended input device stylus to screen to enable pressure.  Have you done that?  I think in MyPaint and Xournal pressure should just work.  You're right list-props shows pressure is enabled and set to default i.e. linear.

You should be able to configure pressure with an xsetwacom command or through the new Wacom tablet applet in System Settings.  See:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration#gnome-settings-daemon](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration#gnome-settings-daemon)  and [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xsetwacom#PressureCurve](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xsetwacom#PressureCurve)
[http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Category:HOWTO](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Category:HOWTO)

You should also be able to set your two stylus buttons.

---

### Post by ayenack on 2011-11-29
> OK. Well in Gimp (Edit > Preferences) and Inkscape you have to set the extended input device stylus to screen to enable pressure. Have you done that?

No I have not done that. Yeah... I feel a bit silly now. LOL.

When I first tried the Wacom applet in System Settings in came up as no device detected and just tried it again and got same thing.

But it is working. I'll take a look at the links you posted try to get the stylus buttons working and report back. I'm also going to have a go at getting the Action buttons working on the peripheral of the tab don't think it should be that hard.

Thanks for all your help so far.

---

### Post by ayenack on 2011-11-29
OK in GIMP I have changed settings as you suggested.

Went to:-

**Edit**>**Preferences**>**Input Devices**>**Configure Extended Input Devices**

In drop down menu set it to:-

**WALTOP International Corp. Slim Tablet Stylus**

In drop down menu 'right' set it to:-

**Mode>Window**

If I set it to screen mode it draws lines from the screen to the drawing window so I end up with lines I didn't want. Pressure now works brilliantly and the stylus buttons seem to be working out of the box also.

Now all I need to do is set up the action buttons on the edge of the tablets drawing area.


I'll stick the tablet on a more powerful desktop and I'm away.

Thanks for all your help and guidance Favux.

---

### Post by Favux on 2011-11-29
Sounding good.  :)

The lines aren't a set up problem but due to a bug in Oneiric:  [https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/863154](https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/863154)

The action buttons aren't supported currently because as far as I know no one has written code to support them.  Not sure what signal they're sending.  That's what you'd need to start with.

---

### Post by ayenack on 2011-11-29
Taking a shot in the dark here but wouldn't changing this:-

[B]Device 'WALTOP International Corp. Slim Tablet stylus':
	Device Enabled (135):	1
	Coordinate Transformation Matrix (137):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000[/B]

To this:-

[B]Device 'WALTOP International Corp. Slim Tablet stylus':
	Device Enabled (135):	1
	Coordinate Transformation Matrix (137):	0.000000, 0.000000, 0.000000, 0.000000, 0.000000, 0.000000, 0.000000, 0.000000, 0.000000[/B]

Solve the line problem?

BTW. Installed MyPaint and Xournal great apps. Thanks.

---

### Post by Favux on 2011-11-29
No CTM is for determining where tablet active area shows up on a monitor, see:  [http://ubuntuforums.org/showthread.php?t=1656089](http://ubuntuforums.org/showthread.php?t=1656089)  So you want it as the identity matrix and if you changed it to all zeros you'd break things.

If you want text entry from the tablet check out CellWriter too.

---

