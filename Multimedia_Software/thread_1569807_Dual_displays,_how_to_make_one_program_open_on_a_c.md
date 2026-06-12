---
title: "Dual displays, how to make one program open on a certain monitor?"
date: 2010-09-07
forum: Multimedia Software
---

### Post by Bicko on 2010-09-07
Hi all,

I have a laptop with an extra monitor attached, working nicely using xrandr.  Xrandr sees these displays as LVDS1 and VGA1, respectively.

I have created a shortcut on the screen that will start a certain videoclip playing at fullscreen.  However, I need this video to always play on the external monitor, not the laptop screen.

Is there a command that will force this to happen each time?
ie something that will direct a program to place its window on a specific display.

Thanks for your help with this, searching is proving fruitless as I really don't know what terms to search for.

Regards,
Bicko.

---

### Post by lykeion on 2010-09-07
I have a monitor and a lcd-tv setup as two separate screens (no xinerama).

You can find the DISPLAY variable by opening up a terminal in each screen and entering```
echo $DISPLAY
```For me it's :0.0 (monitor) and :0.1 (lcd-tv)
With this information I can set which screen the application should open up in, like this (using firefox as an example):```
DISPLAY=":0.1" firefox 
```(will open up in lcd-tv)
Hope this helps...and don't forget to tag thread as SOLVED to help others find solutions easily.

---

### Post by Bicko on 2010-09-07
Thanks for the reply.

I should have mentioned that I've tried DISPLAY=":0.x".

Xrandr shows that both monitors are being treated as one display, Screen0, which I think is why the DISPLAY= method isn't working.

LVDS1 is 1366x768, VGA1 is 1280x1024, "Screen0" is quoted as being 2646x1024. ie the same as both 'real' displays side-by-side.

I really don't want to have to reconfigure things so that each screen is a genuinely different "DISPLAY", because things are running great right now, apart from this one issue.  However, if it's the only way....!

Thanks again.

---

### Post by wkulecz on 2010-09-07
See if your application supports the X Windows --geometry=WidthxHeight+Xoffset+Yoffset option on startup.

---

### Post by Bicko on 2010-09-07
Thanks for the suggestion.

I'm using totem to play the video.  Totem doesn't support the --geometry=... option, but mplayer sort of does.  I'm not fussy what tool I use to play the video so I've had a long play with mplayer tonight, trying to use its own -geometry option to position the window on the other screen.  However, I have not had any success.

Mplayer's -geometry setting is fine for positioning the video anywhere within the laptop screen (LVDS1) and I thought this was going to be the answer to my problem. But as soon as I try to position it in the other screen (VGA1) by using an x value greater than 1366, it simply places the window at x=0. In fact, I only have to overlap it from one screen to the next and it also refuses, and places the window at full left (x=0).

My original question was whether it is possible to direct ANY program to a specific screen, but I would have been happy to have just got mplayer to do it.

If it's any use, here is the output from xrandr -q...
```
$ xrandr -q
Screen 0: minimum 320 x 200, current 2646 x 1024, maximum 8192 x 8192
VGA1 connected 1280x1024+1366+0 (normal left inverted right x axis y axis) 338mm x 270mm
   1280x1024      60.0*+   75.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1  
LVDS1 connected 1366x768+0+0 (normal left inverted right x axis y axis) 344mm x 193mm
   1366x768       60.0*+
   1360x768       59.8  
   1024x768       85.0     75.0     70.1     60.0  
   832x624        74.6  
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     59.9  
   720x400        85.0  
   640x400        85.1  
   640x350        85.1  
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)
DP2 disconnected (normal left inverted right x axis y axis)
$

```
Any more ideas?
Thanks.

---

### Post by Bicko on 2010-09-10
Hi again,

I'm still using my workaround; fire up the video (via a shortcut to a totem command), drag the window to the desired display, hit 'F' to make it full screen.

Has anyone got an idea of how this can go directly to the desired display?

Appreciating any pointers at all !
Cheers.

---

### Post by AutoStatic on 2010-09-10
Try the **wmctrl** package.

---

