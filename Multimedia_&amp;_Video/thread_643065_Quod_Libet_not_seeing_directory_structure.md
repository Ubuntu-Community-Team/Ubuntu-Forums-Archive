---
title: "Quod Libet not seeing directory structure"
date: 2007-12-17
forum: Multimedia &amp; Video
---

### Post by bilder on 2007-12-17
Greetings All

Been re ripping all my tunes to flac with the following directory structure:

directory: FLAC
folder: Artist Name
folder: Album Title
which contains the flac files (songs)

Problem is, using Quod Libet 1.0 on Fiesty, the program is ignoring my file structure and is just putting all my songs in one huge pile called "Unknown" (People Unknown, Album Unknown) using the panned browser, which means I can not select by artist or album.

Same directory structure on another Fiesty box containing oggs seems to work fine.  :confused:

Anyone else having this problem?

---

### Post by hugmenot on 2007-12-17
Did you just name the files, or did you write actual tags to them? In QL, the only browser that takes directory structure into account is the "File System", but that is not very developed.

What you can do after the fact is using the file names to grab the tags from them. You could select all files you have (if the layout is stringent, and the same for all files) and then go to the tag editor and use Tags from Filenames.

---

### Post by bilder on 2007-12-17
> **hugmenot said:**
> Did you just name the files, or did you write actual tags to them? In QL, the only browser that takes directory structure into account is the "File System", but that is not very developed.

What you can do after the fact is using the file names to grab the tags from them. You could select all files you have (if the layout is stringent, and the same for all files) and then go to the tag editor and use Tags from Filenames.

hmm,
I'm ripping to a directory using Grip in flac format, and I assumed they are being flac tagged (or commented) by Grip. When I look at them using EasyTag I see encoder type, channels, bitrate, frequency, size, and time for each file.

Well, I just looked at my Grip configuration and it is set to only tag files ending in .mp3 (checked) and add id3 tags to encoded files (unchecked) as default.

Looks like I need to  turn only tag files ending in ,mp3 off and turn on add id3 tags to encoded files. Is this right? LOL good thing i've only ripped 8000 songs if I have to start over!:shock:

---

### Post by hugmenot on 2007-12-17
> **bilder said:**
> 
Looks like I need to  turn only tag files ending in ,mp3 off and turn on add id3 tags to encoded files. Is this right? LOL good thing i've only ripped 8000 songs if I have to start over!:shock:

No, wrong. The tagging system for flac is called "Vorbis Comments". ID3 is only for MP3. QL will not read .flac files with ID3 tags in them.

But there's no need for despair. If you ripped your songs to such a scheme:

```
/home/bilder/musik/FLAC/MyArtist/MyAlbum/01. MySongtitle.flac
```
then you jsut select all those files and enter as the pattern the following
```
/home/bilder/musik/FLAC/<artist>/<album>/<tracknumber>. <title>.flac
```

All tags will be filled in, but before pressing Save you should verify that is all works out in the preview.

---

### Post by bilder on 2007-12-17
Well, thank you for the tips hugmenot. I will give this a try. Guess I should have tested this out before I got so far into my music collection. It's not that big of a deal, since I'm just going to put them on an A/V server and shuffle play them.

---

