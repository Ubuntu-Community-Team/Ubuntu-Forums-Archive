---
title: "Still unable to play DVDs"
date: 2008-03-03
forum: Multimedia &amp; Video
---

### Post by kyleolm on 2008-03-03
I have installed all codecs, restriced items, etc. I still cannot play DvDs. They will open, a beginning part will play, but when it should go to the title menu it just stops, like there is no dvd in the tray. If i try to play it in VLC, vlc just spontaneously closes. Ive looked throughout the forums and tried everything in there, but so far nothing is working. Help!!! Please!!

---

### Post by aysiu on 2008-03-03
When you say *all codecs*, does that include *libdvdcss2*?

---

### Post by kyleolm on 2008-03-03
yes

---

### Post by aysiu on 2008-03-03
Is it possible there's something physically wrong with your DVD drive?

---

### Post by kyleolm on 2008-03-03
it will play regular cds...what seems weird is it will play part of it...the new line home entertainment part. then when that is over it pretty much stops. The movie is Mr woodcock. On the back of the cd it says dvd rom requires windows...is it possible the copy protection such is just making it impossible to play on a non-windows machine

---

### Post by jrusso2 on 2008-03-03
I guess you could rip the encryption off and reburn it as an unencrypted DVD. Do you have problems with other DVD's or is it just that one?

Did you follow this guide I have found this works well.

Follow the part about playing encrypted DVD's

[https://help.ubuntu.com/community/Medibuntu#head-57a5050d451985de1b87ea87a3ccc1a4895e57d3](https://help.ubuntu.com/community/Medibuntu#head-57a5050d451985de1b87ea87a3ccc1a4895e57d3)

---

### Post by kyleolm on 2008-03-03
i inserted another dvd, and it seems to work seemlessly.

---

### Post by jrusso2 on 2008-03-03
Well if its just that one dvd thats not so bad.

---

### Post by mc4man on 2008-03-04
there's a workaround for some N.L. titles and similar R2 titles
[http://tobias.rautenkranz.ch/libdvdread_ifo.html](http://tobias.rautenkranz.ch/libdvdread_ifo.html)
a very quick how to
[http://ubuntuforums.org/showthread.php?t=652528&page=2](http://ubuntuforums.org/showthread.php?t=652528&page=2)

---

### Post by kyleolm on 2008-03-04
thanks! that worked! YAY! THANKS!
is there any way to get that patch to auto load? having to use that terminal command is highly inconvenient

---

### Post by mc4man on 2008-03-05
As far as 'integrating' the patch into vlc you'd probably have to patch dvdread in libdvdnav4. While it's no problem to patch dvdread in mplayer or libdvdread3 itself, it won't work on the dvdread in libdvdnav4. (to the best of my somewhat limited knowhow )

edit: refer here to redit to get vlc to open with patched dvdnav
[http://ubuntuforums.org/showthread.php?t=652528&page=2](http://ubuntuforums.org/showthread.php?t=652528&page=2)   #13    if you already have patched file on desktop or don't want to add a new source to sources list  or ck. here
[http://ubuntuforums.org/showthread.php?t=727671&page=2](http://ubuntuforums.org/showthread.php?t=727671&page=2)   # 17

---

