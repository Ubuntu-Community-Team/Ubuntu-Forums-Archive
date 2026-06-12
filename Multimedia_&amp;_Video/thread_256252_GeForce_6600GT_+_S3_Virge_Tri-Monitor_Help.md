---
title: "GeForce 6600GT + S3 Virge Tri-Monitor Help"
date: 2006-09-12
forum: Multimedia &amp; Video
---

### Post by elbondo on 2006-09-12
I currently have Twinview enabled using two 19" LCD monitors on my 6600GT, both running at 1280x1024, one via analog and one via digital. I also have an S3 Virge DX/GX in my system, which I used to use in Windows as a third monitor with a 15" 1024x768 LCD.

I want to do the same thing in ubuntu, but I want to avoid using Xinerama and having to specifically open applications on one monitor and not be able to move them. If I could have the X Server consider the 2 19"s as one monitor as it does now, and the 15" as a second using Xinerama, that would be fine, or even if I could only pipe video output through the 15" that would be nice.

I am also wondering how to slightly offset my monitors. I want to move one of my 19" monitors about 10-20px down from the other so that the mouse cursor is in the same place. When I changed the Metamodes line to be ```
1280x1024 +0+0,1280x1024 +0-10;
``` from ```
1280x1024,1280x1024;
``` it changed my monitors into clone mode.

EDIT: Attached lspci and xorg.conf

---

