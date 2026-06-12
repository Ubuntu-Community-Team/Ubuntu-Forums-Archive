---
title: "xrandr --output LVDS1 --set &quot;scaling mode&quot; &quot;Full aspect&quot;"
date: 2011-07-28
forum: Multimedia Software
---

### Post by jarreboum on 2011-07-28
Hi there,

So I'm having a problem regarding fullscreen, widescreen and stretching.
I'm playing a few games that use standard resolution such as 800x600 while my native screen resolution is 1024x600 (a Eee901). When I put these games fullscreen the resolution is streched in order to fill the screen but it looks ugly. I want black bars and proper aspect ratio.

Someone gave me that nice command line that solve this very problem but apparently I have to input it on every reboot. I know I could just use a shell script and have it launch on start but I'm looking for a nicer solution, like a parameter to change in some file somewhere. Or better, a box to tick.

Also out of curiosity how come is "Full" (ugly stretch) instead of "Full aspect" (nice aspect ratio) by default? Is there a particular reason I can't get?

(I'm using Ubuntu 10.04 netbook edition on a Eee901)

---

### Post by realzippy on 2011-07-28
*..like a parameter to change in some file somewhere.*

Not exactly,but you could copy that xrandr command to
/etc/gdm/Init/Default 
instead of creating new script.

```

...................
OLD_IFS=$IFS

xrandr --output LVDS1 --set "scaling mode" "Full aspect"

#if [ -x '/usr/bin/xsplash' ];
...................

```

---

### Post by realzippy on 2011-08-22
Just cleaning up my subscribed threads.
Please set thread as solved (ThreadTools)...thanks

---

