---
title: "DVD rip experts: need advice for my experiments"
date: 2008-05-26
forum: Multimedia Software
---

### Post by megamania on 2008-05-26
I'm trying to learn how to rip dvds and what the best options are.

After a failed experiment with dvdrip a few months ago, I decided to try again with k9copy.
I managed to create an ISO image of the movie. It is 4,3GB in size and everything appears to work (menu, subtitles, languages, etc).

However, if check the properties of the original DVD, it says it 7,7GB.
Since I could access the DVD easily, I decided to copy the files by dragging them to the desktop. This time I came up with a 7,7GB directory, which appears to work exactly as the 4,3GB ISO!

These are the contents of the dvd iso:
```

$ ls /media/backup -R -h -l
/media/backup:
totale 4,0K
dr-xr-xr-x 1 root root 2,0K 2008-05-25 16:07 audio_ts
dr-xr-xr-x 1 root root 2,0K 2008-05-25 16:45 video_ts

/media/backup/audio_ts:
totale 0

/media/backup/video_ts:
totale 4,3G
-r-xr-xr-x 1 root root  12K 2008-05-25 16:45 video_ts.bup
-r-xr-xr-x 1 root root  12K 2008-05-25 16:45 video_ts.ifo
-r-xr-xr-x 1 root root 596K 2008-05-25 16:07 video_ts.vob
-r-xr-xr-x 1 root root 114K 2008-05-25 16:43 vts_01_0.bup
-r-xr-xr-x 1 root root 114K 2008-05-25 16:43 vts_01_0.ifo
-r-xr-xr-x 1 root root  37M 2008-05-25 16:08 vts_01_0.vob
-r-xr-xr-x 1 root root 1,0G 2008-05-25 16:43 vts_01_1.vob
-r-xr-xr-x 1 root root 1,0G 2008-05-25 16:44 vts_01_2.vob
-r-xr-xr-x 1 root root 1,0G 2008-05-25 16:44 vts_01_3.vob
-r-xr-xr-x 1 root root 1,0G 2008-05-25 16:45 vts_01_4.vob
-r-xr-xr-x 1 root root 269M 2008-05-25 16:45 vts_01_5.vob

```

These are the contents of the drag'n'drop copy:
```

$ ls /home/gianfranco/movie/ -R -h -l
/home/gianfranco/movie/:
totale 4,0K
drwxr-xr-x 2 gianfranco gianfranco 4,0K 2008-05-25 15:57 VIDEO_TS

/home/gianfranco/movie/VIDEO_TS:
totale 7,8G
-r--r--r-- 1 gianfranco gianfranco  12K 2008-05-25 15:42 VIDEO_TS.BUP
-r--r--r-- 1 gianfranco gianfranco  12K 2008-05-25 15:42 VIDEO_TS.IFO
-r--r--r-- 1 gianfranco gianfranco 982K 2008-05-25 15:42 VIDEO_TS.VOB
-r--r--r-- 1 gianfranco gianfranco 114K 2008-05-25 15:42 VTS_01_0.BUP
-r--r--r-- 1 gianfranco gianfranco 114K 2008-05-25 15:42 VTS_01_0.IFO
-r--r--r-- 1 gianfranco gianfranco  67M 2008-05-25 15:42 VTS_01_0.VOB
-r--r--r-- 1 gianfranco gianfranco 1,0G 2008-05-25 15:45 VTS_01_1.VOB
-r--r--r-- 1 gianfranco gianfranco 1,0G 2008-05-25 15:47 VTS_01_2.VOB
-r--r--r-- 1 gianfranco gianfranco 1,0G 2008-05-25 15:49 VTS_01_3.VOB
-r--r--r-- 1 gianfranco gianfranco 819M 2008-05-25 15:51 VTS_01_4.VOB
-r--r--r-- 1 gianfranco gianfranco 1,0G 2008-05-25 15:52 VTS_01_5.VOB
-r--r--r-- 1 gianfranco gianfranco 1,0G 2008-05-25 15:54 VTS_01_6.VOB
-r--r--r-- 1 gianfranco gianfranco 1,0G 2008-05-25 15:57 VTS_01_7.VOB
-r--r--r-- 1 gianfranco gianfranco 866M 2008-05-25 15:59 VTS_01_8.VOB

```
So the simple copy has twice the VOB files as the copy I got with k9copy.
My best guess is that K9Copy didn't simply copy the DVD, but it "resampled" it (apparently with some data loss).

Can anybody shed some light on this please?

---

### Post by mc4man on 2008-05-26
K9 trans coded (compressed) the orig. down to a size that will fit on a dvd5, and decrypted the content. If you were to burn it to a single layer dvdr it would work on a standalone.
By copying the disk directly you have a 'working' copy on your pc but it's still encrypted. If you managed to burn it to a dvd9 (dual layer) it would _not_ work on a standalone. (it would be missing the decryption keys which cannot be burnt - they go into an inaccessible area)

---

### Post by megamania on 2008-05-26
> **mc4man said:**
> K9 trans coded (compressed) the orig. down to a size that will fit on a dvd5, and decrypted the content. If you were to burn it to a single layer dvdr it would work on a standalone.
By copying the disk directly you have a 'working' copy on your pc but it's still encrypted. If you managed to burn it to a dvd9 (dual layer) it would _not_ work on a standalone. (it would be missing the decryption keys which cannot be burnt - they go into an inaccessible area)
Ahhh. :-)

So the direct copy works on my computer, but if I burn it on a dvd it won't work anymore because the keys can't be copied.
On the other hand, the k9copy is an unprotected, compressed copy.
Is that correct? If it is, is the compression noticeable in terms of quality loss?

---

### Post by mc4man on 2008-05-26
That depends on 
the amount of compression
the quality of the original source, and or it's compressibility (high action, fast motion vs more static scenes)
You can use k9 to eliminate extras, unneeded audio streams to reduce compression or to just do a movie only ect.  
The size of playback screen can be a factor also
........................................................................
The very best back ups or play disks are re encoded vs. transcoded using encoders like CCE ($60.00 - basic, $2000 - full ) or a free one - hcencoder.
But that's outside the scope of this thread and or forum

---

### Post by megamania on 2008-05-26
Thanks a lot for helping out. That's a completely new subject to me and your inputs are really appreciated!

---

### Post by mc4man on 2008-05-26
Here is a place to gather info - the archives are immense. If your inclined to sign up and post while newbies ?'s are answered there is an expectation that you'll search, read and try to educate yourself, then ask. Read the forum rules !
[http://www.doom9.org/](http://www.doom9.org/)

---

