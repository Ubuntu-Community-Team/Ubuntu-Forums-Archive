---
title: "TV-out on laptop not getting to work"
date: 2010-05-01
forum: Multimedia Software
---

### Post by pluim003 on 2010-05-01
Hi,

My laptop has a S-video TVOUT which I would like to use to show content on my tv. After plunging through a lot of documentation I can't get it to work.

Some config:

root@pluim-nielsen-laptop:~# xrandr --verbose
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 4096 x 4096
LVDS1 connected 1280x800+0+0 (0x43) normal (normal left inverted right x axis y axis) 331mm x 207mm
    Identifier: 0x41
    Timestamp:  6237460
    Subpixel:   horizontal rgb
    Clones:     TV1
    CRTC:       1
    CRTCs:      1
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
    EDID:
        00ffffffffffff0006af741800000000
        010f0103802115780a85a599574f8f26
        1d505400000001010101010101010101
        010101010101ea1a0080502010301520
        44004bcf100000180000000f00000000
        00000000000000000002000000fe0041
        554f0a202020202020202020000000fe
        004231353445573031205638200a00ce
    scaling mode:    Full
        supported: None         Full         Center       Full aspect 
  1280x800 (0x43)   68.9MHz -HSync -VSync *current +preferred
        h: width  1280 start 1301 end 1333 total 1408 skew    0 clock   48.9KHz
        v: height  800 start  804 end  808 total  816           clock   60.0Hz
<cut>
  640x350 (0x54)   31.5MHz +HSync -VSync
        h: width   640 start  672 end  736 total  832 skew    0 clock   37.9KHz
        v: height  350 start  382 end  385 total  445           clock   85.1Hz
TV1 disconnected (normal left inverted right x axis y axis)
    Identifier: 0x42
    Timestamp:  6237460
    Subpixel:   unknown
    Clones:    
    CRTCs:      0 1
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
    bottom margin: 37 (0x00000025)    range:  (0,100)
    right margin: 46 (0x0000002e)    range:  (0,100)
    top margin: 36 (0x00000024)    range:  (0,100)
    left margin: 54 (0x00000036)    range:  (0,100)
    mode:    PAL
        supported: NTSC-M       NTSC-443     NTSC-J       PAL-M       
                   PAL-N        PAL          480p@59.94Hz 480p@60Hz   
                   576p         720p@60Hz    720p@59.94Hz 720p@50Hz   
                   1080i@50Hz   1080i@60Hz   1080i@59.94H

Cable is connected but whatever I try using xrandr is a flickering on the screen.

xorg.conf looks like this:

Section "Device"
        Identifier      "Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
        Driver          "intel"
        BusID           "PCI:0:2:0"
        Option          "monitor-VGA"  "VGA"
        Option          "monitor-TV"   "TV"
        Option          "monitor-LVCD" "LVCD"
EndSection

Section "Monitor"
        Identifier      "VGA"
        Option "Ignore" "true"
EndSection

Section "Monitor"
        Identifier      "LVCD"
        Option          "DPMS"
EndSection

Section "Monitor"
        Identifier      "TV"
        Option  "Ignore" "false"
        Option  "TV_FORMAT¨  "PAL"
EndSection

And I also created a file in /etc/X11/Xsession.d# cat 45custom_xrandr_settings
# If an external monitor is connected, place it with xrandr
 
# External output may be "VGA" or "VGA-0" or "DVI-0" or "TMDS-1"
EXTERNAL_OUTPUT="TV1"
INTERNAL_OUTPUT="LVDS"
# EXTERNAL_LOCATION may be one of: left, right, above, or below
EXTERNAL_LOCATION="right"
 
case "$EXTERNAL_LOCATION" in
       left|LEFT)
               EXTERNAL_LOCATION="--left-of $INTERNAL_OUTPUT"
               ;;
       right|RIGHT)
               EXTERNAL_LOCATION="--right-of $INTERNAL_OUTPUT"
               ;;
       top|TOP|above|ABOVE)
               EXTERNAL_LOCATION="--above $INTERNAL_OUTPUT"
               ;;
       bottom|BOTTOM|below|BELOW)
               EXTERNAL_LOCATION="--below $INTERNAL_OUTPUT"
               ;;
       *)
               EXTERNAL_LOCATION="--left-of $INTERNAL_OUTPUT"
               ;;
esac
 
xrandr |grep $EXTERNAL_OUTPUT | grep " connected "
if [ $? -eq 0 ]; then
    xrandr --output $INTERNAL_OUTPUT --auto --output $EXTERNAL_OUTPUT --auto $EXTERNAL_LOCATION
    # Alternative command in case of trouble:
    # (sleep 2; xrandr --output $INTERNAL_OUTPUT --auto --output $EXTERNAL_OUTPUT --auto $EXTERNAL_LOCATION) &
else
    xrandr --output $INTERNAL_OUTPUT --auto --output $EXTERNAL_OUTPUT --off
fi
 
Output should be put to a plasma-tv with 852x480-resolution. But now cables are in the front av of the HD/DVD-recorder, but putting the cable directly into the tv gives the same results.

Anyone a clue?

---

### Post by pluim003 on 2010-05-01
After a few hours of plugging around no success. Checked the bios as well. TVOUT says PAL, and now all of a sudden I have:

TV1 disconnected (normal left inverted right x axis y axis)
    Identifier: 0x43
    Timestamp:  17943
    Subpixel:   unknown
    Clones:    
    CRTCs:      0 1
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
    bottom margin: 37 (0x00000025)    range:  (0,100)
    right margin: 46 (0x0000002e)    range:  (0,100)
    top margin: 36 (0x00000024)    range:  (0,100)
    left margin: 54 (0x00000036)    range:  (0,100)
    mode:    NTSC-M
        supported: NTSC-M       NTSC-443     NTSC-J       PAL-M       
                   PAL-N        PAL          480p@59.94Hz 480p@60Hz   
                   576p         720p@60Hz    720p@59.94Hz 720p@50Hz   
                   1080i@50Hz   1080i@60Hz   1080i@59.94H

Can't figure out where it comes from.
Only change to xorg.conf is that I've put the default tvformat to Composite.

Still no image on tv.

---

