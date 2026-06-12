---
title: "Svideo TVout problem with ATI Radeon X1300"
date: 2011-05-21
forum: Multimedia Software
---

### Post by action9 on 2011-05-21
Hi,

I recently installed 11.04 and i am tearing my hear out to get Svideo to work properly on my t.v.

Currently my T.V boots fine showing bios info etc but as soon as the   ubuntu logo comes on the whole t.v is green with horizontal and vertical   lines. I have tried with xrandr --output S-video --set "tv standard"   ntsc thinking it would be a PAL/NTSC issue and my t.v is pal, but no go.

Does anyone have any solution for this,because the tvout is working but   something is configured incorrectly that the display is not showing   right. I currently have it running at 800x600 on pal but still nothing.

Also what i noticed is that the t.v is running as an extended desktop   and not twinview, would this have anything to do with it you think?

Your reply would be greatly appreciated.

This is the ouput i get from xrandr --props:
     Quote:
                                                 user@tv-pc:~$ xrandr --props
Screen 0: minimum 320 x 200, current 1824 x 768, maximum 8192 x 8192
DVI-0 connected 1024x768+0+0 (normal left inverted right x axis y axis) 340mm x 270mm
    EDID:
        00ffffffffffff0022f05c2601010101
        0511010368221b8cee5e50a6544c9926
        145054adef8081800101010101010101
        010101010101302a009851002a403070
        1300540e1100001e000000fd00324c1e
        530e000a202020202020000000fc0048
        50204c313730360a20202020000000ff
        00434e433730354e5731570a202000ac
    load detection: 1 (0x00000001)    range:  (0,1)
    underscan vborder: 0 (0x00000000)    range:  (0,12:cool:
    underscan hborder: 0 (0x00000000)    range:  (0,12:cool:
    underscan:    off
        supported: off          on           auto        
    coherent: 1 (0x00000001)    range:  (0,1)
   1280x1024      60.0 +   75.0  
   1152x864       75.0  
   1024x768       75.1     70.1     60.0* 
   832x624        74.6  
   800x600        72.2     75.0     60.3  
   640x480        72.8     75.0     60.0  
   720x400        70.1  
S-video connected 800x600+1024+9 (normal left inverted right x axis y axis) 0mm x 0mm
    tv standard:    pal
        supported: ntsc         pal          pal-m        pal-60      
                   ntsc-j       scart-pal    pal-cn       secam       
    load detection: 1 (0x00000001)    range:  (0,1)
   1024x768       59.9  
   800x600        59.9* 
   848x480        59.7  
   720x480        59.7  
   640x480        59.4  
DVI-1 disconnected (normal left inverted right x axis y axis)
    load detection: 1 (0x00000001)    range:  (0,1)
    underscan vborder: 0 (0x00000000)    range:  (0,12:cool:
    underscan hborder: 0 (0x00000000)    range:  (0,12:cool:
    underscan:    off
        supported: off          on           auto        
    coherent: 1 (0x00000001)    range:  (0,1)
user@tv-pc:~$


I saw a bug report with ref number: #733270 with regards to this exact issue,

is it planned to be fixed sometime cause this is driving me crazy and its an oldish card so why shouldnt it be supported?

---

### Post by www.rzr.online.fr on 2012-07-15
check for workaround :

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/733270](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/733270)

is the quality of the image acceptable ?

not on mine :

[http://rzr.online.fr/q/igp_320m](http://rzr.online.fr/q/igp_320m)

---

