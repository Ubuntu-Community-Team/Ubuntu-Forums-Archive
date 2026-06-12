---
title: "ATI Radeon 9000 (R250) PAL TV Out on 7.10 Gutsy Gibbon"
date: 2008-04-20
forum: Multimedia &amp; Video
---

### Post by tagboard on 2008-04-20
Hi,  

I have been trying to have a unmarked ATI Radeon 9000 card with VGA, DVI & S-Video out.  Please note this card is PCI (Not PCIe or PCIx).

I have been trying to get TV-out via S-Video on a Australian (PAL G/B)  TV.  

By Default the TV will display output, including during boot time.  However this output is black & white.  I believe this is due to TV not accepting NTSC.  

So I have changed "tv_standard" pal using xrandr and used it with a 800x600 mode I found on this forum, however the TV displays output that seems to be heavily out of sync.  Generating a modeline that is compatible with both the card and the TV might be the way to go, but I don't know how to do that.  

I have also tried to install the ATI propriety install using the distribution on ATI's site.  However this fails with an error in the installer script.

So could somebody tell me:
1) If PAL-B/G is suported on this ATI card on 7.10?  

2) Which Driver supports PAL B/G TV-out via S-Video port

3) If yes to above, could someobody help me generate a xorg.conf and xrandr commands to allow TV?  Note: As this is going to be a PVR, I am happy to live with TV-out only and VGA monitor can go.

4) If not, is there an alternative driver and/or patch for this card.  I have looked at [http://wiki.cchtml.com/index.php/Tvout]("http://wiki.cchtml.com/index.php/Tvout") 
but that seems to be for edgy only. 

NOTE:  I am happy to reinstall this box or wait for 8.04 or one of its Release Candidates if that will help.

I can post the full config files on request.

Regards, 

TAGBOARD

_Here is the information of my config: _


```
#uname -a
Linux calculon 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686 GNU/Linux


#lspci | grep VGA
00:05.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] (rev 01)
01:00.0 VGA compatible controller: VIA Technologies, Inc. VT8623 [Apollo CLE266] integrated CastleRock graphics (rev 03)

```
NOTE: Nothing is connected to the onboard (CLE266] VGA port. Bios has been configured to look at the "PCI" card.  on the ATI VGA is connected to a CRT Monitor and S-Video to the TV via a S-video to Composite adaptor.  


Selected bits of xrandr --verbose

```
Screen 0: minimum 320 x 200, current 1280 x 960, maximum 1280 x 960
VGA-0 connected 1280x960+0+0 (0x4f) normal (normal left inverted right) 330mm x 265mm
        Identifier: 0x4c
        Timestamp:  1781608937
        Subpixel:   no subpixels
        Clones:    
        CRTC:       0
        CRTCs:      0 1
        EDID_DATA:
                00fffff
    ... SNIPPED ... 

DVI-0 disconnected (normal left inverted right)
    ... SNIPPED ... 

S-video disconnected (normal left inverted right)
        Identifier: 0x4e
        Timestamp:  1781608937
        Subpixel:   no subpixels
        Clones:    
        CRTCs:      0 1
                tv_standard: ntsc
        tv_vertical_position: 0 (0x00000000) range:  (-5,5)
        tv_horizontal_position: 0 (0x00000000) range:  (-5,5)
        tv_horizontal_size: 0 (0x00000000) range:  (-5,5)
        load_detection: 0 (0x00000000) range:  (0,1)

```


Selected bit of xorg.conf CONFIG

```
 ... SNIPPED Mouse/keyboard bits ... 

Section "Device"
        Identifier      "ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
        Boardname       "ATI Radeon"
        Busid           "PCI:0:5:0"
        Driver          "ati"
        Screen  0
        Vendorname      "ATI"
        Option          "MergedFB"      "off"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Vendorname      "Generic CRT Display"
        Modelname       "Monitor 1024x768"
        Horizsync       31.5-61.0
        Vertrefresh     50-75
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
        Gamma   1.0
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
        Monitor         "Generic Monitor"
        Defaultdepth    24
        SubSection "Display"
                Depth   24
                Virtual 1280    960
                Modes           "800x600@60"    "832x624@75"    "800x600@75"    "1024x768@75"   "800x600@72"  "1024x768@70"    "800x600@56"    "1024x768@60"   "640x480@75"    "1280x960@60"   "640x480@72"    "640x480@60"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
  screen 0 "Default Screen" 0 0
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"

        # Uncomment if you have a wacom tablet
        #       InputDevice     "stylus"        "SendCoreEvents"
        #       InputDevice     "cursor"        "SendCoreEvents"
        #       InputDevice     "eraser"        "SendCoreEvents"
EndSection
Section "Module"
        Load            "glx"
        Load            "GLcore"
        Load            "v4l"
EndSection

    ... SNIPPED OpenChrome Driver stuff for onboard video ... 
```



MOTHERBOARD Data

CPU: Centaur VIA Nehemiah stepping 08 1GHz 133/100MHz FSB
Chipset: North Bridge: VIA CLE266 Digital Media IGP Chipset, South Bridge: VIA VT8235M
System Memory:	1GB High Density DIMM shows as 512MB as chipset does not do HD.
VGA:	Integrated VIA UniChromeTM IGP graphics with AGP interface, 64/32/16MB shared system memory, Hardware MPEG-2 decoding acceleration:

[http://gentoo-wiki.com/HARDWARE_VIA](http://gentoo-wiki.com/HARDWARE_VIA)

---

