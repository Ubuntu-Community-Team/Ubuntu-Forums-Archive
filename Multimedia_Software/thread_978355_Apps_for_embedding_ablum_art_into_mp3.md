---
title: "Apps for embedding ablum art into mp3"
date: 2008-11-11
forum: Multimedia Software
---

### Post by grahams on 2008-11-11
I've tried using Easytag and eyed3 to embedded jpg ablum art into mp3 files. However when I play the mp3s on my Cowon D2 the pictures are corrupt. When I embed the same jpgs and into the same mp3s file with iTunes on my wife xp system it works fine. 

Anyone know why the images get corrupted with Easytag and eyed3. Are there other apps I could use for this?

---

### Post by grahams on 2008-11-21
bump

---

### Post by grahams on 2009-01-23
Anyone ?

---

### Post by rmdegennaro on 2009-05-30
Hi,

I have the same issue on my G1.  I found EasyTag also corrupted the entry so that many other programs would not read nor save tags in the file.  I.e.  I couldn't remove the corrupted image.   

I found an old forum entry that suggested to use a different library, but I hate upgrading just one thing to development versions.

In the end, I did this:
[LIST=1]
[*]resave with K-yamo (no changes necessary)
[*]have ACAD automatically download & save artwork
[/LIST]

I found ACAD ([link]("http://www.unrealvoodoo.org/hiteck/projects/albumart/")) would not actually "fix" the corrupted artwork tag in the MP3.  If launched from command-line, one can see the Python library error message.  Many programs would not actually, that's why I installed K-yamo (sudo apt-get install kyamo) to fix the corrupted MP3 files.  

Oh, you may need to play with the version of ID tags for your player/phone.  The basic process works on my G1 and SanDisk Sansa e280.  

I hope this works for others,
Best,
Rio

---

### Post by rmdegennaro on 2009-05-30
P.S.  I updated to 9.04 and still that issue.  I will file a bug as soon as I have time...  I guess it should be for the PY library as well as EasyTag....

---

### Post by grahams on 2009-06-23
Thanks I'll give that a try.

---

