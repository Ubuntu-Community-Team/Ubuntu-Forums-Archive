---
title: "Cant set screen resolution to 1440x900"
date: 2008-07-11
forum: Multimedia Software
---

### Post by braiam on 2008-07-11
Hello guys and ladies, my first post at ubuntuformus

All I want is to set kde to 1440x900, but it always displays at 1280x768

***This is my setup***
**Monitor:** HP w17e (best resolution is 1440x900@60)
**Graphics Adapter:** 01:05.1 Display controller: ATI Technologies Inc Unknown device 5874 (data from lspci)


***Procedures I've tried***
**Procedure:** Changing Settings from System Settings or kcontrol
**Result:** The module Monitor & Display is not loaded (see attachment)

**Procedure:** Changing or removing xorg.conf and restarting X
**Result:** Nothing special happens, it continues working ok, but not at desired resolution

**Procedure:** Running dpkg-reconfigure xserver-xorg and restarting X
**Result:** Nothing special happens, it continues working ok, but not at desired resolution

**Procedure:** Running dpkg-reconfigure -phigh xserver-xorg and restarting X
**Result:** Nothing special happens, it continues working ok, but not at desired resolution


**Procedure:** Removing ~/.kde/share/config/displayconfigrc and restarting X
**Result:** Login is not possible. Must restore displayconfigrc


This is the output of running **displayconfig**


```
Traceback (most recent call last):
  File "/usr/bin/displayconfig", line 1755, in <module>
    displayapp = DisplayApp()
  File "/usr/bin/displayconfig", line 441, in __init__
    self.xsetup = XSetup(self.xconfigpath)
  File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 394, in __init__
    self._finalizeInit()
  File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 404, in _finalizeInit
    gfxcard._finalizeInit()
  File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 1123, in _finalizeInit
    screen._finalizeInit()
  File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 1588, in _finalizeInit
    (cw,ch,x,x) = self.x_live_screen.getSize()
  File "/var/lib/python-support/python2.5/xf86misc.py", line 77, in getSize
    return self.sizes[self.currentsizeid]
IndexError: list index out of range
```




This is the output of running **xrandr**



```
Screen 0: minimum 320 x 200, current 1280 x 768, maximum 1920 x 1200
VGA-0 disconnected 1280x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
DVI-0 disconnected (normal left inverted right x axis y axis)
S-video disconnected (normal left inverted right x axis y axis)
  1280x768 (0x62)   80.1MHz
        h: width  1280 start 1344 end 1480 total 1680 skew    0 clock   47.7KHz
        v: height  768 start  769 end  772 total  795           clock   60.0Hz
```




And this is **xorg.conf**


```
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "latam"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
EndSection
```



I dont know what else should I try. I know you smart guys must have the solution, thanks in advance, and I hope I can contribute to this community

---

