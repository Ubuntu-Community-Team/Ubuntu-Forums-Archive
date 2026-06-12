---
title: "How to have a virtual screen smaller than the resolution?"
date: 2007-08-23
forum: Multimedia &amp; Video
---

### Post by rjtd on 2007-08-23
Greetings.
I'm trying to use Linux on my LCD TV, via component.
The image is already displayer correctly at 720p on the TV, but given that the LCD has major overscan issues, I need to correct this. It is impossible to do so by modeline, fbset.
So, what I'm trying to do is to get a smaller X screen than the screen resolution (720p, 1280x720).
So, what I need to do is the following
- maintaining the X11 physical resolution, change the "virtual resolution" to something smaller, so that X becomes a image in the middle of the screen surrounded by black bars.
Is this possible? How to do it?

I already tried the following on X, but by default X changes the screen resolution to  the smaller value (Modes vs Virtual), and in this case, it uses 1024x768:
SubSection "Display"
                Depth           24
                Modes           "1280x1024"
                Virtual          1024 768
End SubSection

I wanted to maintain 1280x1024 screen res with a smaller 1024x768 X11 in the middle of the screen.

PS: I want to avoid using Xnest if possible

---

### Post by kocoman on 2007-10-23
bump

I am having the same problem too, expect I am using Mac OSX (hacktonish) and projecting an LCD screen to an overhead, but the LCD screen is 17" while the overhead is 10"

---

### Post by Shazaam on 2007-10-23
Not Ubuntu but Mandriva has this in my xorg.conf...

Section "Monitor"
    Identifier "monitor1"
    VendorName "ViewSonic"
    ModelName "ViewSonic A90"
    HorizSync 30-86
    VertRefresh 50-180

    # TV fullscreen mode or DVD fullscreen output.
    # 768x576 @ 79 Hz, 50 kHz hsync
    ModeLine "768x576"     50.00  768  832  846 1000   576  590  595  630
    
    # 768x576 @ 100 Hz, 61.6 kHz hsync
    ModeLine "768x576"     63.07  768  800  960 1024   576  578  590  616

Maybe something like that will work? I don't use it so I don't know if it will help.

---

