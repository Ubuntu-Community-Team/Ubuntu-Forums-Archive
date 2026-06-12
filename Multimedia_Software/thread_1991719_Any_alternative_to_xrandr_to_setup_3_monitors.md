---
title: "Any alternative to xrandr to setup 3 monitors?"
date: 2012-05-30
forum: Multimedia Software
---

### Post by pi3ch on 2012-05-30
I tried many combinations with xrandr command under lubuntu 12.04 to setup my three monitors
  
[LIST]
[*]DVI (DELL 1) left detected as HDMI1
[*]HDMI (LG E2290) middle detected as HDMI2
[*]VGA (DELL 2) right detected as VGA1
[/LIST]
  I can get the display with fix 1280x1024 on all the monitors. But  once I setup 1280x1024 + 1920x1080 + 1280x1024, I get blank screen on  all the monitors. Sometimes it throws crts fail error instead of  blanking out.

  **Anyone has similar issue? any solution/workaround?**

  P.S. I can setup two monitors using 1280x1280 and 1920x1080 P.S.S. HDMI2 required at least 1920x1080 to display sharp picture.
  
Outputs (it seems graphic card supports up to **8192x8192**):
```
xrandr
Screen 0: minimum 320 x 200, current 3840 x 1024, maximum 8192 x 8192
VGA1 connected 1280x1024+2560+0 (normal left inverted right x axis y axis) 338mm x 270mm
1280x1024      60.0*+   75.0
1152x864       75.0
1024x768       75.1     60.0
800x600        75.0     60.3
640x480        75.0     60.0
720x400        70.1
HDMI1 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 376mm x 301mm
1280x1024      60.0*+   75.0
1152x864       75.0
1024x768       75.1     60.0
800x600        75.0     60.3
640x480        75.0     60.0
720x400        70.1
HDMI2 connected 1280x1024+1280+0 (normal left inverted right x axis y axis) 477mm x 268mm
1920x1080      60.0 +
1680x1050      60.0
1280x1024      75.0     60.0*
1152x864       75.0
1024x768       75.1     60.0
800x600        75.0     60.3
640x480        75.0     60.0
720x400        70.1
DP1 disconnected (normal left inverted right x axis y axis)
DP2 disconnected (normal left inverted right x axis y axis)
```3 CRTs (0,1 VGA, 0,1,2 for other HDMI)
```
xrandr --verbose
VGA1 connected 1280x1024+2560+0 (0x47) normal (normal left inverted right x axis y axis) 338mm x 270mm
Identifier: 0x42
Timestamp:  51324
Subpixel:   unknown
Gamma:      1.0:1.0:1.0
Brightness: 1.0
Clones:
CRTC:       0
CRTCs:      0 1
...
HDMI1 connected 1280x1024+0+0 (0x47) normal (normal left inverted right x axis y axis) 376mm x 301mm
Identifier: 0x43
Timestamp:  51324
Subpixel:   unknown
Gamma:      1.0:1.0:1.0
Brightness: 1.0
Clones:
CRTC:       1
CRTCs:      0 1 2
...
HDMI2 connected 1280x1024+1280+0 (0x47) normal (normal left inverted right x axis y axis) 477mm x 268mm
Identifier: 0x44
Timestamp:  51324
Subpixel:   unknown
Gamma:      1.0:1.0:1.0
Brightness: 1.0
Clones:
CRTC:       2
CRTCs:      0 1 2
```Below command **fails**:
```
xrandr --output VGA1 --auto --output HDMI2 --auto --left-of VGA1 --output HDMI1 --auto --left-of HDMI2
```Below command **passes**:
```
xrandr --output VGA1 --auto --output HDMI2 --mode 1280x1024 --rate 60.0 --left-of VGA1 --output HDMI1 --auto --left-of HDMI2
```Graphic card VGA compatible controller: [U]Intel Corporation Ivy Bridge Graphics Controller (rev 09)
[/U]

---

### Post by chrb on 2013-02-24
> **pi3ch said:**
> I tried many combinations with xrandr command under lubuntu 12.04 to setup my three monitors
  
[LIST]
[*]DVI (DELL 1) left detected as HDMI1
[*]HDMI (LG E2290) middle detected as HDMI2
[*]VGA (DELL 2) right detected as VGA1
[/LIST]


I realise that this is a bit of a late reply, but did you ever try connecting the two Dell monitors to HDMI1 and HDMI2 instead of  VGA1? Ivy Bridge can support three monitors if two of them are of the same connection type and resolution. Your above configuration wouldn't work because you've put the odd monitor on one of the HDMI ports, it would have to be on the VGA port.

---

