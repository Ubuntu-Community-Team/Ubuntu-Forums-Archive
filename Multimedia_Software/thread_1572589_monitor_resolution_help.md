---
title: "monitor resolution help"
date: 2010-09-11
forum: Multimedia Software
---

### Post by rockychrysler on 2010-09-11
fairly new to ubuntu/linux.  been running ubuntu netbook happily for some time; impressed with its ease of use, install, updates, etc.  even done a few command line tasks...

kinda sick of windows 7, but also really intrigued by linux, i installed 10.04 lts on our desktop last night (clean, no partition). install went fine. but ubuntu's monitors control panel shows a maximum screen resolution of 1024x768.  we use this machine on our widescreen tv, so this resolution is pretty unacceptable.

followed the prompt to install the proprietary nvidia driver and, following install, lost the 1024 resolution choice and now have a max of only 640x480.  kinda sukt.  couldn't figure out how to put it back as it was (or how to successfully uninstall the nvidia driver) so i reinstalled ubuntu.  now i'm back to a max res of 1024.  better than 640, but not by much.

i've been reading threads all night and all morning trying to figure out a simple fix for this problem.  i can't find one.  hoping someone on this forum can advise me or direct me to a thread that comprehensible to a newb.

i really want to keep ubuntu.  i'd like to someday begin playing with mythbuntu (we've used this box as windows htpc for some time).  but unless i can fix the screen resolution dealio, i guess i'm gonna have to reinstall windows 7.

---

### Post by rockychrysler on 2010-09-11
while waiting for help i've succeeded in getting a workable resolution on my own... in general, i followed the steps in this thread [http://ubuntuforums.org/showthread.php?t=1112186](http://ubuntuforums.org/showthread.php?t=1112186) but i don't know how to save it permanently.  when i restart, i have to go thru the whole process again.

here's what i did to get a working resolution of 1360x768 at 59mhz (pardon some of the junk)

PLEASE, someone tell me how to SAVE the setup PERMANENTLY! 

fwiw, i guess i've got no xorg.conf flile. since i get nothing but a blank when i sudo gedit xorg.conf.

> rockychrysler@rockychrysler:~$ gtf 1366 768 60

  # 1368x768 @ 60.00 Hz (GTF) hsync: 47.70 kHz; pclk: 85.86 MHz
  Modeline "1368x768_60.00"  85.86  1368 1440 1584 1800  768 769 772 795  -HSync +Vsync

rockychrysler@rockychrysler:~$ xrandr --newmode "1368x768_60.00"  85.86  1368 1440 1584 1800  768 769 772 795  -HSync +Vsync
rockychrysler@rockychrysler:~$ xrandr
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 4096 x 4096
VGA-1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0* 
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9  
  1368x768_60.00 (0x16c)   85.0MHz
        h: width  1368 start 1440 end 1584 total 1800 skew    0 clock   47.2KHz
        v: height  768 start  769 end  772 total  795           clock   59.4Hz
rockychrysler@rockychrysler:~$ gtf 1360 768 60

  # 1360x768 @ 60.00 Hz (GTF) hsync: 47.70 kHz; pclk: 84.72 MHz
  Modeline "1360x768_60.00"  84.72  1360 1424 1568 1776  768 769 772 795  -HSync +Vsync

rockychrysler@rockychrysler:~$ gtf 1365 768 60

  # 1368x768 @ 60.00 Hz (GTF) hsync: 47.70 kHz; pclk: 85.86 MHz
  Modeline "1368x768_60.00"  85.86  1368 1440 1584 1800  768 769 772 795  -HSync +Vsync

rockychrysler@rockychrysler:~$ gtf 1364 768 60

  # 1360x768 @ 60.00 Hz (GTF) hsync: 47.70 kHz; pclk: 84.72 MHz
  Modeline "1360x768_60.00"  84.72  1360 1424 1568 1776  768 769 772 795  -HSync +Vsync

rockychrysler@rockychrysler:~$ gtf 1363 768 60

  # 1360x768 @ 60.00 Hz (GTF) hsync: 47.70 kHz; pclk: 84.72 MHz
  Modeline "1360x768_60.00"  84.72  1360 1424 1568 1776  768 769 772 795  -HSync +Vsync

rockychrysler@rockychrysler:~$ xrandr --addmmode VGA-1 "1360x768_60.00"  84.72  1360 1424 1568 1776  768 769 772 795  -HSync +Vsync
usage: xrandr [options]
  where options are:
  -display <display> or -d <display>
  -help
  -o <normal,inverted,left,right,0,1,2,3>
            or --orientation <normal,inverted,left,right,0,1,2,3>
  -q        or --query
  -s <size>/<width>x<height> or --size <size>/<width>x<height>
  -r <rate> or --rate <rate> or --refresh <rate>
  -v        or --version
  -x        (reflect in x)
  -y        (reflect in y)
  --screen <screen>
  --verbose
  --dryrun
  --nograb
  --prop or --properties
  --fb <width>x<height>
  --fbmm <width>x<height>
  --dpi <dpi>/<output>
  --output <output>
      --auto
      --mode <mode>
      --preferred
      --pos <x>x<y>
      --rate <rate> or --refresh <rate>
      --reflect normal,x,y,xy
      --rotate normal,inverted,left,right
      --left-of <output>
      --right-of <output>
      --above <output>
      --below <output>
      --same-as <output>
      --set <property> <value>
      --scale <x>x<y>
      --transform <a>,<b>,<c>,<d>,<e>,<f>,<g>,<h>,<i>
      --off
      --crtc <crtc>
      --panning <w>x<h>[+<x>+<y>[/<track:w>x<h>+<x>+<y>[/<border:l>/<t>/<r>/<b>]]]
      --gamma <r>:<g>:<b>
      --primary
  --noprimary
  --newmode <name> <clock MHz>
            <hdisp> <hsync-start> <hsync-end> <htotal>
            <vdisp> <vsync-start> <vsync-end> <vtotal>
            [+HSync] [-HSync] [+VSync] [-VSync]
  --rmmode <name>
  --addmode <output> <name>
  --delmode <output> <name>
rockychrysler@rockychrysler:~$ xrandr --newmode "1360x768_60.00"  84.72  1360 1424 1568 1776  768 769 772 795  -HSync +Vsync
rockychrysler@rockychrysler:~$ xrandr
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 4096 x 4096
VGA-1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0* 
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9  
  1368x768_60.00 (0x16c)   85.0MHz
        h: width  1368 start 1440 end 1584 total 1800 skew    0 clock   47.2KHz
        v: height  768 start  769 end  772 total  795           clock   59.4Hz
  1360x768_60.00 (0x16d)   84.0MHz
        h: width  1360 start 1424 end 1568 total 1776 skew    0 clock   47.3KHz
        v: height  768 start  769 end  772 total  795           clock   59.5Hz
rockychrysler@rockychrysler:~$ xrandr --addmode VGA-1 1360x768_60.00
rockychrysler@rockychrysler:~$ 
rockychrysler@rockychrysler:~$ xrandr
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 4096 x 4096
VGA-1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0* 
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9  
   1360x768_60.00   59.5  
  1368x768_60.00 (0x16c)   85.0MHz
        h: width  1368 start 1440 end 1584 total 1800 skew    0 clock   47.2KHz
        v: height  768 start  769 end  772 total  795           clock   59.4Hz
rockychrysler@rockychrysler:~$ xrandr --output VGA-1 --mode 1360x768_60.00
rockychrysler@rockychrysler:~$ sudo gedit /etc/X11/xorg.conf
[sudo] password for rockychrysler: 
rockychrysler@rockychrysler:~$ xrandr
Screen 0: minimum 320 x 200, current 1360 x 768, maximum 4096 x 4096
VGA-1 connected 1360x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0  
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9  
   1360x768_60.00   59.5* 
  1368x768_60.00 (0x16c)   85.0MHz
        h: width  1368 start 1440 end 1584 total 1800 skew    0 clock   47.2KHz
        v: height  768 start  769 end  772 total  795           clock   59.4Hz
rockychrysler@rockychrysler:~$ 

---

