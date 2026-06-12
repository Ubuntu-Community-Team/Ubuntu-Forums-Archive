---
title: "change song info in amarok"
date: 2007-07-01
forum: Multimedia &amp; Video
---

### Post by joos13 on 2007-07-01
when i try to change song information in amarok, I get the error: "sorry, the tag for the following files could not be changed:" 

what is preventing me from changing song information??  thanks.

---

### Post by dfreer on 2007-07-02
Is your music stored someplace funky? on a windows partition, on a USB drive, network share, etc? what format are the songs you are trying to edit (mp3, wma, ogg, etc)?

---

### Post by joos13 on 2007-07-02
the music is stored in /home/josh/documents/music, not really a weird place.  the songs are either mp3 or mpeg-4.  neither format info can be changed.

---

### Post by dfreer on 2007-07-02
Try an ls -l on the music in question, what do the permissions look like?

---

### Post by joos13 on 2007-07-02
So with a little more investigating i realized that I COULD change the information of the mp3s, but could not change the info of the m4a's.  when i did ls -l, some m4a's could be found while others could not.  all the mp3's that i tried to get info on could be located.

> josh@josh-laptop:~$ ls -l "/home/josh/Documents/Music/Killer Bee's Country Mix/01 - Track 01.m4a"
-rw-r--r-- 1 josh josh 4465858 2007-05-06 21:48 /home/josh/Documents/Music/Killer Bee's Country Mix/01 - Track 01.m4a
josh@josh-laptop:~$ ls -l "/home/josh/Documents/Music/E/Eagles/The Complete Greatest Hits [Disc 1]/Hotel California.mp3"
-rw-r--r-- 1 josh josh 6388259 2007-07-02 17:52 /home/josh/Documents/Music/E/Eagles/The Complete Greatest Hits [Disc 1]/Hotel California.mp3
josh@josh-laptop:~$ ls -l "/home/josh/Documents/Music/E/Eagles/The Complete Greatest Hits [Disc 1]/Witchy Woman.m4a"
ls: /home/josh/Documents/Music/E/Eagles/The Complete Greatest Hits [Disc 1]/Witchy Woman.m4a: No such file or directory


So the first m4a track could be found and the mp3, but not "witchy woman.m4a."  What are the permissions?  i assume that the rw and r mean readable and rewritable.  im brand new to linux so go easy on me.  thanks.

---

### Post by dfreer on 2007-07-02
yep, r = read and w = write. In general, you want your files to be -rw-r--r--, or 644 in octal. This means only you can write to the file, and everyone can only read to it. I was wanting to make sure you could write to the files, which might explain why you couldn't write to the files.
I dunno whether amarok can handle m4a or not, or even if it uses ID3 tags like mp3's do. Someone else might, however :)

---

