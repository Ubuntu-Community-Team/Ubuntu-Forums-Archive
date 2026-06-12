---
title: "Working on Dual Monitor Fullscreen Flash Fix"
date: 2011-08-20
forum: Multimedia Software
---

### Post by stealz on 2011-08-20
I am working on this fix in Ubuntu Lucid Lynx 10.04 with gnome and compiz

I've  had problems with Flash, namely it opening on the wrong monitor, and  not staying in fullscreen when other applications are focused.  I was able to move the flash fullscreen window (or any other window for  that matter) to the other monitor using an sh script I will show you  later in this thread.  

However it has a few issues if your monitors have different resolutions:[INDENT]- Sometimes the fullscreen video will have the aspect  ratio of the Monitor that spawned it, so the browser window should be in  the window you will want to watch the video in. 
[/INDENT][INDENT]- Sometimes the fullscreen video will have  the aspect ratio of the Monitor that it spawns in, and will not resize  when moved to a different Monitor. 
[/INDENT]For this script you need the **xdotool** and **wmctrl** packages which you can get by typing the following command in a terminal:

```
sudo apt-get install xdotool && sudo apt-get install wmctrl
```Now you create an empty file with an .sh extension, I named mine "move-window-monitor.sh" and paste the following code in it:
NOTE:  you might have to modify the screen_width1 and screen_width2 values to  match your left (1) and right (2) monitor horizontal resolution  (my  monitors are 1680x1050 and 1920x1080)

```

#!/bin/bash
 
# screen width
screen_width1=1680
screen_width2=1920
 
# active window
window=`xdotool getactivewindow`
 
# get active window size and position
x=`xwininfo -id $window | grep "Absolute upper-left X" | awk '{print $4}'`
w=`xwininfo -id $window | grep "Width" | awk '{print $2}'`
 
maximized=false
 
# window on left monitor
if [ "$x" -lt "$screen_width1" ]; then
    if [[ "$w" -eq "$screen_width1" ]]; then
     maximized=true
   fi
    
 
    if $maximized; then
        wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz
    fi
 
    wmctrl -r :ACTIVE: -e 0,$screen_width1,-1,-1,-1
 
    if $maximized; then
        wmctrl -r :ACTIVE: -b add,maximized_vert,maximized_horz
    fi
 
# window on right monitor
else
   if [[ "$w" -eq "$screen_width2" ]]; then
     maximized=true
   fi
 
    if $maximized; then
        wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz
    fi
 
    wmctrl -r :ACTIVE: -e 0,0,-1,-1,-1
 
    if $maximized; then
        wmctrl -r :ACTIVE: -b add,maximized_vert,maximized_horz
    fi
 
fi

```NOTE:  I did not create this script, I found it on  [http://sabel.bluegfx.de/2011/05/30/linux-aktives-fenster-auf-anderen-monitor-verschieben/](http://sabel.bluegfx.de/2011/05/30/linux-aktives-fenster-auf-anderen-monitor-verschieben/)  and modified it a bit to fit my needs.

now you will have to make the file executable by entering the following command in a terminal:
```
sudo chmod +x move-window-monitor.sh
```now go to System/Preferences/Keyboard Shortcuts
add  a custom shortcut and enter move-window-monitor.sh as command and  assign it to a key (I use the WinKey+Left and WinKey+Right both linked  to this command).

Now whenever you press your key combination,  the active window will be moved to the other monitor. Note that your  Flash Fulllscreen window will not be the active window by default when  opened, so you will usually have to click inside of it (I usually click  Play/Pause twice).

**What is left to be done / Might be possible to archieve:**
I've tried resizing the fullscreen window by using  
```
wmctrl -r :ACTIVE: -e 0,1680,0,1920,1080
```Syntax: wmctrl -r :ACTIVE: -e gravity,x-pos,y-pos,width,height
and 
```
wmctrl -r :ACTIVE:  -b add,maximized_vert,maximized_horz
```Which  results in an increase of the flash window container size. However, the  Video stays the same size and doesnt adapt to the window size. This  means that there will be an invisible Window  around the flash video  that you cannot click through.
HOWEVER - somewhere along these tries  the flash video became resistant to losing focus - meaning I could work  in a different window while the flash stays fullscreen.

**What I could use help with:**
What  I am looking for is a better way to target the flash window so it  doesnt have to be the active window. Since it is very hard to capture  the window class, I was only able to use 
```
sleep 5 && wmctrl -l
```to get the window title, which is <unknown> so not necessarily very unique.

What  would also be very nice is some kind of script that would help resize  the flash to fit the window/screen size. Maybe by using a GreaseMonkey  Script. But this is beyond my skillset and experience, so it might take  some time to research and figure that one out.  [B]

Known Problems
[/B]The script will not work properly on Firefox windows if using the[FONT=Arial][SIZE=1] Hide Caption Titlebar Plus [/SIZE][/FONT]firefox addon. It will still work on the Flash Fullscreen window spawned by firefox.

---

### Post by Jaylor on 2012-12-27
Or you if you're talking about this issue with the Adobe Flash plugin you could just  goto my post about this issue in another thread [http://ubuntuforums.org/showthread.php?t=2005391](http://ubuntuforums.org/showthread.php?t=2005391)

Note: I'm using Ubuntu 12.10 64bit but this should work for anythign since you're editing the Adobe plugin directly.

---

