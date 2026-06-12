---
title: "[SOLVED] Exaile rescan collection bug"
date: 2007-09-30
forum: Multimedia &amp; Video
---

### Post by olavjunior on 2007-09-30
Now I've tried many versions of exaile, and it seems to be a memory problem when rescanning collection. Every time I try, the memory usage peaks and the use of swap expands until the system completely hangs. 

I can't be the only one having this problem?

EDIT: I tried one more time. Closed down all other unnecessary applications, and watched the system monitor as it started scanning. Exailes memory usage kept growing till it reached my max ram of 1 gb, then the cpu-usage of exaile fell from 50% to 0%, while the swap usage kept growing. After a while my computer is totaly unusable. So there's a major memory leak somewhere. I guess it's in exaile. Or could it be in gutsy??

Think I'll jump on to kubuntu when kde4 comes around. Anyway to export library to Amarok fraom Exaile? (Keep playlists and ratings)

---

### Post by ajkenney on 2007-10-07
I just started using Exaile.  First from the repositories then downloaded from their site for the latest release so I could use the plugins and themes.  

I get a very similar problem.  My music is kept on an external usb drive (~20,000 songs @ close to 85gb).  Exaile started reading my collection and 3-4 hours later, it was still working hard at it!  The CPU usage was minimal but, the internal drive was kicking like crazy and I couldn't do anything else on the computer.  Finally had to kill Exail to get my machine back.  I believe the memory leak would have to be in Exaile as I'm using feisty not gutsy! 

I've been using Amarok for awhile and Songbird before that.  I thought I'd try something that the Ubuntu guys would be including with the new releases.  Songbird was just too big and inflexible.  Amarok was maxing out my CPU most of the time but, it was easy to use and sounded great.  I was hoping Exaile would be better!

BTW - I also can't seem to either open or import m3u or pls playlists into Exaile.  Any suggestion on how I could do this?  Thanks!

---

### Post by olavjunior on 2007-10-21
ok, problem solved! I investigated the problem with terminal, and noticed that it started hanging reading my .m4a-files. So removed them (have very few) from the folder, and then it ran smoothly. Maby this was caused by lacking codecs. Haven't tried with the gstreamer plugins bad set jet. 

:popcorn:

---

### Post by Ehtetur on 2007-10-21
Had the same issue w/ Exaile 0.2.11-bzr1437.. it also locked up when trying to play any m4a file...
These are the additional gstreamer files I installed to give exaile m4a support:

gstreamer0.10-plugins-bad
gstreamer0.10-plugins-bad-multiverse
gstreamer0.10-plugins-ugly-multiverse
gstreamer0.10-ffmpeg
gstreamer0.10-plugins-ugly

Some of the files have dependencies that get installed so I made sure I had the medibuntu.list in my sources.list.d folder before starting.
Here's the details for enabling the medibuntu repos in Gutsy:
[https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f](https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f)

---

### Post by smilelover on 2008-05-01
Sorry to wake up this thread... but has anyone experienced the same? My Exaile eats up all resources as well, but in my case removing m4a files and installing all thone gstreamer plugins didn't help... :(

---

### Post by olavjunior on 2008-05-24
> **smilelover said:**
> Sorry to wake up this thread... but has anyone experienced the same? My Exaile eats up all resources as well, but in my case removing m4a files and installing all thone gstreamer plugins didn't help... :(

Have you tried running it in terminal to see what's happening when it's eating your cpu?

---

### Post by smilelover on 2008-05-24
Yeah, I solved id a few weeks ago... sort of... sorry I didn't posted about it. It was caused by MP3s with weird characters (Korean) in ID3 tags. I moved that album out of watched folders and everything went OK.

I haven't opened any bug report though..

---

