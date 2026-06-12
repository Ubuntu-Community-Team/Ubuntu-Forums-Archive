---
title: "Radeon RV250 and dual screen in Maverick (10.10)"
date: 2010-10-15
forum: Multimedia Software
---

### Post by messner on 2010-10-15
I have one external monitor attached to my notebook. When I want to use only the external monitor (change the resolution to the native external resolution and notebook display off), the screen gets distorted and unusable ...

If I plug the monitor in the middle of the normal session to the notebook everything gets distorted automatically ...

The display works fine on both screens, when the lover resolution is used for both screens and the monitor is attached when I turn on the notebook ...

Any help ?

--------------------------------
lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] (rev 01)
--------------------------------
xrandr
Screen 0: minimum 320 x 200, current 1680 x 1050, maximum 4096 x 4096
VGA-0 connected 1680x1050+0+0 (normal left inverted right x axis y axis) 474mm x 296mm
1920x1200 60.0 +
1600x1200 60.0
1680x1050 60.0*
1280x1024 75.0 60.0
1440x900 75.0 59.9
1024x768 75.1 70.1 60.0
800x600 72.2 75.0 60.3
640x480 72.8 75.0 60.0
720x400 70.1
LVDS connected 1680x1050+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
1680x1050 60.7*+ 60.0
1600x1024 60.2
1400x1050 60.0 60.0
1280x1024 59.9 60.0
1440x900 59.9 59.9
1280x960 60.0 59.9
1280x854 59.9
1360x768 59.8
1280x800 59.8
1152x864 60.0
1280x720 59.9
1152x768 59.8
1024x768 60.0 59.9
800x600 60.3 59.9
840x525 120.0 119.8
800x512 120.3
848x480 59.7
700x525 120.0
720x480 59.7
640x512 120.0
720x450 119.8
640x480 120.0 59.9 59.4
680x384 119.6 119.9
576x432 120.1
512x384 120.0
400x300 120.6
320x240 120.1
S-video disconnected (normal left inverted right x axis y axis)

---

