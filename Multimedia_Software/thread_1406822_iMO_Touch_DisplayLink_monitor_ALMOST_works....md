---
title: "iMO Touch DisplayLink monitor ALMOST works..."
date: 2010-02-14
forum: Multimedia Software
---

### Post by solaria on 2010-02-14
I've got the iMO mostly working, but there are a few gaps that keep it from being actually useful.

First, the stuff that works:

Gave up trying for one display with two screens, and instead went with 2 displays.  Started the USB display with:

```
xinit /usr/bin/fluxbox -geometry 800x480+0+40 -display :1.0 -- /usr/bin/X :1 -novtswitch -sharevts -layout USBScreen -dpi 75 >/tmp/dl1.log &
sleep 10
x2x -east -to :1 &
```

The "-layout" option references a ServerLayout in xorg.conf:

```

Section "ServerLayout"
   Identifier "USBScreen"
   Screen  "DisplayLinkScreen"
   InputDevice "DummyMouse"
   InputDevice "DummyKeyboard"
   Option "AllowMouseOpenFail" "True"
   Option "AllowEmptyInput" "false"
   Option "AutoAddDevices" "false"
   Option "AutoEnableDevices" "false"
EndSection
```

Need the "Dummy" InputDevices, otherwise input will go to both displays.  The Dummy devices reference a "void" driver that doesn't exist, so need the "AllowMouseOpenFail" option to keep xinit from aborting at startup.

Had trouble early on with EDID errors when the USB screen initialized.  Changed DisplayLinkDevice frame buffer option to:

```
Option "fbdev" "/dev/fb1"
```

...and everything started falling into place.

In terms of drivers, looks like you need:

udlfb-0.2.3_and_xf86-video-displaylink-0.3.tar

...but only for the xf86 part, not the udlfb part.

Also:

displaylink-mod-0.3.tar
libdlo-0.1.2.tar

With all that in place, it works pretty well for things like MythTV or Miro, etc...

That's the good news.  The bad news is the stuff that doesn't work:

_Menus within applications do not work._

Applications like f-spot, Audacity,etc... clicking on the application menu items ("File", "Edit","View",...) does nothing.
well, OK, not exactly nothing:  a thin, black line will float above the application window.  The length of the line changes depending on which menu item was clicked, but the sub-menu items are not visible.

_TouchPad x-axis is reversed_

Move you finger from left-to-right, the cursor moves from right-to-left.  Tried "InvX", "InvertX", "SwapX", but so far it looks like evtouch is ignoring all options.  Xinput list-props only shows "enabled" as a property.

Actually, even if this worked, the touch pad would still be a problem.  Right now the touch pad input goes to the currently active screen.  Ideally I'd like the touch pad to generate x-values to the right of the main screen so that it controls the USB screen, not the main screen.  Might be an option that controls this, except evtouch ignores all options.

_Suspend kills the USB bus_

If the PC goes into suspend while the USB display is active, when it returns all USB devices are dead;  USB monitor, mouse, keyboard.  Hard reset to clear.

Also, if the USB display is idle long enough, it turns off the display.  Moving the mouse over to that display then causes a USB failure and a hard reset...


Anyone have any suggestions to solve any of these problems?  Might be cool to use it as an out-board screen, but not if the application menus don't work, the touch pad is backwards, and it locks up the system...

---

### Post by bluecobaltss06 on 2010-03-03
Just curious if you were able to get the monitor fully operational with ubuntu yet.  I wanna put this monitor in my car with a mini PC under the seat but hate hate hate windows.

---

### Post by Ad1217 on 2010-12-26
I am also curious if this display works. I think it would be really useful but don't want to spend $200 to buy it if it does not work.

---

