---
title: "15 khz monitor (vga -&gt; scart) with ATI 3870"
date: 2011-11-26
forum: Multimedia Software
---

### Post by martin9112 on 2011-11-26
Hello, i am trying to get a picture with my 15 khz monitor - gfxcard: ati 3870, ubuntu 10.04.

The cable works fine with windows and the 15 khz programm from [COLOR=RoyalBlue][here]("http://community.arcadeinfo.de/showthread.php?9367-Screenshot-and-Downloads")[/COLOR]

Is it possible with the proprietary ati driver?

CRT1: Sony TV via VGA to Scart cable [COLOR=black]([COLOR=RoyalBlue][layout]("http://community.arcadeinfo.de/showthread.php?9365-RGB-via-SCART")[/COLOR])[/COLOR]

CRT2: LCD

> 

root@linux:~# xrandr --newmode "800x600a" 16,48 800 840 920 1040 600 602 605 627 interlace -hsync -vsync

root@linux:~# xrandr --addmode CRT1 800x600a

root@linux:~# xrandr
Screen 0: minimum 320 x 200, current 1680 x 1050, maximum 1680 x 1680
DFP1 disconnected (normal left inverted right x axis y axis)
DFP2 disconnected (normal left inverted right x axis y axis)
CRT1 connected 720x480+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1600x1200      60.0 +
   1400x1050      60.0
   1280x1024      60.0     47.0     43.0
   1440x900       59.9
   1280x960       60.0
   1280x800       60.0
   1152x864       60.0     47.0     43.0
   1280x768       59.9     56.0
   1280x720       60.0     50.0
   1024x768       60.0     43.5
   800x600        60.3     56.2     47.0     24.5
   720x576        50.0
   720x480        60.0     28.7*
   640x480        60.0
   720x480a       28.7
   800x600a       24.5
CRT2 connected 1680x1050+0+0 (normal left inverted right x axis y axis) 474mm x 296mm
   1680x1050      59.9*+
   1400x1050      60.0
   1280x1024      75.0     60.0
   1440x900       59.9
   1280x960       75.0     60.0
   1280x800       75.0     60.0
   1152x864       75.0     60.0
   1280x768       74.9     59.9
   1280x720       60.0
   1024x768       75.0     60.0
   800x600        75.0     60.3     56.2
   720x480        60.0     28.7
   640x480        75.0     60.0
   720x480a       28.7
TV disconnected (normal left inverted right x axis y axis)
CV disconnected (normal left inverted right x axis y axis)
  256x256@59,496 (0xcd)    5.0MHz
        h: width   256 start  268 end  292 total  330 skew    0 clock   15.2KHz
        v: height  256 start  257 end  260 total  273           clock   55.5Hz
  256x256a (0xce)    5.0MHz
        h: width   256 start  268 end  292 total  330 skew    0 clock   15.2KHz
        v: height  256 start  257 end  260 total  273           clock   55.5Hz
  352x256@59,697 (0xcf)    7.0MHz
        h: width   352 start  368 end  400 total  450 skew    0 clock   15.6KHz
        v: height  256 start  257 end  260 total  271           clock   57.4Hz
  640x288 (0xd0)   13.0MHz
        h: width   640 start  672 end  736 total  832 skew    0 clock   15.6KHz
        v: height  288 start  289 end  292 total  309           clock   50.6Hz
root@linux:~# xrandr --output CRT1 --mode 800x600a # TV

still over 15 khz!

---

