---
title: "MP4 playback in MythVideo?"
date: 2007-07-26
forum: Multimedia &amp; Video
---

### Post by dave_chimaera on 2007-07-26
I'm running Feisty with MythTV and associated plugins installed via Medibuntu repositories (FFMPEG, Libdvdcss and so on). Almost everything I've got video-wise plays fine withing MythVideo except for MP4-encoded movies - I've got a bunch of them encoded using a program called Handbrake on OSX from the original DVD. 

Whenever I try to play these MP4 files the screen goes black for maybe 15-20 seconds then it goes back to the Mythvideo menu. Playback through Xine or Mplayer works fine - as  a short term fix I've configured Myth to play these files back through Xine, but its irritating and I'd rather get MythVideo to handle it if at all possible (As Myth passes to Xine the screen flickers and the desktop is briefly visible in the background).

I've heard that the FFMPEG bundled in the repositories is a bit limited in its capabilities - could that be the fault?

---

### Post by geoffp on 2007-08-21
I'm not sure, Dave, but I have exactly the same issue, including Handbrake.  I've just encoded the entire run of Monty Python's Flying Circus, which was a lot of work, and I really, really want Myth to play them nicely in the internal player.

Actually, I think mythtv has a compiled-in version of libavcodec (which I think is the codec collection in ffmpeg), so I'm not sure Ubuntu's ffmpeg would be the issue.  Mythtv using a stale version of libavcodec, however, might be.

I haven't been able to find all that much over at the mythtv trac, except one patch that might have nothing at all to do with this.  Maybe I'll file a bug.

We could always rejigger our videos into .avi, but that would suck, because .avi sucks.

---

