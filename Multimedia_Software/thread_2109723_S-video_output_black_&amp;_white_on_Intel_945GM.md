---
title: "S-video output black &amp; white on Intel 945GM"
date: 2013-01-28
forum: Multimedia Software
---

### Post by macgywer on 2013-01-28
Hello,

I'm getting black and white output to my TV using S-video. 

Lubuntu 12.10 and the graphic card is Intel 945GM.

Worked well on windows XP, any idea why the output is B&W under lubuntu?

I read somewhere that PAL output can be B&W. Where can I find the config file so I can try to change to NTSC?

---

### Post by macgywer on 2013-01-28
Can I modify the output using xandr?

```
danijel@danijel-3000-C200:~$ xrandr --verbose
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 4096 x 4096
LVDS1 connected 1024x768+0+0 (0x45) normal (normal left inverted right x axis y axis) 304mm x 2280mm
	Identifier: 0x41
	Timestamp:  2270297
	Subpixel:   horizontal rgb
	Gamma:      1.0:1.0:1.0
	Brightness: 1.0
	Clones:    
	CRTC:       1
	CRTCs:      1
	Transform:  1.000000 0.000000 0.000000
	            0.000000 1.000000 0.000000
	            0.000000 0.000000 1.000000
	           filter: 
	EDID:
		00ffffffffffff00320c000000000000
		000f0102801e16780a74b09657548b28
		25505400000001010101010101010101
		01010101010164190040410026301888
		360030e4100000180000000000000000
		00000000000000000000000000fe004c
		475068696c6970734c43440a000000fe
		004c503135305830382d544c414100a3
	BACKLIGHT: 7 (0x00000007)	range:  (0,7)
	Backlight: 7 (0x00000007)	range:  (0,7)
	scaling mode:	Full aspect
		supported: None         Full         Center       Full aspect 
  1024x768 (0x45)   65.0MHz -HSync -VSync *current +preferred
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock   48.4KHz
        v: height  768 start  771 end  777 total  806           clock   60.0Hz
  800x600 (0x46)   40.0MHz +HSync +VSync
        h: width   800 start  840 end  968 total 1056 skew    0 clock   37.9KHz
        v: height  600 start  601 end  605 total  628           clock   60.3Hz
  800x600 (0x47)   36.0MHz +HSync +VSync
        h: width   800 start  824 end  896 total 1024 skew    0 clock   35.2KHz
        v: height  600 start  601 end  603 total  625           clock   56.2Hz
  640x480 (0x48)   25.2MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock   31.5KHz
        v: height  480 start  490 end  492 total  525           clock   59.9Hz
VGA1 disconnected (normal left inverted right x axis y axis)
	Identifier: 0x42
	Timestamp:  2270297
	Subpixel:   unknown
	Clones:    
	CRTCs:      0 1
	Transform:  1.000000 0.000000 0.000000
	            0.000000 1.000000 0.000000
	            0.000000 0.000000 1.000000
	           filter: 
TV1 connected 848x480+0+0 (0xdf) normal (normal left inverted right x axis y axis) 0mm x 0mm
	Identifier: 0x43
	Timestamp:  2270297
	Subpixel:   unknown
	Gamma:      1.0:1.0:1.0
	Brightness: 1.0
	Clones:    
	CRTC:       0
	CRTCs:      0 1
	Transform:  1.000000 0.000000 0.000000
	            0.000000 1.000000 0.000000
	            0.000000 0.000000 1.000000
	           filter: 
	bottom margin: 37 (0x00000025)	range:  (0,100)
	right margin: 46 (0x0000002e)	range:  (0,100)
	top margin: 36 (0x00000024)	range:  (0,100)
	left margin: 54 (0x00000036)	range:  (0,100)
	mode:	NTSC-M
		supported: NTSC-M       NTSC-443     NTSC-J       PAL-M       
		           PAL-N        PAL          480p         576p        
		           720p@60Hz    720p@50Hz    1080i@50Hz   1080i@60Hz  
  848x480 (0xc2)   29.0MHz +preferred
        h: width   848 start  849 end  912 total  944 skew    0 clock   30.7KHz
        v: height  480 start  481 end  512 total  513           clock   59.9Hz
  640x480 (0xc3)   22.6MHz +preferred
        h: width   640 start  641 end  704 total  736 skew    0 clock   30.7KHz
        v: height  480 start  481 end  512 total  513           clock   59.9Hz
  1024x768 (0xc4)   53.8MHz
        h: width  1024 start 1025 end 1088 total 1120 skew    0 clock   48.0KHz
        v: height  768 start  769 end  800 total  801           clock   59.9Hz
  800x600 (0xc5)   34.0MHz
        h: width   800 start  801 end  864 total  896 skew    0 clock   37.9KHz
        v: height  600 start  601 end  632 total  633           clock   59.9Hz
  848x480 (0xdf)   24.2MHz
        h: width   848 start  849 end  912 total  944 skew    0 clock   25.6KHz
        v: height  480 start  481 end  512 total  513           clock   50.0Hz

```

What an I doing wrong (see the code below)?

```
danijel@danijel-3000-C200:~$ xrandr --output TV1 --set TV_FORMAT NTSC-M
X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  11 (RRQueryOutputProperty)
  Serial number of failed request:  31
  Current serial number in output stream:  31
danijel@danijel-3000-C200:~$ 
```

---

