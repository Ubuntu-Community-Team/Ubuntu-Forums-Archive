---
title: "detecting if 2nd monitor is plugged in"
date: 2010-07-23
forum: Multimedia Software
---

### Post by aeiah on 2010-07-23
i have an HDTV plugged into my computer, as well as a normal monitor. i usually use this computer as my main one, but when i hit the big green button on my remote, the main screen turns off, and xbmc is loaded on my HDTV. for this to work, i use a script that basically does this when the button is pressed:

```

# x server environment setup
X :1 -layout hdtv &
export DISPLAY=:1.0

# graphics sync settings
nvidia-settings -a :1.0/SyncToVBlank=1 &
nvidia-settings -a :1.0/AllowFlipping=1 &
nvidia-settings -a :1.0/XVideoTextureSyncToVBlank=1 &
nvidia-settings -a :1.0/XVideoBlitterSyncToVBlank=0 &

# launch xbmc
xbmc;

```

my problem is this:

my HDTV is crap, and only has one HDMI port. i have an xbox 360 i use too, so sometimes the computer isnt connected to the TV. if it isnt connected and the button is pressed, my computer just loads up xbmc on my main monitor. id like to be able to detect when the tv isnt connected so i can just throw up a notification instead. i never want xbmc on my normal monitor, and furthermore each time it happens i have to reset the overscanning settings in xbmc because they reset when a different display is used.

anyone have any ideas?

---

### Post by efflandt on 2010-07-23
Unfortunately xrandr does not show inactive displays, but maybe you could still use that as a test. I don't have a 2nd display connected to test, but I am guessing you could test the following, but I am not up on how to put this into an **if ...; then** test at the moment and have to get back to work:
 
**xrandr | grep "Screen 1:"**
 
Although, this little script appears to work:
 
**#!/bin/bash**
**screen1=`xrandr | grep "Screen 1:"` || exit**
**echo found, so do something**
 
Note that the character ` is a grave or backtick (usually same key as tilde), not a single quote.

---

### Post by aeiah on 2010-07-26
xrandr only shows screen 0 unless screen 1 is active, as you feared. since my post id looked into xrandr but it gives the same output whether the monitor is plugged in or not. i found some post regarding slackware where the guy catenated a /proc/ file but the same structure doesnt exist with ubuntu.

perhaps with a card other than nvidia the xrandr method will work but sadly for me it seems ill have to keep poking around

---

### Post by P4man on 2010-07-26
Try this:
```

nvidia-settings --query ConnectedDisplays
```


It shows me this with 2 montiors:

  Attribute 'ConnectedDisplays' (bob-desktop:0[gpu:0]): **0x00010002**.
    'ConnectedDisplays' is a bitmask attribute.
    'ConnectedDisplays' is a read-only attribute.
    'ConnectedDisplays' can use the following target types: X Screen, GPU.

If I unplug one:

  Attribute 'ConnectedDisplays' (bob-desktop:0.0): **0x00000002**.
    'ConnectedDisplays' is a bitmask attribute.
    'ConnectedDisplays' is a read-only attribute.
    'ConnectedDisplays' can use the following target types: X Screen, GPU.

---

