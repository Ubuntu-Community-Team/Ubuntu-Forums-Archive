---
title: "Is there a way to automatically delete duplicate songs"
date: 2017-04-23
forum: Multimedia Software
---

### Post by mercenarycor on 2017-04-23
Hi all,

So this thread exists a couple places in a kinda 'psuedo-answered' form, with the most helpful boiling down to "yeah, but I just go through them myself."  I haven't found any actual instructions for how to do it via command-line or program unless the files are EXACT duplicates.

So I have over 100 gigs of music, and probably 30+ gigs are duplicates.  There's literally dozens that differ by one second, and the album I got them from.  Is there a program or something smart enough to go through these songs and go "these are actually the same song, I'm going to delete X." I've been trudging through it for weeks, and have only worked through 3 gigs of music.  Any suggestions?

Example : Sorrow.mp3 by Flyleaf 2:45 and 03 Sorrow.mp3 by Flyleaf 2:49  I want it to automatically delete one and keep the other...preferably by quality of recording, but that's just if this is more easily resolvable then my searches have led me to believe.

---

### Post by TheFu on 2017-04-23
I feel your pain.  Tried to use a few of the other tools for exact dup removal - even those were cumbersome.
In the end, I just renamed all the files adding the quality to the end of the filename.  EasyTag will do the renaming. Then I'd move all the files for the same album into the same directory and sort.  Then it was easy to remove every other file. 

In my collection, I tend to have complete albums and every song inside the album has the same bitrate. I'm well organized with a 
genre/artist/album/ directory structure.  The only hard part is when artists are in different genres. ;(

Yes, it is still manual.  But **rm *160.mp3** is much easier than other methods. It is 1 command per album that way.

Oh - and a key thing I do is remove any funny characters or spaces from all my filenames. This makes scripting 1000x easier.

And don't forget to make backups along the way. It sucks for a small mistake to wipe out lots of hard work.
```
rm *160.mp3 
rm * 160.mp3   # <--- bad idea
```
one of those is a good command, the other makes for a bad day.  I've seen this - with -rf as an option. It was a bad week at that job.

Since this is an itch that I have too, I might create a script that changes all filename, appending length+bitrate to the end for all files in a single directory, then removes the shorter, lower-bitrate version based on track number.  I wouldn't trust the song title, since spacing and other odd characters could be off.  I'll add this to my TODO list, so don't hold your breath. ;)

---

