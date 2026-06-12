---
title: "editing MP3 Proberties: Album"
date: 2011-05-28
forum: Multimedia Software
---

### Post by gamendorf on 2011-05-28
I have about 1000 mp3s that Windows Media Player messed up. (one of the major reasons I switched to Linux)  I need to go through them and correct the album tags.  I know exactly how to do this in Windows, and I also know that it is extremely tedious. (In Windows, I would right click on the mp3, Properties, Details tab, edit the album tag.

Is there a more efficient way to change them in Ubuntu? It is a collection of three audio-books ripped from cd, and I want all of the tracks from each book to all have the same album tag. (so approx. 350 mp3s need the same tag). I'm thinking that a script might do the trick, but I have no idea what to look for when I parse the file. Or, is there a program that will magically take care of this for me?

---

### Post by gamendorf on 2011-05-28
This frustrated me on principle, but the easiest program I found was [MP3tag]("http://mp3tag.de/en/download.html"). It is a Windows program, but I was done with the job less than 3 minutes from when I started the download.

---

### Post by coffeecat on 2011-05-29
I'm glad you managed to find an app that solved your problem, even if it was a Windows one! For future reference there does seem to be an app in Ubuntu that would have done this. See this thread:

[http://ubuntuforums.org/showthread.php?t=1761898](http://ubuntuforums.org/showthread.php?t=1761898)

The OP solved their own problem eventually with exfalco which is in the repositories. I've just installed it and although I haven't used it properly yet, it does look as though it can batch rewrite specific tags very easily.

It's a pity that neither Easytag nor kid3 have this ability - or not that I can find. The only batch facility I could find in Easytag is for the filename which is useful but doesn't go far enough. The particular issue that I haven't found an answer for is adding the same jpeg to the album art for all the tracks of an album. Albums purchased from Ubuntu One store occasionally arrive without the album art.

---

### Post by gamendorf on 2011-05-29
Just like that OP, I also had an issue with the file names.  They were originally ripped from CD, so they were in different directories named after the CD.  This caused issues when listening on my MP3 player.  I wanted them all in a single "Book" directory with then named 
Book001.mp3 ... Book345.mp3.

I eventually made a custom script to to move and rename them, but that pushed my scripting skills to their max. (I'm not that good)  I definitely didn't have the skill to start modding the contents of the mp3 to change the tags.

I'll give exFalco a shot. I'm always a fan of native apps. Hate to break out VMWare unless I have to.

---

