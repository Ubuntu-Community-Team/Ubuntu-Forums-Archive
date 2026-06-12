---
title: "audio video sync errors"
date: 2009-12-23
forum: Mythbuntu
---

### Post by iitywygms on 2009-12-23
Running Mythbuntu 9.04 with mythtv.22 using the mythbuntu autobuilds. 
Lately, (last week) I have been getting audio/video sync errors.  The video will play ahead of the audio, then slow down, then speed up again.  It never seems to be in sync.  This happens on recorded programs or live tv.  BUT not all recorded programs or all live tv broadcast.
The audio sounds normal and stable.
I have 3 separate front ends and they all exhibit the same issue. I have one main backend. All the front ends use nvida cards, but not vdpau.
I cannot say for sure but it appears to only happen on channels that broadcast in 1080i or 480i, but I cant be completely sure of that.
I have tried several different playback profiles and nothing solves it.
ifconfig shows no network errors.
The backend uses two ati hdtv wonder cards and a hdhomerun dual tuner.

One other thing I should mention.  I get all my signal over the air and it is not always stable.  I get alot of errors.

2009-12-22 22:24:06.691 [mpeg2video @ 0x7facf5ab1820]ac-tex damaged at 41 9
2009-12-22 22:24:06.691 [mpeg2video @ 0x7facf5ab1820]mb incr damaged
2009-12-22 22:24:06.691 [mpeg2video @ 0x7facf5ab1820]mb incr damaged
2009-12-22 22:24:06.698 [mpeg2video @ 0x7facf5ab1820]Warning MVs not available
2009-12-22 22:30:28.262 [ac3 @ 0x7facf5ab1820]frame CRC mismatch
2009-12-22 22:30:28.293 [ac3 @ 0x7facf5ab1820]incomplete frame
2009-12-22 22:30:28.293 [ac3 @ 0x7facf5ab1820]invalid frame size
2009-12-22 22:30:28.945 [mpeg2video @ 0x7facf5ab1820]Warning MVs not available
2009-12-22 22:35:43.431 [ac3 @ 0x7facf5ab1820]frame CRC mismatch
2009-12-22 22:35:43.461 [ac3 @ 0x7facf5ab1820]incomplete frame
2009-12-22 22:35:43.461 [ac3 @ 0x7facf5ab1820]invalid frame size
2009-12-22 22:35:43.949 [mpeg2video @ 0x7facf5ab1820]invalid mb type in B Frame$

Only thing is, I have been using the same setup for over six months, and this sync error just started happening.  That leads me to believe that the poor signal is not the problem.
Any help as this is very annoying.

---

### Post by iitywygms on 2009-12-24
Guys I really need some help here.  This is making my tv unwatchable.
I think the problem has to be on the back end side.  All of my frontends do it.  One is a atv, one is 64x and the other is 32x.
Is there any test or error files I could post that mite help??

---

### Post by iitywygms on 2009-12-26
Fixed.  Finally.
If anyone else has this issue.  Enable OpenGL vertical sync for timing will fix it.
Why it changed?  I don't know.  All of my frontends had it disabled.  Enabling it fixed it on everything.

Maybe the nvidia driver update??????

---

