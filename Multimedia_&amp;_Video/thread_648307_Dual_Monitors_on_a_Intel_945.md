---
title: "Dual Monitors on a Intel 945"
date: 2007-12-23
forum: Multimedia &amp; Video
---

### Post by steveyboy on 2007-12-23
Hi all,

I installed Gutsy last week and got it running good on my laptop with an Intel 945GM graphics card. I have hooked it up to a LG LCD monitor, when I load the desktop, the resolution is fine, 1280x1024 on the LG monitor, however when I maximise the windows. they maximise to 1280x800 (which is the resolution of the laptop monitor, I use Awn,and the task panel appears at the bottom of the screen. I have tried switching the laptop to only use VGA out, but that does not work, the LCD screen goes black, then both monitors turn on. If I turn off the laptop monitor, when I open or maximise a window, the monitor turns back on.

I would like to run a dual monitor system, but whenever I run

xrandr -q

I get:

Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 1280 x 1024
VGA connected 1280x1024+0+0 (normal left inverted right) 376mm x 301mm
   1280x1024      60.0*+   75.0     59.9  
   1280x1024@60   60.0  
   1280x960@60    60.0  
   1152x864       75.0  
   1024x768       74.9     75.1     60.0  
   1024x768@60    60.0  
   832x624        74.6  
   800x600        75.0     74.9     60.3  
   800x600@60     60.3  
   800x600@56     56.2  
   640x480        75.0     74.8     60.0  
   640x480@60     60.0  
   720x400        70.1  
LVDS connected 1280x800+0+0 (normal left inverted right) 331mm x 207mm
   1280x800       60.0*+   60.0  
   1280x768       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
TV disconnected (normal left inverted right)

When I run:

xrandr --output VGA --right-of LVDS

I get:
xrandr: screen cannot be larger than 1280x1024 (desired size 2560x1024)

I have attached my xorg.conf. What am I doing wrong?

---

### Post by TheWheat on 2008-01-19
> 
xrandr: screen cannot be larger than 1280x1024 (desired size 2560x1024)

This can be solved by changing "Virtual 1280    1024" to "Virtual 2560    1024". That worked for me using your xorg.conf.
[This]("http://www.thinkwiki.org/wiki/Xorg_RandR_1.2") link may provide more help if needed. I just got my extended desktop working but now I am tackling the laptop screen not being used as the primary display problem =(
Hope that helps!

---

