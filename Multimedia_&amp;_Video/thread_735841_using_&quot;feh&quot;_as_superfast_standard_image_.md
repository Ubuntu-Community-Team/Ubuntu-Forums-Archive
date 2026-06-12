---
title: "using &quot;feh&quot; as superfast standard image viewer"
date: 2008-03-26
forum: Multimedia &amp; Video
---

### Post by Stefan_xfce on 2008-03-26
Hi, 
lately I discovered "feh", the image viewer, which is a really cool application in my point of view, and I want to make it my standard image viewer instead of "gqview".
When double click on an image now, I configured thunar, (also works with nautilus), so that it would execute
```
feh -F -Z
``` 
and the image loads very fast. 
(Right click, "open with", "open with custom application", "feh -F -Z").

The problem is, that it just loads that one image, and to view other images in that directory I would have to press ESC and click on another image as well.
Question:
What custom string must I tell thunar/nautilus to execute, so that it scans the current directory with feh and I can use the mousewheel to scroll, pretty much as if I would enter
```
feh -F -Z -S name [directory name]
```
in the terminal.

Thanks,
 Stefan
[EDITED - SOLVED]
I found out myself, I did it writing a small executable script and put that in ~/bin
```
#!/bin/bash
#Imageviewer.sh

AKDIR=`pwd`
feh -F -Z -S name "$AKDIR"
```

Then, I made the script executable with "chmod +x".

Then, I right clicked an image in nautilus, "open with", "open with custom application", and there I entered:
```
/home/[myusername]/bin/Imageviewer.sh
```

It works great, you should give it a try!

---

### Post by kerry_s on 2008-03-26
dude, try gpicview, it's just as fast as feh, but with standard pic viewer look.

---

### Post by Stefan_xfce on 2008-03-26
You're right, qpicview is very handy, I just tried it...
Thanks for the hint!

---

