---
title: "Dual Monitors: Tips/Tricks for Usability"
date: 2007-08-10
forum: Multimedia &amp; Video
---

### Post by jamesrl on 2007-08-10
I was wondering if I could start a thread with tips/tricks for usability with multiple desktops.  
Right now, using the Gutsy xserver-xorg with xrandr to set up my dual monitors (described in _[this post]("http://ubuntuforums.org/showpost.php?p=3151046&postcount=5")_); it seems to work great with my two 1680x1050 displays in metacity (beryl/compiz won't work as GL_MAX_TEXTURE_SIZE is 2048 as shown by **glxinfo -l | grep GL_MAX_TEXTURE_SIZE**.

I would like a window manager that will let me do convenient things for dual monitors.  Things like, keyboard shortcuts to move a window to the other monitor (much like how you can move windows to other desktops) without having to drag it via the mouse.  So I wrote a script to do just that.


First, install wmctrl  (**sudo apt-get install wmctrl**), which allows in most window managers (enlightenment, Kwin, Xfce, icewm, metacity, etc.) to move windows via the command line.

Then write this script to an executable file somewhere (gotten from [http://my.opera.com/raphman/blog/index.dml/tag/Linux](http://my.opera.com/raphman/blog/index.dml/tag/Linux). though i had to modify slightly):
Personally I put this in ~/local/bin/swap_monitor.sh
(may have to **mkdir ~/local** and then **mkdir ~/local/bin** then **gedit ~/local/bin/swap_monitor.sh**).  (Just cut and paste).

```

#!/bin/bash
# swap_monitor.sh
# Moves the active window to the other screen of a dual-screen Xinerama 
setup.
#
# Requires: wmctrl, xprop, xwininfo
#
# Author: Raphael Wimmer
# raphman@gmx.de

# get monitorWidth
monitorLine=$(xwininfo -root | grep "Width")
monitorWidth=$((${monitorLine:8}/2 ))
echo $monitorWidth

# get active window id
activeWinLine=$(xprop -root | grep "_NET_ACTIVE_WINDOW(WINDOW)")
activeWinId="${activeWinLine:40}"

# get window position
xPosLine=$(xwininfo -id $activeWinId | grep "Absolute upper-left X")
xPos=${xPosLine:25} 

# get window width
xWidthLine=$(xwininfo -id $activeWinId | grep "Width")
xWidth=${xWidthLine:8}

# calculate new window position
if (( ${xPos} + ${xWidth}/2  > ${monitorWidth} ))
  then xPos=$(( ${xPos} -  ${monitorWidth}))
  else xPos=$(( ${xPos} +  ${monitorWidth}))
fi

# make sure window stays on screen completely
(( ${xPos} < 0 )) && xPos=0 
(( ${xPos} + ${xWidth} > 2 * ${monitorWidth} )) && 
xPos=$((2*${monitorWidth} - ${xWidth}))

echo ${xPos}

# if maximized store info and de-maximize
winState=$(xprop -id ${activeWinId} | grep "_NET_WM_STATE(ATOM)"  )  

if [[ `echo ${winState} | grep "_NET_WM_STATE_MAXIMIZED_HORZ"` != ""  ]]
then 
  maxH=1
  wmctrl -i -r ${activeWinId} -b remove,maximized_horz 
fi

if [[ `echo ${winState} | grep "_NET_WM_STATE_MAXIMIZED_VERT"` != ""  ]]
then
  maxV=1
  wmctrl -i -r ${activeWinId} -b remove,maximized_vert
fi

# move window (finally)
wmctrl -i -r ${activeWinId} -e 0,${xPos},-1,-1,-1

# restore maximization
((${maxV})) && wmctrl -i -r ${activeWinId} -b add,maximized_vert
((${maxH})) && wmctrl -i -r ${activeWinId} -b add,maximized_horz

# raise window (seems to be necessary sometimes)
wmctrl -i -a ${activeWinId}

# and bye
exit 0

```

Save the script, set it to executable **chmod 755 ~/local/bin/swap_monitor.sh** and added a run_command / hotkey in gconf-editor.
That is open gconf-editor, go to /apps/metacity/global_keybindings, then set run_command_1 to say some key command (I used F9).  Then go down to /apps/metacity/keybinding_commands and change command_1 to /home/[ENTER YOUR LOGIN NAME HERE]/local/bin/swap_monitor.sh

Also personally I found it useful to write quick scripts, to switch between one display, two displays, and cloned display (same thing on both).  

one_display.sh
```

#!/bin/sh
## MUST Disconnect second monitor first or will just do cloned display!
xrandr --output VGA --auto

```

cloned_desktop.sh
```

#!/bin/sh
xrandr --output VGA --same-as LVDS

```

two_desktop.sh
```

#!/bin/sh
xrandr --output VGA --left-of LVDS --auto

```

though these scripts should only work with the Gutsy/xrandr method of dual monitors.  You can hotkey them as described above, too, if you want.


I also found a C script for switching your mouse pointer between displays [http://blog.tobez.org/?p=41]("http://blog.tobez.org/?p=41"), however it seems to work for situations where X reports multiple screens, however my situation is X sees just one large virtual machine as shown by the output of xrandr:

```
Screen 0: minimum 320 x 200, current 3360 x 1050, maximum 3360 x 1050
VGA connected 1680x1050+0+0 (normal left inverted right) 474mm x 296mm
   1680x1050      60.0*+   60.0  
   1280x1024      59.9  
   1440x900       59.9     59.9  
   640x480        60.0  
LVDS connected 1680x1050+1680+0 (normal left inverted right) 331mm x 207mm
   1680x1050      60.1*+
   1280x800       60.0  
   1280x768       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
TV disconnected (normal left inverted right)
```

If I get around to it, I'll modify the C code to my 1 large virtual screen needs.

---

### Post by _simon_ on 2007-08-10
I hope this isn't off topic but I run 2960x1050 via 2 screens and it works in Compiz-Fusion.

```

simon@GhostTouch:~$ glxinfo -l | grep GL_MAX_TEXTURE_SIZE.
    GL_MAX_TEXTURE_SIZE = 4096

```

Just confused as to why yours is only 2048? Does it depend on the graphics card used?

---

### Post by jamesrl on 2007-08-10
It is graphic card dependent.  You can see specs for various cards:
[http://www.delphi3d.net/hardware/listreports.php]("http://www.delphi3d.net/hardware/listreports.php")
And my intel 945GM isn't good enough for two large displays side by side.  I guess if I really wanted desktop effects,  and two displays I could lower the resolution on one display (to say 1440x900), and stack them above each other as 1050+900  is less than 2048.   However, then i'd have to deal with other issues (lower resolution, mismatched desktop size, and having to get to other desk  by going over top and bottom of display).

Unfortunately since I have a laptop with a graphics card built-in on the motherboard, I can't change this.

---

### Post by jamesrl on 2007-08-11
Well I started thinking about what features would make using dual monitors, functionally much easier.

1) Separate window lists.  Right now I have a window list displayed at the bottom of one monitor, despite it containing all the information about windows on the current desktop for both monitors.  It would be much easier to look for the application I want to switch to if separate window lists were maintained, dependent on which monitor they (primarily) are on.

2) When switching focus to a new window, choose one from the current monitor.  Currently, if I am looking at one monitor, see three windows and want to close all of them, I press Alt-F4 three times.  However, after the first one, I may refocus to the other desktop and accidentally close the wrong window.

3) Have a keyboard shortcut to quickly switch active 'monitor'.  When pressed the mouse goes to the other monitor (in some sort of logical place; the center of the screen or last location on that screen; unless the mouse was just dragged over to the other screen), and focus gets shifted to the last focused window in that monitor.

4) Easy control of which monitor a new window opens up on.  [Note if X thinks you have two screens ":0.0" and ":0.1" you can control this from the command line with typing  [ DISPLAY="0.0" ] before the command (without the brackets).  For example the following commands would open xeyes on each monitor.

DISPLAY="0.0" xeyes
DISPLAY="0.1" xeyes

However, this doesn't work on my xrandr setup as it see just one display ":0.0" that is 3360x1050.

5) Be able to quickly move any window to the other monitor. [Implemented above with wmctrl.]

Was wondering if anyone had any suggestions for how to try arranging these things.  Like a way to get an extremely configurable taskbar/focus control/etc.

---

### Post by nzadLithium on 2007-08-11
I'm wondering how to make it so opengl apps dont take over both screens. Atm if i put any opengl app in fullscreen it blacks out the other one. It makes it really hard to use pidgin while i'm playing games. And since i have to run them in windowed mode i usually end up missing the bottom 2 cm of the opengl window :s

---

### Post by jamesrl on 2007-08-13
Further thoughts.
Been trying to explore the variety of window managers out there.  Tried enlightenment e17 and enlightenment e16 as well as gnome with metacity.

E17 seems to have the right idea for how to treat dual monitors. In e17, each monitor had its own set of 4 'virtual' desktops, that were independent of the other monitor.  [E.g., you can start a movie on monitor 1 in desktop A, and then flip through 4 desktops on the monitor 2 while working].  It also would have separate window lists for each monitor; if you alt-tab it would keep only run through windows open on that monitor (or if you closed windows the focus would go to another window in that monitor).   You could drag windows between monitors easy enough.  It also somewhat kept track of "shelves" (what I would call panels from gnome) for the second monitor, even when you switch to one monitor mode, and then back to two monitor mode.  [Basically, when you switch to one monitor mode, it loses the second shelf; however, when you are back in two monitor mode, and try and create a new shelf, it brings back the 2nd shelf as it was last configured.  I think with more tweaking I could do this from the command line automatically when switching to two monitor mode]  

However, I found the themes to be very ugly and annoying (to many animations), and takes some effort to change the theme (edit a bunch of images), and the five themes at get-e.org don't much better.  Also, e17 is buggy and in the course of ~1.5 days crashed (to having to logout/login again) about 5 times (popping up "Enlightment crashed message; please restart].  Some of these crashes definitely seemed to be for reasons unrelated to the dual monitors (tied to doing certain events like trying to create an icon by some method), though others came for seemingly no reason so can't tell.

After this, I tried enlightenment 16 with Gnome, hoping to get lucky; but couldn't seem to get any improvement over the dual monitor handling over gnome with metacity.

Will try more (IceWM, FVHM, xfce, openbox, etc.) when I get the time and post results here ....  If anyone knows a good WM for dual monitors please let me know.

---

### Post by Cyphase on 2007-11-04
> **jamesrl said:**
> Well I started thinking about what features would make using dual monitors, functionally much easier.

1) Separate window lists.  Right now I have a window list displayed at the bottom of one monitor, despite it containing all the information about windows on the current desktop for both monitors.  It would be much easier to look for the application I want to switch to if separate window lists were maintained, dependent on which monitor they (primarily) are on.

You can already do that, at least in Gnome. Just create a new panel, drag it over to the other monitor, and add a window list. It'll automatically take over for the windows on that monitor, and any window of which more than half is on a particular monitor will appear on that monitors window list.

---

### Post by gfixler on 2007-11-23
Thank you so much for sharing this! I've had a heck of time this week looking up information on how to do many of the things you're doing here, and haven't been able to find via searches the utilities that give me power over windows. I knew xwininfo, and one or two others, but wmctrl, xprop, and several things you do here have eluded me.

I'm using these on a Matrox TripleHead2Go now. I have Ctrl+Super+1/2/3 rigged to move and scale the active window to each of the 3 screens, and added an additional set of hotkeys - Alt+Super+1/2/3 to move/scale a window to center it on each screen at 600x500. I'd like to learn more, possibly using pygtk, or libwnck, or things I've not yet discovered to take far more control over these things, as this is kind of hackish at the moment. Still, it's so nice to have a way to quickly snap and scale a window to a usable place.

Have you ever discovered a quick way to undecorate/decorate a window? I see things in e.g., pygtk, but don't know how to turn a window ID into an actual window object I can manipulate.

Btw, in Gutsy, I don't have to use the gconf for this anymore. I just go to System->Preferences->Advanced Desktop Effects Settings, and in the General section, modify things in the Commands and Actions tabs. Feels a bit simpler to get to. And the commands are simple with wmctrl. E.g. to scale and move a window to nicely take up the center screen (considering the top/bottom panels) at the 3840x1024 resolution the Matrox box presents to the PC as a single monitor, the command is simply this:

wmctrl -r :ACTIVE: -e 1280,1280,0,1280,950

I'm going to mention the concept of setting up virtual screen borders to the Compiz Fusion guys. Not only would it allow people like me with 1 screen spanning multiple displays to simply use the built-in maximize and fullscreen features on single monitors, but you could set up horizontal and vertical lines anywhere that way, and if you like, divide one display into 2 parts, and maximize two things to each - great for people with widescreens who want to throw up 2 pages to compare, or read side-by-side. The TH2G's Windows driver fakes border edges that way, and you can maximize as usual to whatever display your window is mostly on, or hold Ctrl while maximizing to span the whole thing. That would rule.

Thanks again!

---

### Post by ktulu1115 on 2007-11-30
Would anyone have an idea of how to do this (if even possible) without Xinerama, ie: running two X separate displays?  I know you can set DISPLAY environment variable as jamesrl outlined, which works great - but I want this functionality for already open windows.  I've been wondering about this for some time now but have never come across any promising leads.  Any ideas?

---

### Post by gfixler on 2008-06-02
I just wanted to pop in with a link to a heavily modified version of your code, which I just posted here:

[http://ubuntuforums.org/showthread.php?t=815925](http://ubuntuforums.org/showthread.php?t=815925)

It links here, and speaks of my somewhat unique setup, and how I used your stuff to get what I needed. I thank you again, as this is the single place I've been able to find in a year now with this info all in one place, and even this is hard to find. Words like "screen," and "windows" are just so common!

Anyway, thanks again.

---

