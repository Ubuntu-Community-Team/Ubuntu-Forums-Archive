---
title: "dvd to dvd copy problem using cpdvd"
date: 2009-10-11
forum: Multimedia Software
---

### Post by Mariane on 2009-10-11
Here is the output:
```

tux@tux-laptop:~$ cpdvd /home/tux/Desktop/Pics/cpdvd/
cpdvd: $Revision: 1.10 $ $Date: 2004/01/31 09:53:41 $
 device=/dev/scd0  mount=/dvd
Probing DVD...
 titles: total=10
  #01: len=01:34:52 titleset=02 angles=01 chapters=25
  #02: len=00:00:27 titleset=03 angles=01 chapters=02
  #03: len=00:21:14 titleset=01 angles=01 chapters=05
  #04: len=00:10:09 titleset=01 angles=01 chapters=02
  #05: len=00:02:05 titleset=01 angles=01 chapters=02
  #06: len=00:01:14 titleset=01 angles=01 chapters=02
  #07: len=00:07:48 titleset=01 angles=01 chapters=02
  #08: len=00:58:22 titleset=04 angles=01 chapters=03
  #09: len=00:42:35 titleset=04 angles=01 chapters=02
  #10: len=00:15:48 titleset=04 angles=01 chapters=02
 main title guess: 1
WARNING: Directory '/home/tux/Desktop/Pics/cpdvd' already exists!
Reading title sets
Checking title set files
 min=1, max=4, total=4
Selecting titles and sets
 titles: 1
 sets:   2
copy video manager VIDEO_TS

  IFO: 11 blocks, 22528 bytes, 1 MB -> 1 target file(s)
    writing '/home/tux/Desktop/Pics/cpdvd/VIDEO_TS.IFO' (11 blocks, 22528 bytes, 1 MB)
  BUP: 11 blocks, 22528 bytes, 1 MB -> 1 target file(s)
    writing '/home/tux/Desktop/Pics/cpdvd/VIDEO_TS.BUP' (11 blocks, 22528 bytes, 1 MB)
  MenuVOB: 70354 blocks, 144084992 bytes, 138 MB -> 1 target file(s)
    writing '/home/tux/Desktop/Pics/cpdvd/VIDEO_TS.VOB' (70354 blocks, 144084992 bytes, 138 MB)
copy title set 2
  IFO: 31 blocks, 63488 bytes, 1 MB -> 1 target file(s)
    writing '/home/tux/Desktop/Pics/cpdvd/VTS_02_0.IFO' (31 blocks, 63488 bytes, 1 MB)
  BUP: 31 blocks, 63488 bytes, 1 MB -> 1 target file(s)
    writing '/home/tux/Desktop/Pics/cpdvd/VTS_02_0.BUP' (31 blocks, 63488 bytes, 1 MB)
  MenuVOB: 6946 blocks, 14225408 bytes, 14 MB -> 1 target file(s)
    writing '/home/tux/Desktop/Pics/cpdvd/VTS_02_0.VOB' (6946 blocks, 14225408 bytes, 14 MB)
  TitleVOB: 2142800 blocks, 93487104 bytes, 4186 MB -> 5 target file(s)
    writing '/home/tux/Desktop/Pics/cpdvd/VTS_02_1.VOB' (524288 blocks, 1073741824 bytes, 1024 MB)
    writing '/home/tux/Desktop/Pics/cpdvd/VTS_02_2.VOB' (524288 blocks, 1073741824 bytes, 1024 MB)
    writing '/home/tux/Desktop/Pics/cpdvd/VTS_02_3.VOB' (524288 blocks, 1073741824 bytes, 1024 MB)
Read error at block 1114112 from DVDReadBlocks!
ERROR: Got error result while executing 'cpvts -d "/dev/scd0" -t 2 "/home/tux/Desktop/Pics/cpdvd"'
Ready, but 1 ERROR(s) occured!

```

The result is that though it now takes 2.3G on my hard disk I only have the first half of the movie. 

Mariane

---

