---
title: "Panning on startup"
date: 2009-02-12
forum: Mythbuntu
---

### Post by konadad on 2009-02-12
Just got my new myth box up and running on 8.10.  After hunting through the Frontend setup menus one day, where I may have accidentally temporarily adjusted my GUI setup while playing around, I now am having the following issue:

Every time that I now startup or reboot, the screen enters a Panning mode with MythTV starting up in the upper left half-off the screen.  I can pan up to it and everything works, but the Xfce taskbar stays visible from the Frontend.  The only way that it goes away is if I restart X - then it comes back up with no panning, and the Xfce taskbar is no longer visible in the Frontend.

Have tried the following:
-Verified that my xorg.conf is correct.  The custom modeline I setup worked great before the issue started, and works great after restarting X.
-Verified that everything in Nvidia-Settings looks correct - no panning selected.
-After reading multiple posts suggesting there is a bug with the GUI setup, verified that GUI height, width, X offset, and Y offset are all Zero.
-Used the "Reset" function in the GUI setup screen.

Any other thoughts on how to get back to base condition here?  There must be some underlying setting somewhere that is driving this on every startup, but I have no idea where to look further.

---

### Post by konadad on 2009-02-24
Still struggling with finding any answer to this issue - kicking myself for ever accidentally changing the GUI setting.  I think that [this section of the mythtv wiki]("http://www.mythtv.org/wiki/Overscan#Making_MythTV_fit_the_screen_on_a_TV") references the issue that I am having when it talks about:

> Note - for some window managers (like gnome) the menubar may appear at the top of the screen with the resized GUI below it. Using another window manager like blackbox or fluxbox will eliminate this problem since they do not have a menubar at the top of the screen. This will also make it easier to access a menubar that is off screen because of overscan. The main menu can be accessed in blackbox or fluxbox anywhere on the screen by right clicking the mouse. HOWEVER if you do want to keep gnome, just right click on the menubar at the top, click "customize panel" and check off autohide. Now MythTV will run fullscreen correctly.

But...I like my taskbar and don't want to autohide it.  Any thoughts from folks around how I can make this go away?  There has to be some underlying setting somewhere that I can find and put back to base condition, just need a pointer to send me looking in the right direction.

---

### Post by konadad on 2009-03-01
Since I thought that my problem was caused by altering the GUI settings as mentioned above and also listed in [this bug]("https://bugs.launchpad.net/mythbuntu/+bug/232380"), and I can't find anything that says how to get out of it, I went to the extreme and reloaded my system today from the 8.10 LiveCD (thinking that I would not touch the GUI settings or screen setup wizard this time!!).

To my utter surprise, once I had the system loaded back up, and loaded in my xorg.conf file with custom modeline for my HDTV, surpisingly the problem came RIGHT BACK.  Hadn't even touched anything settings-wise in the Myth applications yet.

So now am back to square one about how to think about the issue.  Attaching my xorg.conf file below for reference in case it helps trigger some thought in someone on what to look at - I use the 1232x693 modeline.  It appears when the problem is there like X is somehow driving a full 1920x1080 resolution to my 1232x693 and hence then has to have panning, but myth and xfce desktop are only displayed in a 1232x693 region of the bigger 1920x1080 space that you can see by panning around with the mouse.  Perhaps related to the incorrect EDID info coming from my Sony HDTV that says its Native res is 1920x1080 (incorrect, but should be overridden by my xorg.conf anyway by how I have it setup)

I can still make the issue go away _instantly_ by just restarting X by doing ctrl-alt-backspace.  I think this has to be a key to solving this.  For whatever reason when the computer initially boots up it is like it is bringing X up differently - does this ring a bell for anyone?  Is there something inherently different in mythbuntu about how X comes up on a cold startup or reboot vs. how it starts up when just doing ctrl-alt-backspace?

xorg.conf that I am using:
```
Section "Module"
    Load           "glx"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
    HorizSync 15.0 - 46.0
    VertRefresh 59.0 - 61.0
    Modeline "1232x693" 74.160 1232 1352 1392 1648 693 716 721 750 +hsync +vsync    
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "DPI" "100x100"
    Option         "UseEvents" "1"
    Option         "AddARGBVisuals" "1"
    Option         "AddARGBGLXVisuals" "1"
    Option         "NoLogo" "1"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    Option "ExactModeTimingsDVI" "True"
    SubSection     "Display"
        Depth       24
        Modes      "1232x693" "nvidia-auto-select" "1920x1080" "1280x720" "1024x768" "720x480" "800x600" "640x480"
    EndSubSection
EndSection
```

---

