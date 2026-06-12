---
title: "aspect ratio and fill can't be changed"
date: 2010-05-05
forum: Mythbuntu
---

### Post by reformy on 2010-05-05
Hi all
I've just upgrade my mythbuntu 9.10 to 10.04 (and apparently mythtv 0.22 to 0.23). Everything went well, except for this:
When playing any recording, it opens with aspect ratio of 16:9. when changing using the menu - nothing happens (stays the same ratio). When changing the fill, same thing - no change.
The weird thing is that OSD changes - the box saying "half"/"full"/"h.streach"... is changed, but the picture stays the same.

Can anyone help plz?

Thanks

---

### Post by Lepy on 2010-05-05
Aspect change works fine for me upgrading from 9.10/.22.

A few guesses...try using the OSD to change aspect and make sure your graphics are configured properly (proprietary drivers installed, etc).

Also, try running the frontend from a terminal and check/post the output when changing the aspect ratio.

---

### Post by chipppy on 2010-05-07
Good Morning

i had huge problem getting 16:9 to run poperly on my Plamsa until I was pointed to the small issue of aspect ratio (4:3)setting in my graphics setting.  set that to 16:9 and all was good.
Might be worth a look in the graphic setting on desktop as opposed to myth settings.
Hope that helps

cheers
chipppy

---

### Post by reformy on 2010-05-07
> **chipppy said:**
> Good Morning

i had huge problem getting 16:9 to run poperly on my Plamsa until I was pointed to the small issue of aspect ratio (4:3)setting in my graphics setting.  set that to 16:9 and all was good.
Might be worth a look in the graphic setting on desktop as opposed to myth settings.
Hope that helps

cheers
chipppy

Thanks! I've activated the ATI drivers and now its working as it should.

---

