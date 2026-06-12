---
title: "Acidrip - Can't Read DVD track. Faulty Disc?"
date: 2010-09-26
forum: Multimedia Software
---

### Post by Claudius1974 on 2010-09-26
All,

I've been trying to rip DVD's using AcidRip but whatever DVD I try I get the same error from AcidRip - Can't Read DVD track. Faulty Disc?

After reading the forums I've tried /dev/dvd ,/dev/sr0 (Found by using the Disk Utility), /Media/DVD Title etc and tried running AcidRip both as myself and Sudo without success.

I'm really stuck here and would welcome some advice!

---

### Post by Claudius1974 on 2010-10-03
All,

I'd really appreciate some help here. 

After unmounting the DVD using the mount /media/mountpoint I've managed to get Acidrip to see the contents of the DVD, but whenever I try and rip a chapter I just get the message 'memcoder interrupted by user'. The screen on my netbook is too small to use the debug option.

I've successfully managed to get AcidRip to work using an ISO that I had lying around, so I tried to make a iso image of the DVD's I've been trying to rip but again I get an error. both dd if=/dev/dvd of=disk.iso and cat /dev/dvd/ > file.iso fail with an input/output error.

```
dd: reading `/dev/dvd': Input/output error
30656+0 records in
30656+0 records out
15695872 bytes (16 MB) copied, 9.52652 s, 1.6 MB/s

```

Am I doing something wrong, or is there a problem with my DVD drive?

---

### Post by PaulyWally on 2010-10-03
I recommend you first try to watch the DVD in the computer.  If it doesn't work, try playing the DVD in a regular DVD player.

Could be a faulty disc.  Could be you're computer is not decoding it properly (this is my guess).

---

