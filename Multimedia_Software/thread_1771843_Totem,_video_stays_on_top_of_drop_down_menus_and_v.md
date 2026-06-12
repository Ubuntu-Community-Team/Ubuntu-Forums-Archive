---
title: "Totem, video stays on top of drop down menus and video remains when I change windows"
date: 2011-05-30
forum: Multimedia Software
---

### Post by drewbob on 2011-05-30
To expand on what I put in the title: this happens with both VLC and Totem, when in either of those programs playing a video, if I click on one of the top menus, say View in Totem, the video stays on top of the drop down options.  In order to see the options I have to hover over them with the mouse at which point they become momentarily visible.

I read a post somewhere where someone had a similar problem and it was solved by reinstalling Compiz, but I've tried uninstalling it entirely, reinstalling it, etc. and none of it works.  It doesn't happen with flash videos in firefox, it does happen with visualisations in Totem, and it only started happening since I upgraded to 11.04.

Thanks for any help anyone can offer,

Andrew

---

### Post by Dimitri123456 on 2011-06-04
Hi Andrew,

I had the same problem, reinstalling compiz didn't work for me either. I don't know if you have an ATI graphic card? I do, by installing the new ATI catalyst 11.5/FLGRX 8.5, I solved it for me.

Dimitri

---

### Post by drewbob on 2011-06-07
Hey Dimitri, thanks a lot for the reply, I'll give it a shot and mark as solved if it works!

---

### Post by drewbob on 2011-06-07
Didn't work unfortunately, from lshw:

*-display
                description: VGA compatible controller
                product: RS780M/RS780MN [Radeon HD 3200 Graphics]
                vendor: ATI Technologies Inc

This is the graphics card I'm using, I'm guessing it should be supported using the driver you suggested, it installed fine anyway.

If there are any other suggestions from anyone, I'd really appreciate it.  This is the only thing stopping me from pretty much permanently using Ubuntu.

---

### Post by drewbob on 2011-06-13
[http://ubuntuforums.org/showthread.php?t=1746078](http://ubuntuforums.org/showthread.php?t=1746078)

The gstreamer-properties suggestion worked for me.

---

