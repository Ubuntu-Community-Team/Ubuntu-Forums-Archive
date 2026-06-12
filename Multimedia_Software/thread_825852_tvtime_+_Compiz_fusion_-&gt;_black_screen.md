---
title: "tvtime + Compiz fusion -&gt; black screen"
date: 2008-06-11
forum: Multimedia Software
---

### Post by huepfend_schof on 2008-06-11
Hello,
When I activate the 3D-effects in my Ubuntu Hardy, then my video windows are getting black. In VLC and the other players I resolved the problem by setting the video output device to x11.
In tvtime I don't know how I can resolve the problem. If I set tvtime to fullscreen, I can see at the beginning everything, but after some time, the screen becomes black, even in full screen mode. This is very annoying.
Does anybody knows how I can solve this (I don't want to turn the 3D effects off!)

PS: I have an ATI graphics card and the fglrx driver.

---

### Post by robbiie on 2008-06-11
Hi there,

I am experiencing the same problem:

Hardy Heron
tvtime
compiz fusion
ATI Radeon 9600

From time to time, when I start tvtime in fullscreen mode, the tv-video is visible. but never in non-fullscreen mode. Is there a way to tell tvtime which DISPLAY it should use?

---

### Post by huepfend_schof on 2008-06-13
If I run compiz with indirect rendering it works now almost all the time. But after I watch TV a long time, sometimes the screen still becomes black. Then I restart compiz with:
alt-F2 -> "compiz --indirect-rendering"
and then it works for some hours.

To start compiz with indirect rendering at startup I changed the /usr/bin/compiz file:

> sudo gedit /usr/bin/compiz

right at the very bottom it says:
> ${COMPIZ_BIN_PATH}${COMPIZ_NAME} $COMPIZ_OPTIONS "$@" $COMPIZ_PLUGINS || exec $FALLBACKWM $FALLBACKWM_OPTIONS

Which I replaced by:
> ${COMPIZ_BIN_PATH}${COMPIZ_NAME} $COMPIZ_OPTIONS --indirect-rendering "$@" $COMPIZ_PLUGINS || exec $FALLBACKWM $FALLBACKWM_OPTIONS



But this is not the ideal solution. Does anybody has an idea what I could try?

---

### Post by openware on 2009-01-18
same problem here:

intrepid
tvtime
compiz fusion
ATI Radeon 9600
fglrx driver

---

### Post by jettapup on 2009-01-21
This cut from the Common Problems on the tvtime web page at:
[http://tvtime.sourceforge.net/problems.html#fgloverlay](http://tvtime.sourceforge.net/problems.html#fgloverlay)

tvtime not starting when using the Radeon FireGL drivers 


This can be set in the Device section for the fglrx of your /etc/X11/XF86Config-4 using:
    Option  "VideoOverlay"       
or
    Option  "OpenGLOverlay"  
 
To use tvtime, you **MUST** select VideoOverlay instead of OpenGLOverlay. The tvtime bug report on this is bug 787142.  

I have same problem such that tvtime will not start with the ATI drivers enabled. 
However I can not find FX86Config-4 to edit it in 8.04.HH. Where might it Be?

---

### Post by openware on 2009-01-27
This is not the same problem!
In your case you must edit your /etc/X11/xorg.conf and add 
        Option "VideoOverlay" "on"
        Option "OpenGLOverlay" "off"
under "Device" section if it is not already added.


The mentioned problem in this thread - black screen occures in tvtime and in any player when playing movie only when compiz is enabled. Once compiz is disabled the picture is fine.
Please, anyone help and thanks for your time!

---

### Post by ajcrm125 on 2009-01-29
Bump.
Same problem here.  I've tried the directions here as well as those outlined here:
[http://forum.compiz-fusion.org/showthread.php?t=6794]("http://forum.compiz-fusion.org/showthread.php?t=6794")

but still get black window when I fire up tvtime.  If I drag the window I can sometimes see the video for 1/4 a second but that's about it.  Disabling Compiz allows me to see the video.

---

### Post by ajcrm125 on 2009-01-29
While waiting for a proper resolution, I made a quick script to fire off tvtime:

```

metacity --restart &
sleep 5
/usr/bin/tvtime $*
compiz --restart &

```

---

