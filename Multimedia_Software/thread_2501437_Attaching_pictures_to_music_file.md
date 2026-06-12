---
title: "Attaching pictures to music file?"
date: 2024-10-07
forum: Multimedia Software
---

### Post by Autodave on 2024-10-07
Looking fir a program that will let me attach pics of lyrics to a music file.  In other words, I would like to take a song that I already have recorded and then make LibreOffice (?) file with the lyrics and attach that to the music as it plays.  This would be a series of files....not all of the words at a time, but just a line or two of the words......and the words would change as the music plays.  

Any suggestions?

If I am still not being clear, think of a song on YouTube.  As it plays, the words pop up as the singer sings them.

---

### Post by Holger_Gehrke on 2024-10-07
The simplest approach is probably an [lrc-file]("https://en.wikipedia.org/wiki/LRC_(file_format)"). That's just a simple text-file with a time stamp before each verse. A lot of players support these either directly or through a plugin. Just create the file in your favourite editor, give it a name matching the song (e.g. 'MySong.flac' and 'MySong.lrc'), put both files in the same directory and if your player supports lrc then it should display the lyrics while playing the song.

Alternatively there are tags in ID3 v2 named SYLT (**sy**nchronized **l**yrics or **t**ext) and USLT (**u**n**s**ynchronized **l**yrics or **t**ext) and flac can have tags in vorbis comment blocks including a "LYRICS" tag. Good luck finding a player that supports these.

Holger

---

### Post by Autodave on 2024-10-08
Thanks for the reply, but I am looking probably for something else.  I would like to make this a portable audio/video thing......a file that I could just copy to a USB and play anywhere instantly.

---

### Post by nicolasdentremont on 2024-10-08
You should be able to do that with most video editing programs. I've used Open Shot for a couple video projects, it seems to be a decent program.

---

### Post by Autodave on 2024-10-11
> **nicolasdentremont said:**
> You should be able to do that with most video editing programs. I've used Open Shot for a couple video projects, it seems to be a decent program.

Openshot worked......it was a lot more work than I had hoped it would be, but it did do the trick.  Thanks!

---

