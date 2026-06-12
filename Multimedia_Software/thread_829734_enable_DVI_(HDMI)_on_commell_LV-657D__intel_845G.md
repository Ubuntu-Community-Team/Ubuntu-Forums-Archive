---
title: "enable DVI (HDMI) on commell LV-657D / intel 845G"
date: 2008-06-15
forum: Multimedia Software
---

### Post by vanatteveldt on 2008-06-15
Dear Forum,


I am fairly new to linux; I am building a box (for mythtv) using a commell LV-675D motherboard, which has Intel integrated graphics (I think 845G) and DVI out. I installed ubuntu 8.04 and everything works fine on a normal monitor. I want to connect the machine to my TV using the DVI out and a DVI->HDMI cable.

I was hoping that I could just connect the machine to my TV and boot up, but unfortunately it does not show anything.

Since I don't have a mobile screen (my two normal desktop screens are screwed to the wall) I decided to test by connecting one screen to the VGA port and the other to the DVI using a VGA-to-DVI dongle. This works for my (windows) desktop to get dual screen. I cannot get the second screen to be used.

I tried using xrandr to activate the second screen:

wva@huis:~$ xrandr
Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 1280 x 1280
VGA connected 1280x1024+0+0 (normal left inverted right x axis y axis) 338mm x 270mm
   1280x1024      60.0*+   75.0     59.9
   1280x960       59.9
   1152x864       75.0     74.8
   1024x768       75.1     70.1     60.0
   832x624        74.6
   800x600        72.2     75.0     60.3     56.2
   640x480        75.0     72.8     66.7     60.0
   720x400        70.1
TMDS connected (normal left inverted right x axis y axis)
   1280x800       60.0
   1280x768       60.0
   1024x768       60.0
   800x600        60.3
   640x480        59.9
wva@huis:~$ xrandr --output TMDS --auto
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  156 (RANDR)
  Minor opcode of failed request:  21 ()
  Serial number of failed request:  15
  Current serial number in output stream:  15
wva@huis:~$ xrandr --output TMDS --mode 1024x768 --pos 0x0

The last line causes the VGA to go black but does not enable the second monitor. I put this into a shell script to execute xrandr -c after it and then swtich the TMDS off again to see what it did, and this is the outpu:

wva@huis:~$ cat test
xrandr --output VGA --mode 1280x1024 --pos 0x0
xrandr --output TMDS --mode 1024x768 --pos 0x0
xrandr
xrandr --output VGA --auto --output TMDS --off

wva@huis:~$ bash test
Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 1280 x 1280
VGA connected 1024x768+0+0 (normal left inverted right x axis y axis) 338mm x 270mm
   1280x1024      60.0 +   75.0     59.9
   1280x960       59.9
   1152x864       75.0     74.8
   1024x768       75.1     70.1     60.0*
   832x624        74.6
   800x600        72.2     75.0     60.3     56.2
   640x480        75.0     72.8     66.7     60.0
   720x400        70.1
TMDS connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1280x800       60.0
   1280x768       60.0
   1024x768       60.0*
   800x600        60.3
   640x480        59.9

So it seems that it does activate the TMDS (it gets an asterisk), but (a) deactivates the VGA and (b) does not display.

using i810 switch lcd on does not seem to help

There are some lines in the Xorg.0.log that I do not understand:

(II) intel(0): Creating default Display subsection in Screen section
        "Default Screen" for depth/fbbpp 24/32
(==) intel(0): Depth 24, (==) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) 845G
(--) intel(0): Chipset: "845G"
(--) intel(0): Linear framebuffer at 0xE0000000
(--) intel(0): IO registers at addr 0xEC100000
(II) intel(0): 1 display pipe available.
(==) intel(0): Using EXA for acceleration
[...]
(II) intel(0): Output configuration:
(II) intel(0):   Pipe A is on
(II) intel(0):   Display plane A is now enabled and connected to pipe A.
(II) intel(0):   Output VGA is connected to pipe A
(II) intel(0):   Output TMDS is connected to pipe none


So it seems to say that it only has one pipe available, and that TMDS is somehow connected to pipe none. I have no idea what a pipe is but it doesn't sound good :-)

Can anyone help?

Thanks!

-- Wouter

---

### Post by mathew_davis on 2008-07-14
Just ondering if you got this figured out or not?  I am experiancing a similar problem.  I have an intel board and I am trying to activate the on board HDMI but can't seem to figuret out.  Luckily my LCD tv accepts VGA or I would be in trouble but I would also like to pipe the sound so I would like to get this working.  Any luck?

---

### Post by rob.webinator on 2008-08-08
Maybe this is off your topic but here goes.  I am just trying to figure out how to enable DVI for my one monitor.  I have:
Video card: nVidia Corporation NV34 [GeForce FX 5500] (rev a1)
Monitor: Acer AL2016WBbd

VGA works fine but when I connect the monitor to video card via DVI, I get "No input signal".

I figure this is a basic problem and I just need to do something very simple.  Any help appreciated!

---

