---
title: "xine can't find DVD"
date: 2007-05-10
forum: Multimedia &amp; Video
---

### Post by ubuntum0nk3y on 2007-05-10
I have two DVD/RW drives in my machine and neither Xine nor Totem can locate them to begin playback.

When I put a disc into the drive, I get an icon on the Desktop that says DVD/R and no autoplay. Browsing around the filesystem,  don't find where the DVD drive is mounted.

Any suggestions?

---

### Post by GLRenderer on 2007-07-07
I got the same problem and I still haven't been able to fix it properly. What I did to fix things with Xine was to configure it to  search for /dev/hdc instead of /dev/dvd which is the default setting.

I got Xine running fine for that particular DVD+RW drive, it auto-starts fine. Now, the issue is how to make Xine choose the drive according to the media introduced to a particular drive?

I don't really know how linux selects the drive and the auto-mounting process so I can change the way in which the dvd device is actually selected.

---

