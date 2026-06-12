---
title: "Wiimote crashes mythfrontend after upgrade"
date: 2009-04-27
forum: Mythbuntu
---

### Post by Triptol on 2009-04-27
I already posted this thread [here]("http://http://ubuntuforums.org/showthread.php?t=1138218"), but since I didn't get any reaction, I thought this forum probably better, hence the repost.

Before I upgraded to Jaunty I had a working Mythbuntu installation with Wiimote control using cwiid (wminput).

After the upgrade every button click on the wiimote crashes the mythfrontend.

I have checked the wminput settings with wmgui and everything seems fine.

So I started mythfrontend with the following options:

```
mythfrontend --verbose all
```

This is what I get as soon as I push a button on the wiimote:

```
mythfrontend.real: Fatal IO error: client killed
2009-04-26 13:38:54.280 MythSocket: readyread thread exit
```

I have no clue what my next steps could be. Ideas are appreciated!

My /etc/cwiid/wminput/buttons

```
#buttons

#Wiimote.A              = BTN_LEFT
Wiimote.A               = KEY_ENTER
#Wiimote.B              = BTN_RIGHT
Wiimote.B               = KEY_ESC
Wiimote.Up              = KEY_UP
Wiimote.Down            = KEY_DOWN
Wiimote.Left            = KEY_LEFT
Wiimote.Right           = KEY_RIGHT
Wiimote.Minus           = KEY_LEFTBRACE
Wiimote.Plus            = KEY_RIGHTBRACE
Wiimote.Home            = KEY_Y
#Wiimote.1              = KEY_PROG1
Wiimote.1               = KEY_M
#Wiimote.2              = KEY_PROG2
Wiimote.2               = KEY_I

#Nunchuk.C              = BTN_LEFT
#Nunchuk.Z              = BTN_RIGHT

#Classic.Up             = KEY_UP
#Classic.Down   = KEY_DOWN
#Classic.Left   = KEY_LEFT
#Classic.Right  = KEY_RIGHT
#Classic.Minus  = KEY_BACK
#Classic.Plus   = KEY_FORWARD
#Classic.Home   = KEY_HOME
#Classic.A              = BTN_LEFT
#Classic.B              = BTN_RIGHT
#Classic.X              =
#Classic.Y              =
#Classic.ZL             =
#Classic.ZR             =
#Classic.L              =
#Classic.R              =
```

---

### Post by Triptol on 2009-04-28
Found it is not mythfrontend related. Somehow clicking the wiimote crashes X!

This is what I get in my Xorg.0.log after I press a button:
```
Backtrace:
0: /usr/bin/X(xorg_backtrace+0x3b) [0x813518b]
1: /usr/bin/X(xf86SigHandler+0x55) [0x80c7be5]
2: [0xb8067400]
3: /usr/bin/X(GetKeyboardValuatorEvents+0xa8) [0x80a0958]
4: /usr/bin/X(GetKeyboardEvents+0x4a) [0x80a0cda]
5: /usr/bin/X(xf86PostKeyboardEvent+0x9b) [0x80d817b]
6: /usr/lib/xorg/modules/input//evdev_drv.so [0xb5f573db]
7: /usr/bin/X [0x80c7da7]
8: /usr/bin/X [0x80b82cc]
9: [0xb8067400]
10: /usr/bin/X(Dispatch+0x7e) [0x808d2be]
11: /usr/bin/X(main+0x3bd) [0x80722ed]
12: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7c31775]
13: /usr/bin/X [0x80717a1]
Saw signal 11.  Server aborting.
(II) Nintendo Wiimote: Close
(II) UnloadModule: "evdev"
(II) Macintosh mouse button emulation: Close
(II) UnloadModule: "evdev"
 ddxSigGiveUp: Closing log
```

---

### Post by Triptol on 2009-04-29
Gave up and deinstalled cwiid and installed XWii. [http://www.resplect.com/xwii/index.php](http://www.resplect.com/xwii/index.php).

PPA packages are available as well, so installation was a breeze.

---

### Post by jape42 on 2009-05-02
I'm using wminput on a clean install of 64bit jaunty.  I've used both the radeon and radeonhd x11 drivers with no crashes so far.

jp

---

### Post by Meph1st0 on 2009-05-02
Triptol,

You're actually the first person I've seen who's actually using their Wiimote for use with Mythtv (although I'm sure there's plenty).  I've considered this but can't think of any real use for it.  My question for you then is how are you putting it to use?  What sort of cool tricks are you doing with the Wiimote that I couldn't get with a regular remote?  The biggest appeal for me is using it for web browsing.  It's got to be the best way to surf the web from the couch.  Are you using it with your Wii sensor bar?  Essentially, how are you using your Wii remote with Mythtv and how do you like it?  Should I do it too?  I gotta admit, I'm already tempted.

---

### Post by Flecko on 2009-05-03
I have my Wiimote controlling my MythTV box running 9.04 as well. No problems to report so far. Its odd that your cwiid was crashing X for you.

As for Mephisto: Look up Myth_Py_Wii on google to see some cool stuff.

---

### Post by Triptol on 2009-05-09
Hi Meph1st0,

I do have a Logitech Harmony IR Remote as well, using the Wiimote was added because it is possible. However the Wiimote does have some advantages:

[LIST]
[*]Bluetooth: it just connects better than IR does (at least with my receiver).
[*]Handling: it (almost) has all the things nescessary, athough I miss the number buttons. It is very accurate and easy for everyone to use (the kids and the wife already know how the Wii works).
[*]It is possible: I just read it could be done, so I tried it and it worked. Which is fun and adds to the geek factor. Visitors always wonder how it is done.
[/LIST]

I'm not (yet) using the Infrared capabilities. I'm thinking of building in 5 IR lights in my Mythbox using an USB adapter, but I haven't had the time to do it yet. That would really increade web capabilities.

I am using the Flack function, to bring up the menu, which is kinda fun. Motion detection is not really helpful for the rest, although I have seen some nice examples with a motion detecting mouse on linuxmce.com.

---

### Post by bcg30506 on 2009-06-01
I get this exact same crash after upgrading to jaunty.  It worked in 8.04.  I'm trying to use my Wiimote in Frets on Fire via wminput.  As soon as I try to arrow down in the main menu, X crashes.  I use the nvidia driver for the GeForce 9300.  When it worked, I used fglrx for an ATI card.

The error in Xorg.0.log is:

(II) config/hal: Adding input device Macintosh mouse button emulation
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 2.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) config/hal: Adding input device Nintendo Wiimote
(**) Nintendo Wiimote: always reports core events
(**) Nintendo Wiimote: Device: "/dev/input/event4"
(II) Nintendo Wiimote: Found x and y absolute axes
(II) Nintendo Wiimote: Found keys
(II) Nintendo Wiimote: Configuring as keyboard
(II) XINPUT: Adding extended input device "Nintendo Wiimote" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Nintendo Wiimote: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Nintendo Wiimote: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Nintendo Wiimote: xkb_layout: "us"
(**) Nintendo Wiimote: (accel) keeping acceleration scheme 1
(**) Nintendo Wiimote: (accel) filter chain progression: 2.00
(**) Nintendo Wiimote: (accel) filter stage 0: 20.00 ms
(**) Nintendo Wiimote: (accel) set acceleration profile 0

Backtrace:
0: /usr/bin/X(xorg_backtrace+0x3b) [0x813518b]
1: /usr/bin/X(xf86SigHandler+0x55) [0x80c7be5]
2: [0xb7ff6400]
3: /usr/bin/X(GetKeyboardValuatorEvents+0xa8) [0x80a0958]
4: /usr/bin/X(GetKeyboardEvents+0x4a) [0x80a0cda]
5: /usr/bin/X(xf86PostKeyboardEvent+0x9b) [0x80d817b]
6: /usr/lib/xorg/modules/input//evdev_drv.so [0xa5d103db]
7: /usr/bin/X [0x80c7da7]
8: /usr/bin/X [0x80b82cc]
9: [0xb7ff6400]
10: /usr/bin/X(Dispatch+0x7e) [0x808d2be]
11: /usr/bin/X(main+0x3bd) [0x80722ed]
12: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7bcb775]
13: /usr/bin/X [0x80717a1]
Saw signal 11.  Server aborting.
(II) Macintosh mouse button emulation: Close
(II) UnloadModule: "evdev"
(II) Nintendo Wiimote: Close
(II) UnloadModule: "evdev"
 ddxSigGiveUp: Closing log

---

### Post by Triptol on 2009-06-04
I just did an upgrade on the same box with the same hardware. It is Nvidia I am using, so it might be related to what you are seeing.

Since I have moved on I can't provice any more information.

---

### Post by bcg30506 on 2009-06-04
I got my problem solved and FoF is working great now.  The issue is the wminput driver seems to be buggy with the nvidia vdpau driver.  So I removed it and installed xwii instead.  It works fine.

---

### Post by joe_newbie on 2009-07-20
I am also experiencing X crashes when I use a non-standard buttons file in /etc/cwiid/wminput/buttons


I have created custom key mappings for mythtv which worked great with hardy, but not jaunty. wminput works fine with my integrated *intel* video chipset with standard key mappings.

for those interested here is my buttons file:

#/etc/cwiid/wminput/buttons
#buttons

Wiimote.A		= KEY_ENTER
Wiimote.B		= KEY_ESC
Wiimote.Up		= KEY_UP
Wiimote.Down	= KEY_DOWN
Wiimote.Left	= KEY_LEFT
Wiimote.Right	= KEY_RIGHT
Wiimote.Minus	= KEY_9
Wiimote.Plus	= KEY_0
Wiimote.Home	= KEY_SPACE
Wiimote.1		= KEY_KPPLUS
Wiimote.2		= KEY_KPMINUS

---

### Post by vintermann on 2009-08-24
I, too, crash X with what I would think was a perfectly reasonable wminput configuration file:

```

Classic.Up = KEY_UP
Classic.Down = KEY_DOWN
Classic.Left = KEY_LEFT
Classic.Right = KEY_RIGHT
Classic.B = KEY_LEFTALT
Classic.A = KEY_LEFTCTRL
Classic.LStick.X = ABS_X
Classic.LStick.Y = ABS_Y

```

I get this at the end of my X crash log:

```
II) config/hal: Adding input device Nintendo Wiimote
(**) Nintendo Wiimote: always reports core events
(**) Nintendo Wiimote: Device: "/dev/input/event10"
(II) Nintendo Wiimote: Found x and y absolute axes
(II) Nintendo Wiimote: Found keys
(II) Nintendo Wiimote: Configuring as keyboard
(II) XINPUT: Adding extended input device "Nintendo Wiimote" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Nintendo Wiimote: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Nintendo Wiimote: xkb_model: "pc105"
(**) Option "xkb_layout" "no"
(**) Nintendo Wiimote: xkb_layout: "no"
(**) Nintendo Wiimote: (accel) keeping acceleration scheme 1
(**) Nintendo Wiimote: (accel) filter chain progression: 2.00
(**) Nintendo Wiimote: (accel) filter stage 0: 20.00 ms
(**) Nintendo Wiimote: (accel) set acceleration profile 0
(EE) Nintendo Wiimote: Read error: No such device
(II) config/hal: removing device Nintendo Wiimote
(II) Nintendo Wiimote: Close
(II) UnloadModule: "evdev"
(II) config/hal: Adding input device Nintendo Wiimote
(**) Nintendo Wiimote: always reports core events
(**) Nintendo Wiimote: Device: "/dev/input/event10"
(II) Nintendo Wiimote: Found x and y absolute axes
(II) Nintendo Wiimote: Found keys
(II) Nintendo Wiimote: Configuring as keyboard
(II) XINPUT: Adding extended input device "Nintendo Wiimote" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Nintendo Wiimote: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Nintendo Wiimote: xkb_model: "pc105"
(**) Option "xkb_layout" "no"
(**) Nintendo Wiimote: xkb_layout: "no"
(**) Nintendo Wiimote: (accel) keeping acceleration scheme 1
(**) Nintendo Wiimote: (accel) filter chain progression: 2.00
(**) Nintendo Wiimote: (accel) filter stage 0: 20.00 ms
(**) Nintendo Wiimote: (accel) set acceleration profile 0

Backtrace:
0: /usr/X11R6/bin/X(xorg_backtrace+0x3b) [0x813518b]
1: /usr/X11R6/bin/X(xf86SigHandler+0x55) [0x80c7be5]
2: [0xb7f47400]
3: /usr/X11R6/bin/X(GetKeyboardValuatorEvents+0xa8) [0x80a0958]
4: /usr/X11R6/bin/X(GetKeyboardEvents+0x4a) [0x80a0cda]
5: /usr/X11R6/bin/X(xf86PostKeyboardEvent+0x9b) [0x80d817b]
6: /usr/lib/xorg/modules/input//evdev_drv.so [0xb768d3db]
7: /usr/X11R6/bin/X [0x80c7da7]
8: /usr/X11R6/bin/X [0x80b82cc]
9: [0xb7f47400]
10: /usr/X11R6/bin/X(Dispatch+0x7e) [0x808d2be]
11: /usr/X11R6/bin/X(main+0x3bd) [0x80722ed]
12: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7b0e775]
13: /usr/X11R6/bin/X [0x80717a1]
Saw signal 11.  Server aborting.
(II) ThinkPad Extra Buttons: Close
(II) UnloadModule: "evdev"
(II) Video Bus: Close
(II) UnloadModule: "evdev"
(II) AT Translated Set 2 keyboard: Close
(II) UnloadModule: "evdev"
(II) TPPS/2 IBM TrackPoint: Close
(II) UnloadModule: "evdev"
(II) Macintosh mouse button emulation: Close
(II) UnloadModule: "evdev"
(II) UnloadModule: "synaptics"
(II) Nintendo Wiimote: Close
(II) UnloadModule: "evdev"
(II) AIGLX: Suspending AIGLX clients for VT switch
Output LCD1 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Blank CRTC 1 success
Disable CRTC 1 success
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0xdfffd800 0xdfffd800
(II) RADEON(0):   MC_AGP_LOCATION  : 0x003f0000
(II) RADEON(0): avivo_restore !
Enable CRTC 0 success
Unblank CRTC 0 success
 ddxSigGiveUp: Closing log

```

Looks like it thinks the wiimote is a keyboard (fair enough, since it's supposed to send keypresses) but tries to set Norwegian keyboard layout for it (maybe not such a terrific idea?). Anyway, with the config file above, it does not crash right away, only when a button (not stick) on the classic controller is pressed. If I remove the last two lines of the config file, dealing with the stick, it works fine.

I'm posting this here in the hope that someone with the same problem can figure it out; I don't think it has to do with gfx cards, because as you can see I have a different one.

---

### Post by joe_newbie on 2009-11-29
Never did solve this problem. Switched to xwii which is by far easier to set up, for those looking for an alternative

---

### Post by geekyhawkes on 2009-12-15
right i must be stuipid but i cant get xwii to work on 910!  Could someone see what i am doing wrong please?

I have downloaded the tar file at this location;

[http://www.resplect.com/xwii/files/releases/2.8/XWii_2.8_source.tar.gz](http://www.resplect.com/xwii/files/releases/2.8/XWii_2.8_source.tar.gz)

I have then;

tar -zxvf XWii_2.8_source.tar.gz

Installed     
* libbluetooth-dev
* libxtst-dev

As well as the SDL/OpenGL libs.

THen cd into the Xwii directory and sudo make.  I get a couple of error 2 at the end of the compilation If i run ./start_xwii.py  then i get the profile choice but after choosing any of the profiles xwii stops saying

sh: ./xwii: not found

Any idea, or thoughts as to what i am doing wrong?

---

### Post by geekyhawkes on 2009-12-17
anyone help me out with this?

---

