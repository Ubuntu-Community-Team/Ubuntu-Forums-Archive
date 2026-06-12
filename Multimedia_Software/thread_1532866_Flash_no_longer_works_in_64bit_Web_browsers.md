---
title: "Flash no longer works in 64bit Web browsers"
date: 2010-07-17
forum: Multimedia Software
---

### Post by kemra on 2010-07-17
I installed 64bit flash last week when I installed Ubuntu 10.04 64bit on my new laptop, and for the past week it has worked without issues.

However a couple of day ago it simply stopped showing flash videos on sites such as youtube etc. I think there might have been a ream of updates around the time this happened but my memory is a little vague.

I have since tried installing the each of the 3 flash codecs in turn that Firefox recommends but these will not install, failing with an exit status of 2. After I tried this I followed the 64bit flash instructions on the Wiki once more to get back to the point when it previously worked but alas this has been of no help.

I have also tried loading flash videos in Chromium and these suffer from the same issue. Anyone have any ideas what could have caused flash to suddenly stop working?

---

### Post by djscribe on 2010-07-17
I'm running Flash 10 fine on my Lucid, it's my Hardy giving me trouble. 

I can't get anything with Flash 10 to play. Most, not all Flash 9 or earlier play fine, then again, after several views, just renders a black screen and I need to restart FFox to continue viewing. All workarounds have failed thus far. Running 1gb RAM on AMD64 Athlon 3.2gHz with 5Gigs free space. Update fine, upgrade fine, although I suspect Firefox has a hard time processing flash for very long since flash-ridden sites crash the browser at random. Running an NVidia BFG 512MB play movies on my rig for hrs at a time, no problem. I really like FFox so I haven't explored other browsers. Lucid runs Flash 10 fine with the flashplayer installer plugin just fine. I've tried both loading the ISO as I've cleaned and simply used the non-free from Synaptic, to no avail. Why can't us Hardy lovers run it as well?

Anyway, did you try using the flashplayer-installer pkg from Synaptic, Kemra? Not the non-free, the "installer" - works fine on my side.

---

### Post by lovinglinux on 2010-07-17
Flash 64bit is no longer supported by Adobe and has a critical vulnerability. You should install the 32bit version.

Try version 1.0.7 of [FLASH-AID](http://flash-aid-extension.blogspot.com). It will allow to remove conflicting plugins and install the proper flash from the repositories.

---

### Post by kemra on 2010-07-18
> **lovinglinux said:**
> Flash 64bit is no longer supported by Adobe and has a critical vulnerability. You should install the 32bit version.

Try version 1.0.7 of [FLASH-AID](http://flash-aid-extension.blogspot.com). It will allow to remove conflicting plugins and install the proper flash from the repositories.

Thanks a lot that worked great.

---

### Post by lovinglinux on 2010-07-18
> **kemra said:**
> Thanks a lot that worked great.

You are welcome.

---

