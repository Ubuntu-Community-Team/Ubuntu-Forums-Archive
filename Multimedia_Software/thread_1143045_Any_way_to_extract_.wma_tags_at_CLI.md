---
title: "Any way to extract .wma tags at CLI?"
date: 2009-04-29
forum: Multimedia Software
---

### Post by Huufarted on 2009-04-29
I'm converting some wma files to mp3 at the command line and I want to take the tags with them.  As it stands, I can't find a way to strip out the individual tags.  Anybody know of something I can use at the command line to that will print out the info tags in a .wma file or a way to convert .wma to .mp3 while preserving the tags?

---

### Post by mc4man on 2009-04-29
Maybe try pacpl which if it can do the conversion will write new tags as per the orig.

Thead on
[http://ubuntuforums.org/showthread.php?t=712064](http://ubuntuforums.org/showthread.php?t=712064)

When i tested it I just used this package which installed cleanly on my 8.10 (I have modified 8.10 with newer libs AV wise, don't know about clean install on stock 8.10

[http://packages.debian.org/unstable/main/pacpl](http://packages.debian.org/unstable/main/pacpl)

Downsides of pacpl (to the extent I tried, which due to following wasn't much
Won't do wma *lossless* which is all I have
Seems to only use very basic mp3 options (cbr


I made myself a little script for converting and tagging wma lossless to mp3 using lame and any valid lame options, only really useful if doing an album  (in other words tags all tracks with same artist, album, year and genre tags,  track name and track number are individualized.
( those are the six tags I want, can be pared down and or others can be easily  added. 

If that's something you end up wanting to try, to customize for you I need to know how your tracks are numbered, really need any of these types (while zero padding 1-9 isn't necessary, it's very much advised

If so also do you want track number tag for 01 - 09 to be 2 digit (01, 02, ect.) or 1 digit (1, 2, ect.

04 The Great Gig in the Sky.wma 
04 - The Great Gig in the Sky.wma 
04-The Great Gig in the Sky.wma 
04- The Great Gig in the Sky
04_The_Great_Gig_in_the_Sky.wma

( all of mine are either the first or second example

screen shows the first 5 tags via mediainfo for above track

---

