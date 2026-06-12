---
title: "Rhythmbox skips"
date: 2007-11-05
forum: Multimedia &amp; Video
---

### Post by ZeroYuy on 2007-11-05
Okay, my Rhythmbox is acting REAL funny like. If will play some .m4a's half way through, and it will play mp3's just fine, but it will skip. XMMS won't load any .m4a's and another player was able to play them, but was skipping. I get the error "Internal GStreamer error: Negotiation problem. Report this as a bug at..link.."

i have ALL the codec's from the restricted, and then some. Any help here? I really need my music. It's like a drug addiction. xD

I did find ONE possible solution, and that was to go back to an older version, but the files weren't on the server anymore and I couldn't find it..

Oh right, Ubuntu Feisty Fawn, the latest version.

---

### Post by dark_harmonics on 2007-11-07
I also have this error playing m4a files and no problem with mp3. Running the latest updated fresh install of gutsy gibbon.

---

### Post by dark_harmonics on 2007-11-09
I just converted all my m4a files to mp3s. It sucks to lose all that metadata though.

---

### Post by teejay17 on 2007-12-30
> **dark_harmonics said:**
> I also have this error playing m4a files and no problem with mp3. Running the latest updated fresh install of gutsy gibbon.
I have the same problem too: m4as in Rhythmbox, but fine everywhere else. Some help would be much appreciated:KS

---

### Post by tfgibbon on 2008-04-05
im guessing you guys may have solved your problem by now but for anyone else i wanted to point out the resources that helped me fix it on my laptop 

starting here: [https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/138728](https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/138728)

go down and download [http://launchpadlibrarian.net/10185451/gst-plugins-bad-multiverse0.10_0.10.5.debdiff](http://launchpadlibrarian.net/10185451/gst-plugins-bad-multiverse0.10_0.10.5.debdiff)

learn how to use debdiff here: [https://wiki.ubuntu.com/UbuntuPackagingGuide/BuildFromDebdiff?highlight=%28debdiff%29](https://wiki.ubuntu.com/UbuntuPackagingGuide/BuildFromDebdiff?highlight=%28debdiff%29)

the example at the bottom made it easier for me to understand.

this fixed it for me, hope this is helpful to someone

by the way im running gutsy

---

### Post by teejay17 on 2008-04-07
> **tfgibbon said:**
> im guessing you guys may have solved your problem by now but for anyone else i wanted to point out the resources that helped me fix it on my laptop 

starting here: [https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/138728](https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/138728)

go down and download [http://launchpadlibrarian.net/10185451/gst-plugins-bad-multiverse0.10_0.10.5.debdiff](http://launchpadlibrarian.net/10185451/gst-plugins-bad-multiverse0.10_0.10.5.debdiff)

learn how to use debdiff here: [https://wiki.ubuntu.com/UbuntuPackagingGuide/BuildFromDebdiff?highlight=%28debdiff%29](https://wiki.ubuntu.com/UbuntuPackagingGuide/BuildFromDebdiff?highlight=%28debdiff%29)

the example at the bottom made it easier for me to understand.

this fixed it for me, hope this is helpful to someone

by the way im running gutsy
Well, I didn't really solve my problem, *per se, *but I was able to get my songs playing without skipping: I turned off the "fade" option between tracks, and that did the trick. 
However, it would be nice to have it running the way its supposed to, with tracks fading into one another.

---

