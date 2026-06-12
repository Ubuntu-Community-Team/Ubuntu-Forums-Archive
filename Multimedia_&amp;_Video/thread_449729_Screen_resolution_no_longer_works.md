---
title: "Screen resolution no longer works"
date: 2007-05-20
forum: Multimedia &amp; Video
---

### Post by shifuimam on 2007-05-20
I've got an ATI All-In-Wonder 9600 AGP card. It's got dual VGA outputs, and I'm running on two Samsung 710n 17" analog LCDs that run at 1280x1024@60hz (2560x1024 for the dual display).

I got my setup to work with dual display when I first got Ubuntu installed, I believe using this guide:

[http://ubuntuforums.org/showthread.php?t=301941](http://ubuntuforums.org/showthread.php?t=301941)

It worked great for awhile. I haven't booted into Ubuntu for awhile, and today I booted into it to test my DVD burner, and lo and behold my display wasn't working correctly. If I look under the "Screen Resolution" control panel, it has my resolution set to 3100x1600@60hz. I can change it to 1280x1024, which makes my displays mirror each other. My primary display is now attempting to display at 1600x1200, although it's all fuzzy and jittery since it's higher than its native resolution. My secondary display still works at 1280x1024. I've made several xorg.conf changes to no avail, and I cannot remember for the life of me what changes I made to xorg.conf in the first place to make it work!

Any help is greatly appreciated. Thanks in advance!

You can see my current xorg.conf here:
[http://shifuimam.googlepages.com/xorg.txt](http://shifuimam.googlepages.com/xorg.txt)

---

### Post by shifuimam on 2007-05-20
I should add that I looked in gconf-edit and found that the resolution was changed to 3100x1600 there - I changed it to 2560x1024 and rebooted, and that didn't fix the issue, either.

---

### Post by shifuimam on 2007-05-20
*bump*

Anyone have any ideas?? :\

---

