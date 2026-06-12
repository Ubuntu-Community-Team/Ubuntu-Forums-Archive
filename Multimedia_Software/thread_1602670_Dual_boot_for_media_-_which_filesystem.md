---
title: "Dual boot for media - which filesystem"
date: 2010-10-21
forum: Multimedia Software
---

### Post by artyom108 on 2010-10-21
I'm about to build a new 10.04 / Win7 dual boot laptop system.  (I've been running a 8.04 / winxp system for several years)

I mostly do software dev in ubuntu and do media stuff in windows (watch streaming netflix, occasional audio editing and video, etc)

My main question is about how best to assign the mountpoints and  also create visibility between the OS's

I was thinking of making my mount points
at

/home
/mymedia
and then 
/ would have everything else
(with boot and swap etc)

1) I'm thinking of making /mymedia be the place for audio and video.  Should I make it an NTFS partition, and then let ubuntu see it, or make it ext3 partition and let Win7 see it using one of the fs extensions?  ie, For which set of playing / editting tools would having the native file system be most helpful?  I'd likely do video watching and editing on windows, but will often listen to my music collection on linux as I work.

Right now, in 8.04, for example Rhythmbox often hangs if I've watched any videos or flash stuff on the web before I launch it... are these kinds of issues a thing of the past with 10.04?

(I have a 250G drive)

---

