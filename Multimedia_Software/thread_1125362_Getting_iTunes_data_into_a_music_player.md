---
title: "Getting iTunes data into a music player"
date: 2009-04-14
forum: Multimedia Software
---

### Post by hatsnstuff on 2009-04-14
I've been looking around for ways to import my itunes play data (specifically play counts) into a music player for ubuntu, but Rhythmbox, Amarok and Banshee don't seem to have any working solutions at this time. I've found threads about them, but all these solutions are outdated/don't work.

It seems like its possible in Songbird, but that's my one of my last choices for music player.

So, I was wondering if anyone knows a way I can take my itunes music library, change computer/file locations and still keep my itunes music metadata? 

I'd prefer if someone had a solution for Amarok first, or one of the other music players listed above, or any other that they recommend. If not I'll probably take a shot at doing this in songbird.

Thanks in advance.

---

### Post by laluz on 2009-04-21
I have used a dcop based shell script to parse the iTunesDB xml and adjust the ratings in amarok. iTunesDB.xml has a rather simple structure.
I suggest you ask this question on Amarok forum, and if nobody helps you, write a script for playcounts yourself.

---

