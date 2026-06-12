---
title: "MP3 File Tags"
date: 2009-05-13
forum: Multimedia Software
---

### Post by rabi.fettig on 2009-05-13
I've been noticing a problem when I rip CDs. Whenever I import a CD, I enter all of the information (Artist, Album Title, Genre, Year, etc.) beforehand, and everything looks good when I'm playing the music back in Rhythmbox or Amarok, but when I transfer the same MP3 files to my MP3 player (Sansa Fuze) or to my XP system at work, it doesn't see any information, and tells me it's an unknown artist from an unknown album.

What would cause this, and how do I fix it? I don't see any settings that I could potentially adjust pertaining to ID3 tags in Sound Juicer.

---

### Post by logos34 on 2009-05-13
Maybe add 'xingmux' to end of gstreamer mp3 pipeline:

> ... ! xingmux ! id3v2mux

Or better yet use some [other ripper,]("https://help.ubuntu.com/community/CDRipping#Other%20CD%20Ripping%20Software") since there's a bug in the gstreamer lame plugin (get VBR mp3 output wrong, among other things).  Read the ["Warning" here.]("https://help.ubuntu.com/community/CDRipping#MP3%20Encoding")

---

