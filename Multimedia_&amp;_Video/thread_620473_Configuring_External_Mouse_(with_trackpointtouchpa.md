---
title: "Configuring External Mouse (with trackpoint/touchpad)"
date: 2007-11-22
forum: Multimedia &amp; Video
---

### Post by Redmumba on 2007-11-22
I have a Thinkpad T61, which includes both a touchpad and the trackpoint.  Now, when I'm in my room, I use a USB-connected Intellimouse Explorer, but of course, the back/forward buttons don't work on it--because the X-org entry that I would normally edit is the one attached to the trackpoint.

> 
#Trackpoint
Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
    Option         "EmulateWheel" "on"
    Option         "EmulateWheelButton" "2"
    Option         "YAxisMapping" "4 5"
    Option         "XAxisMapping" "6 7"
EndSection

#Touchpad
Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizEdgeScroll" "0"
EndSection


Now, I tried setting up the xorg.conf file to look SPECIFCALLY at mouse0/1/2, etc., but it doesn't have any effect on the mouse.  How can I setup a third mouse for my system?

---

