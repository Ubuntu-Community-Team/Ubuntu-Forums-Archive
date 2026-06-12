---
title: "Cannot play certain mp4 even with Fluendo codec"
date: 2007-03-14
forum: Multimedia &amp; Video
---

### Post by uzd4ce on 2007-03-14
I cannot play video files that I took on my Xacti HD1a camcorder.  All the movie players I try just shut down right after I hit play.  I get the same problem on my Edgy desktop and my Feisty laptop.

The files are mpeg-4, 1280x720.  Right clicking for the properties shows AAC 2.0 (libfaad) 48000 hz audio. 

VLC from a terminal shows:
$ vlc SANY0021.MP4 

VLC media player 0.8.6 Janus
main warning: can't store message (Invalid or incomplete multibyte or wide character): found Box: 
main warning: can't store message (Invalid or incomplete multibyte or wide character): read box: "
main warning: can't store message (Invalid or incomplete multibyte or wide character): found Box: 
main warning: can't store message (Invalid or incomplete multibyte or wide character): read box: "
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  141 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  82
  Current serial number in output stream:  83

I can successfully play another mp4 (320x240, 24000hz audio) that I downloaded from the web.

What is it about the Xacti format that Ubuntu doesn't like?  I've installed all the normal codecs via Automatix, and have also bought and installed the Fluendo mp4 part 2 codec.

Thanks

---

### Post by Masterj15 on 2007-03-14
I'm not that sure what your saying but try this link and see me posts. See if it helpes in any way possible.
[http://www.ubuntuforums.org/showthread.php?t=383106&page=2]("http://www.ubuntuforums.org/showthread.php?t=383106&page=2")[http://www.ubuntuforums.org/showthread.php?t=383106&page=2](http://www.ubuntuforums.org/showthread.php?t=383106&page=2)

---

### Post by uzd4ce on 2007-03-14
What I meant is that when I try to play certain mp4 files in any video player, the player immediately crashes.

I've done some more research and found that the problem (BadAlloc error) is related to shared memory on the video card and the i810 video driver that I'm using.  It appears that videos over a certain size require more video memory, which is not allocated by default, or something.

I've seen a few tips about editing the xorg.conf to add Options for VideoRam and CacheLines to the Device section, but I can't find a setting that works for me.  The video players always still crash.

I'd appreciate any other suggestions anyone might have.

---

