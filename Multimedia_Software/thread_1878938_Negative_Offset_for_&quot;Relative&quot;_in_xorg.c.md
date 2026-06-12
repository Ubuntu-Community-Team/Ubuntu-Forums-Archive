---
title: "Negative Offset for &quot;Relative&quot; in xorg.conf"
date: 2011-11-10
forum: Multimedia Software
---

### Post by mwinstan on 2011-11-10
I have two identical monitors running 1920x1200 resolution.  The one on  the left is landscape and the one on the right is portrait for document  viewing purposes.  The problem is when I drag the mouse or a window from  the display on the left to the display on the right, the mouse jumps up  360 pixels on the right monitor.  I tried including the following line  in the "ServerLayout" section of the xorg.conf file:

[FONT=Courier New]Screen      1  "Screen1" Relative "Screen0" +1920 -360[/FONT]

X server fails to start with a negative value as an offset.  Does anyone know of a way to specify this?  TIA

---

### Post by mwinstan on 2011-11-11
anyone?

---

### Post by mwinstan on 2011-11-14
bump

---

### Post by mwinstan on 2011-11-15
I found that my approach was wrong.  Rather than trying to provide an offset relative to "Screen0" with a negative offset, I used absolute offsets for both monitors and gave the primary monitor a positive offset on the y axis.  So my xorg.conf file under Server Layout went from this:

Screen 0    "Screen0"    0 0
Screen 1    "Screen1"    Relative "Screen0" 1920 0 #want to insert -360 for the y offset

to this:

Screen 0    "Screen0"    0 360
Screen 1    "Screen1"    1920 0

Just to keep things clear for anyone else looking for a solution, I have two monitors that are 1920x1200.  The one on the left is the primary monitor and is in landscape orientation.  The one on the right is primarily for document viewing, so it is in portrait orientation.  The 360 y offset for the primary monitor is so that the mouse pointer lines up when I drag it from one screen to the next.  360 is the number of pixels on the right monitor that extend above the top of the left monitor.

---

