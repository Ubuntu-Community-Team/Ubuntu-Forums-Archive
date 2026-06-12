---
title: "Music player export media to spreadsheet to edit metadata"
date: 2016-07-23
forum: Multimedia Software
---

### Post by rgorrison on 2016-07-23
Hello - 
I'm running Lubuntu 14.04. 
I've tried a variety of media players (mostly rhythmbox, audacious, clementine) and am mostly happy with rhythmbox but it is missing some features I am looking for. I installed wine/playonlinux and then itunes, but the program kept freezing up, and I would much rather use an open source solution. I'm hoping for a little expert guidance. 

A few things which I would be interested in having capability for: 
[LIST]
[*]a) sorting by category within playlists
[*]b) adding multiple copies of the same song within a single playlist
[*]c) exporting playlists as a pdf or spreadsheet file
[/LIST]

 Also, d), I have about 7k songs for which I need to edit metadata - the years in particular. I have a spreadsheet of the songs and their years, but no way of getting my music into a format where I can automate updating the metadata for those 7k songs.

I hope it's okay that I have four different points here -- any help much appreciated.

Rebecca

---

### Post by Keith_Helms on 2016-07-25
You didn't mention what format your music is in.  Is it MP3s?  Audacious will sort by category, assuming you meant genre.  It will also let you add multiple copies of a song to playlists.  I've been looking for years for a player that has "weighted playlist" capability (play song A 3 times as often as song B), but haven't come across it.

For c) it sounds like you want to export the tags to a spreadsheet and not just the playlist entries.  If you just wanted the filenames, Audacious will let you export a playlist to pls format, which is pretty much just plain text.

There are a lot of tag editors around.  Most of them seem to be command line based although a few have a gui.  One called puddletag looks interesting, although I didn't explore it enough to see what all it can do.  What is it you want to accomplish?  Do you want to select a set of audio files and set the tag data within them to the same value?  Do you want to sort by some tag field and move all the files with the same value to a new directory?  Something else?

---

### Post by rgorrison on 2016-07-28
Hi Keith_Helms -  Thanks for the reply!

My music files are primarily .flac, but also .wma and .mp3 files. In terms of sort by category, I mean by genre, year, and artist name, ratings, etc - in rhythmbox I can still search within a playlist in the search bar, but not sort how they are viewed.  I see the Audacious has this sorting capability (awesome!) but the library/search environment is really poor in my opinion (not so awesome..). 

In terms of the exporting there are two things, first to export the playlist as a pdf to share it with others, and additionally export the tags to edit them. The files I'm interested in are tango songs from late 1920s to the early 1960s. 

For editing the tags, if I export from audacious in .pls is there a way to import the edited pls file and assign data to the files?  A lot my songs don't have the date recorded attached to them and that is the information I want to add.  I have a spreadsheet with the name of a song and the date that song was recorded, but need a way to get that information attached to my media files. I have a few thousand songs and don't want to do it by hand.  It isn't consistent by album or artist, so I can't think of a batch way to select that way. Maybe I could write out a list of songs and have anything that matched one of those strings be assigned to a certain year?   I'll look into some of the command line editors.

---

### Post by Keith_Helms on 2016-07-28
A pls playlist looks like this:
```
[playlist]
NumberOfEntries=130
File1=./1973-Ring Ring/01-Ring, Ring.mp3
File2=./1973-Ring Ring/02-Another Town, Another Train.mp3
File3=./1973-Ring Ring/03-Disillusion.mp3
File4=./1973-Ring Ring/04-People Need Love.mp3
File5=./1973-Ring Ring/05-I Saw It In The Mirror.mp3
File6=./1973-Ring Ring/06-Nina, Pretty Ballerina.mp3
```

Audacious is more of a player than a "library manager".  If it has a search capability more advanced than "find artists, albums or songnames containing text" I'm not aware of it.

If what you're starting with is a spreadsheet containing song names that may not match the file names of the music, then it's going to be hard to come up with any automated process to save you from a lot of manual updates.

Sorry.  Maybe somebody else will chime in with an "oh, you just need to do this" answer. ;)

---

### Post by rgorrison on 2016-07-28
Thanks for your help...  I was looking at the pls file and it seems like not quite the golden ticket I was hoping for.   

Likely there is no easy fix. I'll do it manually or try to figure out a way in a tagging editor.

---

