---
title: "PVR 350 PPA [mpeg @ 0xb748b8b0]Parser not found for Codec Id: 94210 !"
date: 2007-12-27
forum: Mythbuntu
---

### Post by chacon on 2007-12-27
I think I have seen this elsewhere but not here.  IF anyone has any info or links which might help.  So basically I am running Gutsy with the PPA(???) drivers from superm1(sorry trying to work from memory here).   TV-out works fine, but when i play a DVD or play a movie(either avi or mp4) i try to watch a recording after that it fails.  

here is some of the mythfrontend.log:


2: start_time: 0.026 duration: 658.383
stream: start_time: 0.289 duration: 14438.080 bitrate=2389 kb/s
2007-12-27 10:16:04.429 AFD: Opened codec 0x9089c20, id(MPEG2VIDEO) type(Video)
2007-12-27 10:16:04.442 AFD: Opened codec 0x908b940, id(MP2) type(Audio)
[mpeg @ 0xb748b8b0]Parser not found for Codec Id: 94210 !
0: start_time: 0.036 duration: 658.399
1: start_time: 641.076 duration: 658.377
2: start_time: 0.026 duration: 658.383
stream: start_time: 0.289 duration: 14438.080 bitrate=2389 kb/s
2007-12-27 10:16:05.816 AFD: Opened codec 0x9086760, id(MPEG2VIDEO) type(Video)
2007-12-27 10:16:05.816 AFD: Opened codec 0x9086df0, id(MP2) type(Audio)
[mpeg @ 0xb748b8b0]Parser not found for Codec Id: 94210 !

I reboot the machine and it works fine(I believe i tried to restart the frontend and backend but it didnt work).  I would love it if it worked w/o having to reboot.    

Would it be safer/easier to just go back to my old system which was  feisty fawn using the feisty PVR350 howto...I remember getting that to work fine.


 Any advice would be great.  Thanks.

---

### Post by andrewb78 on 2007-12-27
I don't have any real solutions, but I think I have the same problem.  I don't have access to the box right now (it was a Christmas gift for my girlfriend and it's at her place), so I don't have any way to check logs.  I have reported a similar problem on [these]("http://ubuntuforums.org/showthread.php?t=643328") [forums]("http://ubuntuforums.org/showthread.php?t=644937"), however, to no avail.  There is a Gusty HOWTO (to which I contributed), but it doesn't fix this problem.  I really don't want my girlfriend to have to reboot the machine every time there has been a DVD in the drive.  Any help?

---

### Post by superm1 on 2007-12-27
The only recommendation I can add is maybe to fall back to an external player instead.

---

### Post by chacon on 2007-12-28
I read somewhere that if you uncheck "Use the PVR-350's TV out/ MPEG decoder" everything works fine.  I tried that and it works.  But the point is to use it since its less overhead on the CPU.    But that is a workaround for the moment.


Wait.. are you saying that if I use mplayer to play movies or DVD instead of "Internal" and leave  "Use the PVR-350's TV out/ MPEG decoder", it will work as it used to?

---

### Post by superm1 on 2007-12-29
> **chacon said:**
> I read somewhere that if you uncheck "Use the PVR-350's TV out/ MPEG decoder" everything works fine.  I tried that and it works.  But the point is to use it since its less overhead on the CPU.    But that is a workaround for the moment.


Wait.. are you saying that if I use mplayer to play movies or DVD instead of "Internal" and leave  "Use the PVR-350's TV out/ MPEG decoder", it will work as it used to?
That's what i'm saying to try at least.

---

