---
title: "dd fails with 'cannot skip: Invalid argument' reading unfinalized DVD"
date: 2018-02-16
forum: Multimedia Software
---

### Post by austin-green on 2018-02-16
Used dvd+rw-mediainfo to get track addresses from an unfinalized DVD:
```
# dvd+rw-mediainfo /dev/sr0
<snip>
READ DISC INFORMATION:
 Disc status:           appendable
 Number of Sessions:    1
 State of Last Session: incomplete
<snip>
READ TRACK INFORMATION[#3]:
 Track State:           complete incremental
 Track Start Address:   2816*2KB
 Free Blocks:           0*2KB
 Track Size:            420512*2KB
```
When trying to read a track with command such as
```
# dd bs=2048 skip=2816 count=420512 if=/dev/sr0 of=/tmp/disk5-track3.vob
```
I get this message:
```
dd: '/dev/sr0': cannot skip: Invalid argument
```
This method of extracting VOB files from unfinalized media is described elsewhere, e.g.
[http://flay.jellybee.co.uk/2011/01/how-to-get-files-off-unfinalized-dvd.html](http://flay.jellybee.co.uk/2011/01/how-to-get-files-off-unfinalized-dvd.html)
and seems to work for many people. Any info on possible causes, debugging tools and tips, etc., will be gratefully received.

---

### Post by TheFu on 2018-02-16
Use ddrescue. It keeps going after failures and tries again.

---

### Post by austin-green on 2018-02-17
> **TheFu said:**
> Use ddrescue. It keeps going after failures and tries again.

Thanks for the hint; didn't know about ddrescue. However, it just keeps retrying over and over on the first block, and never succeeds in reading. If I direct it to skip any blocks, it complains that there is only 2048 bytes of data on the media.

---

### Post by TheFu on 2018-02-17
Are you certain any data was actually flushed to the DVD?  Can't you finalize it?

---

### Post by austin-green on 2018-02-17
> **TheFu said:**
> Are you certain any data was actually flushed to the DVD?  Can't you finalize it?

Yes, as dvd+rw-mediainfo reports 23 tracks, most of them status 'complete incremental'.

No, cannot finalize as device used is no longer available.

---

### Post by TheFu on 2018-02-18
If ddrescue can't get anything, I don't know anything that can.
You might try other data recovery - there's a "*data recovery ubuntu*" page somewhere. Google for it.  photorec and testdisk ... something.  They are painful to use, IME.

---

