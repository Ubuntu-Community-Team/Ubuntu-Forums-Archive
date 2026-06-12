---
title: "Still can not get my eGalaxy to work..."
date: 2010-04-17
forum: Multimedia Software
---

### Post by e-San on 2010-04-17
Hi!

I bought touchscreen 0.4 with usb hub to connect to camera port.
I at last put it together and into my asus eee 900. I had to swich wires from 1-2-3-4 to 4-3-2-1 since camera connector (USB interface) is switched. I tested all this stuff on usb adapter. When i was testing it (before i put it inside) i checked many times when green light blinks on touch - i belive there is everything all right. So it came to install it on ubuntu.

I compiled two or three kernel with modules and built in egalax driver, tried egalax installer and other things, but i still can not get it to work.

Tried TKCalc, tried few ways in xorg but it does not work. My xorg tries:
```
san@eeepc:~$ sudo nano /etc/X11/xorg.conf
[sudo] password for san: 
san@eeepc:~$ cat /etc/X11/xorg.conf
Section "ServerLayout"
#        InputDevice "EETI" "SendCoreEvents"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
#	InputDevice    "touchscreen0"   "SendCoreEvents" 
#	InputDevice    "touchscreen1"   "SendCoreEvents" 
#	InputDevice    "touchscreen3"   "SendCoreEvents" 
	InputDevice    "touchscreen4"   "SendCoreEvents" 
#	InputDevice    "touchscreen2"   "SendCoreEvents" 
 	Option         "AllowMouseOpenFail" "true"
	InputDevice "dummy"
EndSection

Section "InputDevice"
    Identifier "dummy"
    Driver "void"
    Option "Device" "/dev/input/mice"
EndSection

Section "InputDevice"
        Identifier      "touchscreen4"
        Driver  "egalax"
        Option  "Device"        "/dev/input/event7" # stands for the event number your touchscreen is on
        Option  "DeviceName"    "touchscreen4"
        Option  "MinX" "8" 
        Option  "MinY" "8"
        Option  "MaxX" "256"
        Option  "MaxY" "256"
        Option  "SwapY"         "1"
        Option  "ReportingMode" "Raw"
        Option  "Emulate3Buttons"
        Option  "Emulate3Timeout"       "50"
        Option  "SendCoreEvents"
EndSection

Section "InputDevice"
        Identifier      "touchscreen3"
        Driver  "egalax"
        Option  "Device"        "/dev/input/mouse1" # stands for the event number your touchscreen is on
        Option  "DeviceName"    "touchscreen3"
#        Option  "MinX" "8" 
#        Option  "MinY" "8"
#        Option  "MaxX" "1144"
#        Option  "MaxY" "760"
        Option  "SwapY"         "1"
#        Option  "ReportingMode" "Raw"
#        Option  "Emulate3Buttons"
#        Option  "Emulate3Timeout"       "50"
#        Option  "SendCoreEvents"
EndSection

Section "InputDevice"
        Identifier      "touchscreen0"
        Driver  "evtouch"
        Option  "Device"        "/dev/input/mouse1" # stands for the event number your touchscreen is on
        Option  "DeviceName"    "touchscreen0"
#        Option  "MinX" "8" 
#        Option  "MinY" "8"
#        Option  "MaxX" "1144"
#        Option  "MaxY" "760"
        Option  "SwapY"         "1"
#        Option  "ReportingMode" "Raw"
#        Option  "Emulate3Buttons"
#        Option  "Emulate3Timeout"       "50"
#        Option  "SendCoreEvents"
EndSection

Section "InputDevice"
        Identifier      "touchscreen1"
        Driver  "evtouch"
        Option  "Device"        "/dev/input/event7" # stands for the event number your touchscreen is on
        Option  "DeviceName"    "touchscreen1"
#        Option  "MinX" "8" 
#        Option  "MinY" "8"
#        Option  "MaxX" "1144"
#        Option  "MaxY" "760"
        Option  "SwapY"         "1"
#        Option  "ReportingMode" "Raw"
#        Option  "Emulate3Buttons"
#        Option  "Emulate3Timeout"       "50"
#        Option  "SendCoreEvents"
EndSection

Section "InputDevice"
        Identifier      "touchscreen2"
        Driver  "evtouch"
        Option  "Device"        "/dev/input/event8" # stands for the event number your touchscreen is on
        Option  "DeviceName"    "touchscreen2"
#        Option  "MinX" "8" 
#        Option  "MinY" "8"
#        Option  "MaxX" "1144"
#        Option  "MaxY" "760"
        Option  "SwapY"         "1"
#        Option  "ReportingMode" "Raw"
#        Option  "Emulate3Buttons"
#        Option  "Emulate3Timeout"       "50"
#        Option  "SendCoreEvents"
EndSection

### Touch Configuration Beginning ###
Section "InputDevice"
        Identifier "EETI"
        Driver "egalax"
        Option "Device" "usbauto"
        Option "Parameters" "/var/lib/eeti.param"
        Option "ScreenNo" "0"
        Option "SkipClick" "1"
EndSection
### Touch Configuration End ###

Section "Files"
	ModulePath   "/usr/lib/xorg/modules"
(...) (fonts)
	FontPath     "built-ins"
EndSection

Section "Module"
(...)
EndSection

Section "InputDevice" (kbd)
(...)
EndSection

Section "InputDevice" (touchpad)
Section "Files"
	ModulePath   "/usr/lib/xorg/modules"
(...) (fonts)
	FontPath     "built-ins"
EndSection
(...)
EndSection

Section "Monitor"
(...)
EndSection

Section "Device" (intel graphic)
(...)
EndSection

Section "Screen"
(...)
EndSection
```
i organized somehow quoted xorg to make it easier to read.

at the moment, when i try 'TKCalc /dev/input/event7 draw', it 
jumps, 
when i move verticaly it sometimes (much too often) draws horizontaly - i do not find this as problem since there is option in xorg to rotate it,
it draws only on left-down almost-quarter, even when i touch on right upper-corner,
it does not respond on left-down edges corner.

I belive there is problem with drivers or even with controller - beacose of last one. i wont rotate sinc it jumps to much and i do not know for sure.

Tried other input files - event7 seems to be most accurate.

Guys, help! I bought it almost half year ago!

Regards!

edit.
...and part of my xorg.log
```
(--) Mouse0: touchpad found
(**) Option "CorePointer"
(**) Mouse0: always reports core events
(II) XINPUT: Adding extended input device "Mouse0" (type: TOUCHPAD)
(**) Mouse0: (accel) keeping acceleration scheme 1
(**) Mouse0: (accel) filter chain progression: 2.00
(**) Mouse0: (accel) filter stage 0: 20.00 ms
(**) Mouse0: (accel) set acceleration profile 0
(--) Mouse0: touchpad found
State: S_UNTOUCHED	Action: No Action		Button: 0
State: S_TOUCHED	Action: No Action		Button: 0
State: S_LONGTOUCHED	Action: down		Button: 1
State: S_MOVING	Action: No Action		Button: 0
State: S_MAYBETAPPED	Action: up		Button: 1
State: S_ONEANDAHALFTAP	Action: down		Button: 3
(**) Option "MinX" "1"
(**) Option "MaxX" "1200"
(**) Option "MinY" "1"
(**) Option "MaxY" "650"
(**) Option "Emulate3Buttons" "no"
(**) Option "SwapX" "1"
(**) Option "DeviceName" "touchscreen5"
(**) Option "SendCoreEvents"
(**) touchscreen5: always reports core events
(II) XINPUT: Adding extended input device "touchscreen5" (type: TOUCHSCREEN)
(**) touchscreen5: (accel) keeping acceleration scheme 1
(**) touchscreen5: (accel) filter chain progression: 2.00
(**) touchscreen5: (accel) filter stage 0: 20.00 ms
(**) touchscreen5: (accel) set acceleration profile 0
(**) Option "Device" "/dev/input/event7"
(II) LoadModule: "void"
(WW) Warning, couldn't open module void
(II) UnloadModule: "void"
(EE) Failed to load module "void" (module does not exist, 0)
(EE) No input driver matching `void'
[config/dbus] couldn't take over org.x.config: org.freedesktop.DBus.Error.AccessDenied (Connection ":1.408" is not allowed to own the service "org.x.config.display0" due to security policies in the configuration file)
(II) config/hal: Adding input device eGalax Inc. Touch
(II) Synaptics touchpad driver version 1.1.2
(**) Option "Device" "/dev/input/event7"
(**) Option "SHMConfig" "On"
(**) Option "EmulateTwoFingerMinZ" "90"
(**) Option "VertTwoFingerScroll" "1"
(**) Option "HorizTwoFingerScroll" "1"
(**) Option "TapButton1" "1"
(**) Option "TapButton2" "2"
(**) Option "TapButton3" "3"
(--) eGalax Inc. Touch: no supported touchpad found
(EE) eGalax Inc. Touch Unable to query/initialize Synaptics hardware.
(EE) PreInit failed for input device "eGalax Inc. Touch"
(II) UnloadModule: "synaptics"
(EE) config/hal: NewInputDeviceRequest failed (8)
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 2.2.5
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
```

---

### Post by Horatio on 2010-04-29
Search the forums for "touchkit" for better results.

or goto [http://home.eeti.com.tw/web20/eGalaxTouchDriver/linuxDriver.htm](http://home.eeti.com.tw/web20/eGalaxTouchDriver/linuxDriver.htm)
and follow the readme or pdf guide. You should only need to run the setup.sh.

I am currently testing this with [http://home.eeti.com.tw/web20/drivers/touch_driver/Linux/20100413/eGalaxTouch-3.01.4001-32b-k26.tar.gz](http://home.eeti.com.tw/web20/drivers/touch_driver/Linux/20100413/eGalaxTouch-3.01.4001-32b-k26.tar.gz), and so far this is the only drive that has worked in 9.04. I don't remember if I tried the stable versions from home.eeti.com.tw, but having looked at my email, I think I did. I'll likely retry later.

Although it is only working to most of my expectations. I can't draw with the touch screen because as I move the stylus across the screen( or in a curved path) the pointer jumps from the corner and back to the next point on the screen. So good luck.

---

### Post by e-San on 2010-05-03
> or goto [http://home.eeti.com.tw/web20/eGalax...inuxDriver.htm](http://home.eeti.com.tw/web20/eGalax...inuxDriver.htm)
and follow the readme or pdf guide. You should only need to run the setup.sh.

> tried egalax installer and other things, but i still can not get it to work.

> Although it is only working to most of my expectations. I can't draw with the touch screen because as I move the stylus across the screen( or in a curved path) the pointer jumps from the corner and back to the next point on the screen. So good luck.

> at the moment, when i try 'TKCalc /dev/input/event7 draw', it 
jumps,

meybe some constructive response?
does it work on windows?

EDIT. Today i tried to configure it again. Since i installed Ubuntu 10.04 with original kernel i have /dev/input/event6 wich shows properly signs when touching touchscreen. 
i installed xorg evtouch package and added this to my xorg.conf:

```
Section "ServerLayout"
        InputDevice    "eGalax"
EndSection


Section "InputDevice"
    Identifier "eGalax"
    Driver "evtouch"
    Option "Device" "/dev/input/event6"
    Option "DeviceName" "eGalax Touch Screen"
    Option "MinX" "85"
    Option "MinY" "260"
    Option "MaxX" "1900"
    Option "MaxY" "1845"
    Option "ReportingMode" "Raw"
    Option "Emulate3Buttons"
    Option "Emulate3Timeout" "50"
    Option "SendCoreEvents" "On"
    Option "SwapX" "On"
EndSection
```

and now it works fine!
for getting Min/Max X/Y i suggest to use 'xinput test' command. You will find the way. If you move stylus from left to right and pointer runs in opossite, try commenting SwapX option (SwapY for verticaly movements).

in the end, i will remove Emulate3Buttons option snce i do not like to use it.

sorry for m bad english, 
Regards.

---

### Post by e-San on 2010-06-20
Hi!

I got it to work, but, since it is mobile computer i prefer to swich off sometimes my touchscreen.
But, when i do so and reconnect ts, it work like it was not calibratet (does not use xorg.conf).

Where are files wich should act as configuration files for new devices?

Regards!

p.s. the final solution to get it to work is: blacklist usbtouchscreen and enable usbhid module.

---

