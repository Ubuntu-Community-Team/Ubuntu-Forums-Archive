---
title: "CDG creation?"
date: 2010-04-28
forum: Multimedia Software
---

### Post by gimmickless on 2010-04-28
I've created a few audio files to make some karaoke tracks.  Problem is, I can't seem to find a program that creates CDG files. The Software Store has nothing, and Googling various keywords (linux, ubuntu, cdg, cd+g, create) turns up little besides PyKaraoke.  

There are a few available for Windows, but I'd rather resort to WINE unless absolutely necessary.  I'd rather learn how to create an MPEG/AVI first.  

Has anybody else solved this problem before?

---

### Post by chuck-dtol on 2010-11-25
Bump.  You are no the only person looking...

---

### Post by mannyweb.ca on 2011-03-27
Here's another bump.  Also looking, but appears ubuntu and linux overall is limited in this respect. :(

---

### Post by pSYcl0Ne on 2011-07-08
Bumpidy bump bump... looking for a solution also. how hard can this be? it must be almost as simple as a subtitle file for movies.

---

### Post by dzoey on 2012-02-28
I haven't been able to find a Linux program either.  My imperfect work around is to create ogg+kate files and play them through vlc, enabling a visualization, and then (through the video menu) subtitles.
First convert your wav files to ogg  using
oggenc -o songMusic.ogg song.wav

then create an ogg file containing the lyrics lrc information (see lrcgenerator.com to create lrc files from lyrics text)
kateenc -t lrc -c LRC -l en_US -o songLyrics.ogg song.lrc 

then merge the two
oggz merge -o song.ogg songLyrics.ogg songMusic.ogg 

Unfortunately, pykaraoke doesn't support ogg, so I've only been able to get this to work in vlc

---

