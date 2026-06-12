---
title: "video_ts 71.8GB?"
date: 2010-03-14
forum: Multimedia Software
---

### Post by magikid on 2010-03-14
I'm trying to back up one of my dvds to my hdd.  My usual method is to copy the video_ts folder onto my hdd and convert it from there.  I popped this dvd into my computer and nautilus is saying that there is 71.8gb of data on this disk.

If I run df -h, here's what I see:
```
/dev/sr0              7.8G  7.8G     0 100% /media/cdrom0
```

but if I run du -h /media/cdrom0:
```
72G	/media/cdrom0/VIDEO_TS
72G	/media/cdrom0/

```

If I run du -h /media/cdrom0/*, I see a bunch of entries like this:
1.0G	/media/cdrom0/VIDEO_TS/VTS_22_1.VOB
1.0G	/media/cdrom0/VIDEO_TS/VTS_22_2.VOB
1.0G	/media/cdrom0/VIDEO_TS/VTS_22_3.VOB
1.0G	/media/cdrom0/VIDEO_TS/VTS_22_4.VOB
1.0G	/media/cdrom0/VIDEO_TS/VTS_22_5.VOB
1.0G	/media/cdrom0/VIDEO_TS/VTS_22_6.VOB

There are actually 65 of these 1gb files.

Any ideas on why this is happening or how to get this backed up?

---

### Post by mc4man on 2010-03-14
The title has structure protection that at the very least has numerous bogus titlesets and borked .ifo's. (there could and probably are some other things 'wrong'

Manually you're not going to be able to do too much, at least not in a reasonable time and effort.

Maybe try the latest k9copy which may or may not be able to deal with - possibly trying different means - movie only - reauthor menu, movie only - keep orig menu, ect.
(you'd need to probably tell k9 which titleset to use if there are dups of the 'real' one and discard the rest.

(if you just wanted it for playback then you could dump to an encrypted .iso which would be the true size and playback fine - but couldn't be processed.

Otherwise use some windows prog or a win one in wine.

---

### Post by magikid on 2010-03-14
I actually found another way to do this.  With some useful googling, I found that the chapter on the disk that is the actual movie is chapter 50, so I used vlc to rip that chapter with the command:
```
vlc -I rc dvd:///dev/sr0@50 --sout "#standard{access=file,mux=ps,dst=movie.mpeg}"
```

That outputted an mpeg into my current directory.

---

### Post by hazelnut on 2010-03-14
I think you mean title 50, a chapter will usually be 5 to 10 minutes or so.

I use this command to backup my movies (assuming title 50):

mplayer -nocache -dvd-device /media/cdrom0 dvdnav://50 -aid 128 -dumpstream -dumpfile myvideo.mpg

---

