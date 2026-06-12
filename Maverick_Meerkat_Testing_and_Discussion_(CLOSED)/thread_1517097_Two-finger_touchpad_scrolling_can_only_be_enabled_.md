---
title: "Two-finger touchpad scrolling can only be enabled through gconf"
date: 2010-06-24
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Starks on 2010-06-24
The option is greyed out in the mouse and touchpad settings.

The only thing that works to enable it is this:

gconftool-2 --set /desktop/gnome/peripherals/touchpad/scroll_method --type int "2"

---

### Post by arrow.69 on 2010-08-30
For me even that doesn't work.  I know my touchpad supports two-finger scrolling, since it worked in Lucid.

I used to simply run a script which would do

xinput set-prop 12 272 0 0 0  (disabled edge scrolling on touchpad)
xinput set-prop 12 273 1 1 (enabled 2-finger scrolling on touchpad)

Now in Maverick, I can run those same commands without getting an error message.  My edge scrolling will get disabled, but even though the property values are set to 1 1, two-finger scrolling doesn't work.

I get the exact same results when I edit the setting in gconf-editor like you did.

---

### Post by Framli on 2010-08-30
The sky is clear and two fingers can scroll via gnome-mouse-properties, here on up-to-date 10.10, fresh install from yesterday.

---

### Post by arrow.69 on 2010-08-31
Do you know if yours is a Synaptics Touchpad?

What's strange to me is that the option for two finger scroll is there, it just doesn't seem to work.

---

### Post by Starks on 2010-08-31
Yup. Synaptics.

This is rough fix though.

xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Pressure" 32 10
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Width" 32 8
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Two-Finger Scrolling" 8 1
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Scrolling" 8 1 1

---

### Post by arrow.69 on 2010-09-03
Thanks!

I had a similar type of script running in Lucid but I guess xinput changed properties around and I couldn't get it to work.  My startup script now uses the commands you gave me, plus an extra one to disable edge scrolling

```

#!/bin/sh

sleep 5
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Pressure" 32 10
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Width" 32 8
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Two-Finger Scrolling" 8 1
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Scrolling" 8 1 1
xinput set-prop "SynPS/2 Synaptics TouchPad" "Synaptics Edge Scrolling" 0 0 0
echo "success!"

```



Thanks for your help!

---

### Post by andrek on 2010-09-08
Thanks **arrow.69** for your script! Works great.

---

