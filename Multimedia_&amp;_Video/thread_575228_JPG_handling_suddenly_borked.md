---
title: "JPG handling suddenly borked"
date: 2007-10-13
forum: Multimedia &amp; Video
---

### Post by rmfought on 2007-10-13
So I'm trying to organize all my photos, and all of a sudden (as in today, this worked just days ago) Gnome has no clue what to do with image files.  Whenever I try to open a JPG or GIF file I get the following message:

"Cannot open image.gif: No application suitable for automatic installation is available for handling this kind of file."

I don't remember removing anything lately except messing with Gdesklets which broke recently.  Anyone else have this problem before?  Fiesty Fawn amd64.

---

### Post by rmfought on 2007-10-14
Aha, I did another search and found the following thread:

[http://ubuntuforums.org/showthread.php?t=485266]("http://ubuntuforums.org/showthread.php?t=485266")

For the most part it worked, but I still kept getting the security message about type mismatch:

**Do not open the file unless you created the file yourself, or received the file from a trusted source. To open the file, rename the file to the correct extension for "PDF document", then open the file normally. Alternatively, use the Open With menu to choose a specific application for the file.**

So to solve that I followed loucomballa's solution in this thread:

[http://ubuntuforums.org/showthread.php?t=224064]("http://ubuntuforums.org/showthread.php?t=224064")

Great, everything works.  All because gDesklets is hosed for amd64.  This is the problem with running 64-bit, there's always some workaround but it seems that if you do enough "workarounds" the system becomes just as flaky as Windows.  So I'm sticking with 32-bit when Gutsy is released.

---

