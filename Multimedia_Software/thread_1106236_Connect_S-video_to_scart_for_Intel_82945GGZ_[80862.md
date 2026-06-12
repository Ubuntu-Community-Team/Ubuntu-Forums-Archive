---
title: "Connect S-video to scart for Intel 82945G/GZ [8086:2772]"
date: 2009-03-25
forum: Multimedia Software
---

### Post by iosifidis on 2009-03-25
I'm trying to connect a computer to tv so I'll make it media center for my nephew to watch his movies in Greek without having the problem to change the language etc (my mom doesn't remember how to change it). The program I'll use is [XBMC]("http://tombuntu.com/index.php/2008/12/09/transform-ubuntu-into-a-media-center-with-xbmc/")

Well I'll try to describe what I did so far.

First of all **lspci -nn | grep VGA** gives me:
[00:02.0 VGA compatible controller [0300]: Intel Corporation 82945G/GZ Integrated Graphics Controller [8086:2772] (rev 02)]("http://www.imageshack.gr/view.php?file=znb4bijazhi71q12r9pm.png")
This card is onboard ([D945GCLF2]("http://www.mini-box.com/Intel-D945GCLF2-Mini-ITX-Motherboard"))
I also tried this with many operating systems (Mythbuntu 8.10, Ubuntu 8.10 and now I have Ubuntu 9.04 because I found on the net that it solves problem).
The connection I do is S-video to scart to a CRT tv.

1. When I turn on my computer, I see ONLY black and white image. This is solved following the instructions of the picture at our forum ([How to have color signal using S-video]("http://forum.ubuntu-gr.org/viewtopic.php?f=9&t=2402").

2. Again when I turn on my computer, I cannot have both tv and VGA signal. When I use only the tv (S-video) I get the following result:
[[img]http://img262.imageshack.us/img262/1412/dsc02341.jpg[/img]](http://img262.imageshack.us/my.php?image=dsc02341.jpg)
[[img]http://img262.imageshack.us/img262/dsc02341.jpg/1/w800.png[/img]](http://g.imageshack.us/img262/dsc02341.jpg/1/)

The first one is solved using Randr program.
[LIST]
[*]**grandr** shows me the 2 output signals and can change the resolution.
[*]**lxrandr** shows me how to change the resolution and if I want to have both signals the same time.
[*]**arandr** couldn't open. It sends a bug (or something) back.
[/LIST]

Now, after I used those programs and can see at the same time to both tv and VGA, I manage the tv to show only the left side (let's say a stripe 25% of the whole screen) with the same result.

I guess the problem is the NTSC and PAL. Well, since my tv shows only PAL (it's old CRT one), I tried couple of commands with xrandr. And here the results:
**xrandr --verbose**
```
Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 1600 x 1600
VGA connected 1280x1024+0+0 (0x3e) normal (normal left inverted right x axis y axis) 338mm x 271mm
   Identifier: 0x3b
   Timestamp:  23079
   Subpixel:   unknown
   Clones:   
   CRTC:       0
   CRTCs:      0 1
   Panning:    0x0+0+0
   Tracking:   0x0+0+0
   Border:     0/0/0/0
   Transform:  1.000000 0.000000 0.000000
               0.000000 1.000000 0.000000
               0.000000 0.000000 1.000000
              filter:
   EDID_DATA:
      00ffffffffffff0015c3151701010101
      010e010268221c78eac5c6a3574a9c23
      124f54bfef8081808140814f714f0101
      010101010101302a009851002a403070
      1300520f1100001e000000ff00343637
      34393031340a20202020000000fd0038
      4c1f500e000a202020202020000000fc
      004c3535300a20202020202020200049
  1280x1024 (0x3d)  108.0MHz +HSync +VSync +preferred
        h: width  1280 start 1328 end 1440 total 1688 skew    0 clock   64.0KHz
        v: height 1024 start 1025 end 1028 total 1066           clock   60.0Hz
  1280x1024 (0x3e)  135.0MHz +HSync +VSync *current
        h: width  1280 start 1296 end 1440 total 1688 skew    0 clock   80.0KHz
        v: height 1024 start 1025 end 1028 total 1066           clock   75.0Hz
  1280x1024 (0x3d)  108.0MHz +HSync +VSync
        h: width  1280 start 1328 end 1440 total 1688 skew    0 clock   64.0KHz
        v: height 1024 start 1025 end 1028 total 1066           clock   60.0Hz
  1280x960 (0x3f)  129.9MHz -HSync +VSync
        h: width  1280 start 1368 end 1504 total 1728 skew    0 clock   75.1KHz
        v: height  960 start  961 end  964 total 1002           clock   75.0Hz
  1280x960 (0x40)  108.0MHz +HSync +VSync
        h: width  1280 start 1376 end 1488 total 1800 skew    0 clock   60.0KHz
        v: height  960 start  961 end  964 total 1000           clock   60.0Hz
  1152x864 (0x41)  108.0MHz +HSync +VSync
        h: width  1152 start 1216 end 1344 total 1600 skew    0 clock   67.5KHz
        v: height  864 start  865 end  868 total  900           clock   75.0Hz
  1024x768 (0x42)   78.8MHz +HSync +VSync
        h: width  1024 start 1040 end 1136 total 1312 skew    0 clock   60.0KHz
        v: height  768 start  769 end  772 total  800           clock   75.0Hz
  1024x768 (0x43)   75.0MHz -HSync -VSync
        h: width  1024 start 1048 end 1184 total 1328 skew    0 clock   56.5KHz
        v: height  768 start  771 end  777 total  806           clock   70.1Hz
  1024x768 (0x44)   65.0MHz -HSync -VSync
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock   48.4KHz
        v: height  768 start  771 end  777 total  806           clock   60.0Hz
  832x624 (0x45)   57.3MHz -HSync -VSync
        h: width   832 start  864 end  928 total 1152 skew    0 clock   49.7KHz
        v: height  624 start  625 end  628 total  667           clock   74.6Hz
  800x600 (0x46)   50.0MHz +HSync +VSync
        h: width   800 start  856 end  976 total 1040 skew    0 clock   48.1KHz
        v: height  600 start  637 end  643 total  666           clock   72.2Hz
  800x600 (0x47)   49.5MHz +HSync +VSync
        h: width   800 start  816 end  896 total 1056 skew    0 clock   46.9KHz
        v: height  600 start  601 end  604 total  625           clock   75.0Hz
  800x600 (0x48)   40.0MHz +HSync +VSync
        h: width   800 start  840 end  968 total 1056 skew    0 clock   37.9KHz
        v: height  600 start  601 end  605 total  628           clock   60.3Hz
  800x600 (0x49)   36.0MHz +HSync +VSync
        h: width   800 start  824 end  896 total 1024 skew    0 clock   35.2KHz
        v: height  600 start  601 end  603 total  625           clock   56.2Hz
  640x480 (0x4a)   31.5MHz -HSync -VSync
        h: width   640 start  656 end  720 total  840 skew    0 clock   37.5KHz
        v: height  480 start  481 end  484 total  500           clock   75.0Hz
  640x480 (0x4b)   31.5MHz -HSync -VSync
        h: width   640 start  664 end  704 total  832 skew    0 clock   37.9KHz
        v: height  480 start  489 end  492 total  520           clock   72.8Hz
  640x480 (0x4c)   30.2MHz -HSync -VSync
        h: width   640 start  704 end  768 total  864 skew    0 clock   35.0KHz
        v: height  480 start  483 end  486 total  525           clock   66.7Hz
  640x480 (0x4d)   25.2MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock   31.5KHz
        v: height  480 start  490 end  492 total  525           clock   59.9Hz
  720x400 (0x4e)   28.3MHz -HSync +VSync
        h: width   720 start  738 end  846 total  900 skew    0 clock   31.5KHz
        v: height  400 start  412 end  414 total  449           clock   70.1Hz
TV-1 connected 800x600+0+0 (0x57) normal (normal left inverted right x axis y axis) 0mm x 0mm
   Identifier: 0x3c
   Timestamp:  23079
   Subpixel:   horizontal rgb
   Clones:   
   CRTC:       1
   CRTCs:      0 1
   Panning:    0x0+0+0
   Tracking:   0x0+0+0
   Border:     0/0/0/0
   Transform:  1.000000 0.000000 0.000000
               0.000000 1.000000 0.000000
               0.000000 0.000000 1.000000
              filter:
  1600x1024 (0x4f)  103.1MHz +HSync +VSync
        h: width  1600 start 1600 end 1656 total 1664 skew    0 clock   62.0KHz
        v: height 1024 start 1024 end 1029 total 1030           clock   60.2Hz
  1280x1024 (0x3d)  108.0MHz +HSync +VSync
        h: width  1280 start 1328 end 1440 total 1688 skew    0 clock   64.0KHz
        v: height 1024 start 1025 end 1028 total 1066           clock   60.0Hz
  1280x1024@60.00 (0x50)   87.3MHz
        h: width  1280 start 1281 end 1344 total 1376 skew    0 clock   63.4KHz
        v: height 1024 start 1025 end 1056 total 1057           clock   60.0Hz
  1440x900 (0x51)  106.5MHz -HSync +VSync
        h: width  1440 start 1520 end 1672 total 1904 skew    0 clock   55.9KHz
        v: height  900 start  903 end  909 total  934           clock   59.9Hz
  1280x960 (0x40)  108.0MHz +HSync +VSync
        h: width  1280 start 1376 end 1488 total 1800 skew    0 clock   60.0KHz
        v: height  960 start  961 end  964 total 1000           clock   60.0Hz
  1360x768 (0x52)   84.8MHz -HSync +VSync
        h: width  1360 start 1432 end 1568 total 1776 skew    0 clock   47.7KHz
        v: height  768 start  771 end  781 total  798           clock   59.8Hz
  1152x864 (0x53)   81.6MHz -HSync +VSync
        h: width  1152 start 1216 end 1336 total 1520 skew    0 clock   53.7KHz
        v: height  864 start  865 end  868 total  895           clock   60.0Hz
  1024x768 (0x44)   65.0MHz -HSync -VSync
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock   48.4KHz
        v: height  768 start  771 end  777 total  806           clock   60.0Hz
  1024x768@60.00 (0x54)   53.8MHz
        h: width  1024 start 1025 end 1088 total 1120 skew    0 clock   48.1KHz
        v: height  768 start  769 end  800 total  801           clock   60.0Hz
  920x766@60.00 (0x55)   48.7MHz
        h: width   920 start  921 end  984 total 1016 skew    0 clock   47.9KHz
        v: height  766 start  767 end  798 total  799           clock   60.0Hz
  832x624@60.00 (0x56)   36.6MHz
        h: width   832 start  833 end  896 total  928 skew    0 clock   39.4KHz
        v: height  624 start  625 end  656 total  657           clock   60.0Hz
  800x600 (0x48)   40.0MHz +HSync +VSync
        h: width   800 start  840 end  968 total 1056 skew    0 clock   37.9KHz
        v: height  600 start  601 end  605 total  628           clock   60.3Hz
  800x600@60.00 (0x57)   34.0MHz *current
        h: width   800 start  801 end  864 total  896 skew    0 clock   38.0KHz
        v: height  600 start  601 end  632 total  633           clock   60.0Hz
  720x576@60.00 (0x58)   29.8MHz
        h: width   720 start  721 end  784 total  816 skew    0 clock   36.5KHz
        v: height  576 start  577 end  608 total  609           clock   60.0Hz
  704x576@60.00 (0x59)   29.2MHz
        h: width   704 start  705 end  768 total  800 skew    0 clock   36.5KHz
        v: height  576 start  577 end  608 total  609           clock   60.0Hz
  720x540@60.00 (0x5a)   28.1MHz
        h: width   720 start  721 end  784 total  816 skew    0 clock   34.4KHz
        v: height  540 start  541 end  572 total  573           clock   60.0Hz
  720x480@60.00 (0x5b)   25.1MHz
        h: width   720 start  721 end  784 total  816 skew    0 clock   30.8KHz
        v: height  480 start  481 end  512 total  513           clock   60.0Hz
  640x480 (0x4d)   25.2MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock   31.5KHz
        v: height  480 start  490 end  492 total  525           clock   59.9Hz
```

**xrandr --q**
```
VGA connected 1280x1024+0+0 (normal left inverted right x axis y axis) 338mm x 271mm
   1280x1024      60.0 +   75.0*    60.0 
   1280x960       75.0     60.0 
   1152x864       75.0 
   1024x768       75.0     70.1     60.0 
   832x624        74.6 
   800x600        72.2     75.0     60.3     56.2 
   640x480        75.0     72.8     66.7     59.9 
   720x400        70.1 
TV-1 connected 800x600+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1600x1024      60.2 
   1280x1024      60.0 
   1280x1024@60.00   60.0 
   1440x900       59.9 
   1280x960       60.0 
   1360x768       59.8 
   1152x864       60.0 
   1024x768       60.0 
   1024x768@60.00   60.0 
   920x766@60.00   60.0 
   832x624@60.00   60.0 
   800x600        60.3 
   800x600@60.00   60.0*
   720x576@60.00   60.0 
   704x576@60.00   60.0 
   720x540@60.00   60.0 
   720x480@60.00   60.0 
   640x480        59.9  
```

Both commands give me the resolution only.

Not sure if I had to put **TV-1** or just **TV**. I did both. TV-1 gives me that there's not a name or something like that with following results. TV gives me this:
**xrandr --output TV --set TV_FORMAT PAL**
```
X Error of failed request:  164
  Major opcode of failed request:  150 (RANDR)
  Minor opcode of failed request:  15 ()
  Serial number of failed request:  24
  Current serial number in output stream:  24
```

Some links I found which I couldn't understand many things:
[LIST]
[*][http://www.thinkwiki.org/wiki/Intel_Graphics_Media_Accelerator_950]("http://www.thinkwiki.org/wiki/Intel_Graphics_Media_Accelerator_950")
[*][https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/298422]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/298422")
[*][A Newbie's Guide To RandR 1.2]("http://www.phoronix.com/scan.php?page=article&item=927&num=1")
[/LIST]

I hope I didn't bore you with all this info. Can anyone help?

---

### Post by iosifidis on 2009-03-27
I think I made something today.

I changed my xorg.conf to the following:

```
Section "Device"
Identifier "Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
Driver "intel"
BusID "PCI:0:2:0"
Option "monitor-VGA" "VGA"
Option "monitor-TV" "TV"
Option "monitor-LVCD" "LVCD"
EndSection

Section "Monitor"
Identifier "VGA"
Option "Ignore" "true"
EndSection

Section "Monitor"
Identifier "LVCD"
Option "DPMS"
EndSection

Section "Monitor"
Identifier "TV"
Option "Ignore" "false"
Option "TV_FORMAT" "PAL"
EndSection
```

The only thing I missed is the lxrandr and grandr shows only TV output but I see picture on TV and my VGA.

Regarding the picture, I think I turned it into (see picture).

[[img]http://www.imageshack.gr/files/h1be02i0a7ht780ftdrk_thumb.jpg[/img]](http://www.imageshack.gr/view.php?file=h1be02i0a7ht780ftdrk.jpg)

[[img]http://www.imageshack.gr/files/1oe7kjjg0hww9dbvdyre_thumb.jpg[/img]](http://www.imageshack.gr/view.php?file=1oe7kjjg0hww9dbvdyre.jpg)

It's PAL but I can see flickering (if it's called like this). I thinki I see doubles. Is there anything I can do or I have to "play" with xorg.conf?

---

### Post by braddcadd on 2009-03-28
Can you help me project my laptop to the tv?  Everything works but my s-video connection only allows 800x600 resolution.  Only part of my 1024x768 laptop screen appears on my tv.  Can I edit a config file to allow 1024x768?


```

me@mycomputer:~$ xrandr -q
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 1824 x 768
VGA-0 disconnected (normal left inverted right x axis y axis)
DVI-0 disconnected (normal left inverted right x axis y axis)
LVDS connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0*+   60.0  
   800x600        60.3  
   640x480        59.9  
S-video connected (normal left inverted right x axis y axis)
   800x600        59.9 +

```

---

### Post by braddcadd on 2009-03-28
looks like S-video doesn't support 1024x768.  I will try to switch to HDMI or VGA.

---

### Post by dfdario on 2009-07-27
Bug is still there... [http://bugs.freedesktop.org/show_bug.cgi?id=22891](http://bugs.freedesktop.org/show_bug.cgi?id=22891)

---

