---
title: "xrandr subpixel"
date: 2008-11-30
forum: Multimedia Software
---

### Post by trailofdead on 2008-11-30
I'm using xrandr to hook up an old lcd tv to my laptop.  I'm connecting it through VGA-0.  I'm setting VGA-0 to the native resolution, but the text isnt that clear.  I'm thinking maybe because of subpixel?  

Below is my xrandr --verbose

BTW, the native resolution is 1280x720, and some of the VGA-0 modes are not supported by my TV, such as 1280x1024.

```
Screen 0: minimum 320 x 200, current 2680 x 1050, maximum 2840 x 1050
VGA-0 connected 1280x720+1400+0 (0x5a) normal (normal left inverted right x axis y axis) 628mm x 3433mm
	Identifier: 0x44
	Timestamp:  161682
	Subpixel:   no subpixels
	Clones:    
	CRTC:       1
	CRTCs:      0 1
	EDID_DATA:
		00ffffffffffff0011a9000042000000
		110e01001804039c8e00000000000000
		000000fffff881c081c0818000000000
		000000000000000000fc004c4344204d
		756c74692d4d6564000000fc00696120
		446973706c6179202020000000fc000a
		202020202020202020202020302a0098
		51002a40f8706308040300000078004a
	load_detection: 1 (0x00000001) range:  (0,1)
  1280x1024 (0x57)  135.0MHz +HSync +VSync
        h: width  1280 start 1296 end 1440 total 1688 skew    0 clock   80.0KHz
        v: height 1024 start 1025 end 1028 total 1066           clock   75.0Hz
  1280x1024 (0x58)  109.0MHz -HSync +VSync
        h: width  1280 start 1368 end 1496 total 1712 skew    0 clock   63.7KHz
        v: height 1024 start 1027 end 1034 total 1063           clock   59.9Hz
  1280x800 (0x49)   83.5MHz
        h: width  1280 start 1344 end 1480 total 1680 skew    0 clock   49.7KHz
        v: height  800 start  801 end  804 total  828           clock   60.0Hz
  1152x864 (0x59)  108.0MHz +HSync +VSync
        h: width  1152 start 1216 end 1344 total 1600 skew    0 clock   67.5KHz
        v: height  864 start  865 end  868 total  900           clock   75.0Hz
  1280x768 (0x4a)   80.1MHz
        h: width  1280 start 1344 end 1480 total 1680 skew    0 clock   47.7KHz
        v: height  768 start  769 end  772 total  795           clock   60.0Hz
  1280x720 (0x5a)   74.5MHz -HSync +VSync
        h: width  1280 start 1344 end 1472 total 1664 skew    0 clock   44.8KHz
        v: height  720 start  723 end  728 total  748           clock   59.9Hz
  1024x768 (0x5b)   78.8MHz +HSync +VSync
        h: width  1024 start 1040 end 1136 total 1312 skew    0 clock   60.1KHz
        v: height  768 start  769 end  772 total  800           clock   75.1Hz
  1024x768 (0x5c)   75.0MHz -HSync -VSync
        h: width  1024 start 1048 end 1184 total 1328 skew    0 clock   56.5KHz
        v: height  768 start  771 end  777 total  806           clock   70.1Hz
  1024x768 (0x4b)   65.0MHz -HSync -VSync
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock   48.4KHz
        v: height  768 start  771 end  777 total  806           clock   60.0Hz
  1024x768 (0x5d)   44.9MHz +HSync +VSync Interlace
        h: width  1024 start 1032 end 1208 total 1264 skew    0 clock   35.5KHz
        v: height  768 start  768 end  776 total  817           clock   43.5Hz
  832x624 (0x5e)   57.3MHz -HSync -VSync
        h: width   832 start  864 end  928 total 1152 skew    0 clock   49.7KHz
        v: height  624 start  625 end  628 total  667           clock   74.6Hz
  800x600 (0x5f)   50.0MHz +HSync +VSync
        h: width   800 start  856 end  976 total 1040 skew    0 clock   48.1KHz
        v: height  600 start  637 end  643 total  666           clock   72.2Hz
  800x600 (0x60)   49.5MHz +HSync +VSync
        h: width   800 start  816 end  896 total 1056 skew    0 clock   46.9KHz
        v: height  600 start  601 end  604 total  625           clock   75.0Hz
  800x600 (0x4c)   40.0MHz +HSync +VSync
        h: width   800 start  840 end  968 total 1056 skew    0 clock   37.9KHz
        v: height  600 start  601 end  605 total  628           clock   60.3Hz
  800x600 (0x61)   36.0MHz +HSync +VSync
        h: width   800 start  824 end  896 total 1024 skew    0 clock   35.2KHz
        v: height  600 start  601 end  603 total  625           clock   56.2Hz
  640x480 (0x62)   31.5MHz -HSync -VSync
        h: width   640 start  656 end  720 total  840 skew    0 clock   37.5KHz
        v: height  480 start  481 end  484 total  500           clock   75.0Hz
  640x480 (0x63)   31.5MHz -HSync -VSync
        h: width   640 start  664 end  704 total  832 skew    0 clock   37.9KHz
        v: height  480 start  489 end  491 total  520           clock   72.8Hz
  640x480 (0x64)   30.2MHz -HSync -VSync
        h: width   640 start  704 end  768 total  864 skew    0 clock   35.0KHz
        v: height  480 start  483 end  486 total  525           clock   66.7Hz
  640x480 (0x65)   25.2MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock   31.5KHz
        v: height  480 start  490 end  492 total  525           clock   60.0Hz
  640x480 (0x4d)   25.2MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock   31.5KHz
        v: height  480 start  490 end  492 total  525           clock   59.9Hz
  720x400 (0x66)   35.5MHz -HSync -VSync
        h: width   720 start  738 end  846 total  900 skew    0 clock   39.4KHz
        v: height  400 start  421 end  423 total  449           clock   87.8Hz
  720x400 (0x67)   28.3MHz -HSync +VSync
        h: width   720 start  738 end  846 total  900 skew    0 clock   31.5KHz
        v: height  400 start  412 end  414 total  449           clock   70.1Hz
DVI-0 disconnected (normal left inverted right x axis y axis)
	Identifier: 0x45
	Timestamp:  161682
	Subpixel:   horizontal rgb
	Clones:    
	CRTCs:      0 1
		scaler: off
		tmds_pll: bios
LVDS connected 1400x1050+0+0 (0x48) normal (normal left inverted right x axis y axis) 0mm x 0mm
	Identifier: 0x46
	Timestamp:  161682
	Subpixel:   horizontal rgb
	Clones:    
	CRTC:       0
	CRTCs:      0
		scaler: full
	backlight: 255 (0x000000ff) range:  (0,255)
  1400x1050 (0x48)   85.0MHz
        h: width  1400 start 1472 end 1512 total 1600 skew    0 clock   53.1KHz
        v: height 1050 start 1052 end 1053 total 1062           clock   50.0Hz
  1280x800 (0x49)   83.5MHz
        h: width  1280 start 1344 end 1480 total 1680 skew    0 clock   49.7KHz
        v: height  800 start  801 end  804 total  828           clock   60.0Hz
  1280x768 (0x4a)   80.1MHz
        h: width  1280 start 1344 end 1480 total 1680 skew    0 clock   47.7KHz
        v: height  768 start  769 end  772 total  795           clock   60.0Hz
  1024x768 (0x4b)   65.0MHz -HSync -VSync
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock   48.4KHz
        v: height  768 start  771 end  777 total  806           clock   60.0Hz
  800x600 (0x4c)   40.0MHz +HSync +VSync
        h: width   800 start  840 end  968 total 1056 skew    0 clock   37.9KHz
        v: height  600 start  601 end  605 total  628           clock   60.3Hz
  640x480 (0x4d)   25.2MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock   31.5KHz
        v: height  480 start  490 end  492 total  525           clock   59.9Hz
S-video disconnected (normal left inverted right x axis y axis)
	Identifier: 0x47
	Timestamp:  161682
	Subpixel:   no subpixels
	Clones:    
	CRTCs:      0 1
		tv_standard: ntsc
	tv_vertical_position: 0 (0x00000000) range:  (-5,5)
	tv_horizontal_position: 0 (0x00000000) range:  (-5,5)
	tv_horizontal_size: 0 (0x00000000) range:  (-5,5)
	load_detection: 0 (0x00000000) range:  (0,1)

```

Any help would be appreciated.  Thanks

---

### Post by trailofdead on 2008-11-30
bump

---

